# Setup directories for caddy

Web servers serve files from directories. If you noticed, the caddy welcome page tells you to setup your site so that it serves pages from `/var/www/html`. The `/var/www` directory is the standard place where we store web pages on a Linux system. We will use the `html` directory as the default page for your site. Later in the semester, we will have you setup additional directories in `/var/www` to store other sites.

For all of this work, we are going to be using Cloud9.

## Look around

Before doing some important work, use the bash terminal in Cloud9 to list the files in the `/var/www/html` direcotry:

```bash
ls /var/www/html
```

You will see this:

```sh
ubuntu:~/environment $ ls /var/www/html
index.html
ubuntu:~/environment $ 
```

This means there is one file in there, `index.html`.

Let's take a closer look:

```sh
ubuntu:~/environment $ ls -al /var/www/html
total 20
drwxr-xr-x 2 root root  4096 Aug 16 04:03 .
drwxr-xr-x 3 root root  4096 Aug 16 04:03 ..
-rw-r--r-- 1 root root 10918 Aug 16 04:03 index.html
```

The `-al` flag shows you who owns the file directory (.), the parent directory (..), and the `index.html` file.  You will notice all of these are owned by `root`, which is the superuser or administrator account for your machine. 

If `root` owns those files, who are you?

```
ubuntu:~/environment $ whoami
ubuntu
ubuntu:~/environment $ 
```

You are the `ubuntu` user. To change any files owned by `root` you need to use `sudo` to temporarily become a superuser or administrator.

## Change ownership

Since you will be wanting to access `/var/www/html` all semester, it will be more convenient to have this directory owned by `ubuntu`. You can make this change with this command:

```
sudo chown -R ubuntu /var/www 
```

The `chown` command changes ownership. The `-R` flag tells it to operate recursively. You are changing the directory `/var/www/` and all files inside it (and any subdirectories), so that they are owned by `ubuntu`.

Now you can rerun the `ls -al` command:

```
ubuntu:~/environment $ ls -al /var/www/html
total 20
drwxr-xr-x 2 ubuntu root  4096 Aug 16 04:03 .
drwxr-xr-x 3 ubuntu root  4096 Aug 16 04:03 ..
-rw-r--r-- 1 ubuntu root 10918 Aug 16 04:03 index.html
```

You will see that the directory (.) and the parent directory (..) and the file `index.html` are now owned by `ubuntu`. 

## Create a shortcut

It will be convenient to edit files in Cloud9. To get to the `/var/www` directory, create a shortcut to it in the bash terminal:

```
ln -s /var/www .
```

You should now see the `www` shortcut in the pane on the left side.

## Edit CaddyFile

We need to edit the Caddyfile to use the `/var/www/html` directory.

```
sudo vim /etc/caddy/Caddyfile
```

As a reminder, you can navigate in the vim editor, using the arrow keys. Once you get to the line where you want to edit the file, type `i`. This changes to `insert mode`. When you are done with editing, you type the `ESC` or escape key to get out of insert mode. Then you can type `:wq` to write the file and quit vim.

You want to edit the root so that it says:

```sh
root * /var/www/html
```

So the file should look like this:

```sh
ec2-54-186-104-251.us-west-2.compute.amazonaws.com {
        # Set this path to your site's directory.
        root * /var/www/html

        # Enable the static file server.
        file_server

        # Another common task is to set up a reverse proxy:
        # reverse_proxy localhost:8080

        # Or serve a PHP site through php-fpm:
        # php_fastcgi localhost:9000
}
```

Ignore all the comments. There are really only three lines to configure a basic caddy setup

- the hostame
- the location of the root directory
- a line that tells caddy to serve the files that are located here (`file_server`)

Once you are done editing, be sure to restart caddy so it uses this new configuration:

```
sudo systemctl restart caddy
```

## Edit index.html

The `index.html` file you are given is the default for the Apache web server, which was installed for you.

Edit this file in the Cloud9 editor by finding it in the `www` shortcut and then double-clicking the file:

![editing index.html file](/images/editing-index.png)

Delete everything in this file and replace it with:

```html
<!DOCTYPE html>

<html>
    <p>Hello World!</p>
</html>
```

Now you should be able to reload the page for your web site. If you don't have that tab open again, you want to navigate to the EC2 dashboard in AWS, then go to `Instances`, click on your Instance, and look for the `Public IPv4 DNS` label. Next to that is a link that says `open address`.

You should be able to see:

![hello world web page](/images/hello-world.png)

## Done

You're done! Congratulations on learning how to setup a web server on an EC2 instance using Cloud9. :-)
