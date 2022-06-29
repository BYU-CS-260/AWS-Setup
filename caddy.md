Now that you have your Cloud9 instance running, you need to configure it as a web server.  
You have access to a full Linux machine and you can install and run software on this server.
We will be teaching you some basic systems administration commands and will be building just
enough command line tools to allow you to be successful. 
First you will open port 80 in the firewall to allow web browsers to connect to your server.  
Then we will set up Caddy, a web server that will answer requests from web browsers.  
We will provide you with minimal instructions on how to use these systems so you arent confused, but 
you are welcome to explore more of the features on your own if you have time.
1. 
2. Congratulations! You now have your own website configured.  
All you have to do is upload html pages to your diretory and they will be served at the URL shown for your EC2 node.  
You can see the URL for the bucket at the bottom of the "Static website hosting" pane.  You can put this into the URL bar of your web browser and you will be able to see the web pages you have uploaded.  
![](images/url.png)  
14. Now go back to your S3 bucket name and upload the index.html file you created and displayed in your Docker web server.  
You should be able to see this page at the URL shown in your "Static website hosting" pane.  
16. You may want to look through the [Cloud9 tutorial](https://docs.aws.amazon.com/cloud9/latest/user-guide/tutorial.html) 
to become more familiar with how Cloud9 works.
