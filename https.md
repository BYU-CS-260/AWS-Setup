# Setting up HTTPS 

In this tutorial, we will configure Caddy to use https to serve files from your public_html directory. 
You should wait to perform this step until you have received notification that your domain has been set up.
You can continue to use http://IPV4_address until your [domain](domain.md) is provisioned.

1. Edit the `/etc/caddy/Caddyfile` so that it uses this Route53 Domain Name.

```
sudo nano /etc/caddy/Caddyfile
```

You need to replace the ":80" with the host name for your web server.

```

markclement.net {
        # Set this path to your site's directory.
        root * /usr/share/caddy
```

3. Exit nano by pressing the "Control" and the "O" key at the same time to save out the file.  Press the "return" key to accept the file name to save to.
Then press the "Control" and the "X" key at the same time to exit the nano eitor.

4. Restart caddy to make caddy use the new configuration file.

```
sudo systemctl restart caddy
```

When caddy sees this new configuration, with a hostname specified, it is now able to automatically request and configure a certificate for your website sot that it can serve files using HTTPS. This provides encryption between the web browser and your web server, so that any information anyone sends to your website, such as a password or a credit card, is encrypted when it is sent to your server.  This step may take a while.  Caddy has to request a certificate for your domain.  If you cant seem to get the https to work after an hour or so, you can try spinning up a new instance and deleting this one.

5. Now you can visit your web server using the `open address` link shown in your EC2 instance, right next to where you found the host name. You should see your "Hello World" web page.

And you should see a lock icon in the browser window. (Note, some browsers are instead showing _nothing_ when the website is secure, and `Not Secure` when it is not secure. So check to see what your browser does for secure sites.)
It may take a while for Caddy to set up a certificate to allow for secure connections, so be patient.

If you have trouble with this, then put the ":80" back into the Caddyfile and you can use HTTP to access your pages.  Talk to a TA or the instructor to figure out how to make things work.
6. You can also set up a proxy that will have Caddy serve content from other servers on your computer.  And you can set up a subdomain using the following syntax in your /etc/caddy/Caddyfile
```
markclement.net {
        # Set this path to your site's directory.
        root * /usr/share/caddy

        # Enable the static file server.
        file_server

        # Another common task is to set up a reverse proxy:
        # reverse_proxy localhost:8080
        handle /api/* {
                reverse_proxy localhost:3000
        }

        # Or serve a PHP site through php-fpm:
        # php_fastcgi localhost:9000
}

# Set up a subdomain
creative3.markclement.net {
        # Set this path to your site's directory.
         root * /var/www/html
        #
        # Enable the static file server.
        file_server
}
```



