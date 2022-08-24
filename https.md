# HTTPS Setup

Once you have your web server working, you will want to run it in secure mode with HTTPS instead of HTTP.  
To do this, you will need to modify the ```/etc/caddy/Caddyfile``` to turn on secure mode.
1. Edit the file using the nano editor by running the following command from the command line.
```
nano /etc/caddy/Caddyfile
```
Replace the ":80" with the URL for your web server.
You will have to use the arrow keys to move to different lines in the "Caddyfile".
Then use "^O" to write out the file and "^X" to exit the editor.
<img src="images/caddyhttps.png" width=1000>
2. Restart caddy to make caddy use the new configuration file.
```
sudo systemctl restart caddy
```

3. Now try the URL for your EC2 node using https ```https://ec2-35-86-147-34.us-west-2.compute.amazonaws.com/```
