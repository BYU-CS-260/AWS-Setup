# AWS Setup
During this class, you will be developing web applications that people throughout the world (like your Mom) to be able to see.  In order to do this, we will be using a cloud based web server to serve your applications.  

Amazon Web Services (AWS) provides access to cloud based web servers through their [Cloud9](https://aws.amazon.com/cloud9/) service.  
In this learning activity, you will set up your Amazon AWS account and then will create a Cloud9 instance to serve your web pages.  

1. In your browser, select the [AWS login page](https://portal.aws.amazon.com/gp/aws/developer/registration/) and select “Create a new AWS account”.  
![](images/login.png)  
2. Fill in your address information  
![](images/signup.png)  
3. On the next screen, you will enter a credit card.  There should not be charges for normal usage for the class.  If you have signed up before, there may be a charge for around $3.50 per month.  Since we dont have a book for this class, consider this to be the cost of the book you would have purchased.  
![](images/free.png)  
4. Congratulations!  You have now set up your account and can access an incredible number of cloud services.  Once you understand how to use an Amazon cloud server, you will be able to use other cloud providers (like Google) if you want to investigate them in the future.  
![](images/congrats.png)  
5. You should get an email from amazon with links to training materials and information on how to get started.  Make sure the email doesn't end up in your SPAM folder.  You will want to be able to receive emails from Amazon in the future.  
![](images/email.png)  
6. Now you want to create a web server with Cloud9 so that your Mom can see your amazing web pages. [Sign into the AWS console](https://signin.aws.amazon.com/) as the Root User.  
![](images/root.png)  
7. Then search for "Cloud9" in the upper left search bar.  
![](images/cloud9.png)  
8. Create a Cloud9 environment
![](images/createenv.png)
9. Give your environment a name (pick whatever you want, but make it meaningful).
![](images/nameenv.png)
10. Configure the Cost-saving settings so that the web server will never hibernate.
![](images/configsettings.png)
11. Then create the environment.  It can take several minutes to set up your server.  The system is allocating a virtual server on a real computer somewhere in the Amazon Web Services infrastructure.  You should select the "US West (N. California)" region for your server in the upper right corner of the screen.
![](images/docreate.png)
12. You should now be able to see your Cloud9 window.  On the left pane is your directory or folder browser, in the center is your editor and on the bottom you will see a command line interface that will allow you to type commands for your server.
![](images/cloud9screen.png)
13. Congratulations! You now have your own website configured.  All you have to do is upload html pages to this S3 bucket and they will be served at the URL shown for your S3 bucket.  You can see the URL for the bucket at the bottom of the "Static website hosting" pane.  You can put this into the URL bar of your web browser and you will be able to see the web pages you have uploaded.  
![](images/url.png)  
14. Now go back to your S3 bucket name and upload the index.html file you created and displayed in your Docker web server.  You should be able to see this page at the URL shown in your "Static website hosting" pane.  
16. You may want to look through the [Cloud9 tutorial](https://docs.aws.amazon.com/cloud9/latest/user-guide/tutorial.html) to become more familiar with how Cloud9 works.
