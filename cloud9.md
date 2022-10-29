# Setting Up Cloud9

Now you want to  setup the Cloud9 IDE. When you use Cloud9, you are actually using an EC2 instance, which is a virtual machine running Linux in Amazon's cloud. Cloud9 provides a convenient way to manage that Linux machine, plus also edit files in an IDE. 

## Cloud9 service

To get to the Cloud9 service, [Sign into the AWS console](https://signin.aws.amazon.com/) as the Root User.  
<img src="images/root.png" width=300> 

Then search for "Cloud9" in the upper left search bar.  
<img src="images/cloud9.png" width=750>  

## Create a Cloud9 IDE

Click Create a Cloud9 environment

<img src="images/createenv.png" width=750>

**Be sure to should select the "US West (N. California)" region for your server in the upper right corner of the screen.**

Then give your environment a name (pick whatever you want, but make it meaningful).

<img src="images/nameenv.png" width=750>

## Configure settings

Use the defaults for an EC2 instance (direct access) and a t3.small instance type.

**Be sure to select `Ubuntu Server` for the platform.**

Configure the `Cost-saving settings` so that the web server will never hibernate.

<img src="images/configsettings.png" width=750>

Then click `Next Step` to setup the environment.

## Wait

It can take several minutes to set up your server.  The system is allocating a virtual server on a real computer somewhere in the Amazon Web Services infrastructure.  

<img src="images/docreate.png" width=500>

## Done

You should now be able to see your Cloud9 window.  On the left pane is your directory or folder browser, in the center is your editor and on the bottom you will see a bash terminal that will allow you to type commands to manage your server.

<img src="images/cloud9screen.png" width=750>

[Next Tutorial](firewall.md)
