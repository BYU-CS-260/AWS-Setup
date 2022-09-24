# Setting up the firewall

Now that you have your Cloud9 instance running, you need to configure the firewall so that people using the web can access your web server (which we will setup next).
A firewall keeps anyone from connecting to your machine on ports that you haven't turned on.  By default, your machine has *no* ports open, so no attackers can get to anything on your machine.

We are going to open the following ports:

- 80 -- this allows HTTP traffic to come to your machine
- 443 -- this allow HTTPS traffic to come to your machine
- 3000-3010 -- this allows traffic on port 3000-3010, which we will use for development purposes
- 8080 -- React will use this port

## Access the EC2 dashboard

Sign into the [AWS console](https://aws.amazon.com/console/) and search for the EC2 service.  Amazon Elastic Compute Cloud (Amazon EC2) is a the service that your Cloud9 web server is running on, so you will need to configure the firewall in the EC2 dashboard.
![](images/ec2.png)

Once you open the dashboard, you should see a menu of Resources:

![EC2 resources menu](/images/ec2-resources-menu.png)

## Security groups

Click on the ID for the security group that is shown and you should see the list of rules that are configured, called `Inbound rules`:

![](images/ec2securitygroup.png)


Notice that the inbound rules allow port 22 to connect to your instance.  This is the port for SSH, and it is configured so that your Cloud9 service can connect to your instance using SSH.

## Add rules for port 80

Click the `Edit inbound rules` button and then the `Add rule` button at the bottom left.

![](images/inboundrules.png)


* Change the `Type` to HTTP (for port 80)
* Change the `Source` to Anywhere-IPv4`
  
This allows anyone to connect to your server form anywhere on the Internet, using IPv4.

Some of you may connect from home using an IPv6 address. So do this entire process again, adding a second rule that has:

* Change the `Type` to HTTP (for port 80)
* Change the `Source` to Anywhere-IPv6`

## Add rules for port 443

Add a rule with:

* Change `Type` to HTTPS (for port 443)
* Change the `Source` to Anywhere-IPv4`

Add a rule with:

* Change `Type` to HTTPS (for port 443)
* Change the `Source` to Anywhere-IPv6`

## Add rules for port 3000-3010

Add a rule with:

* Change `Type` to Custom TCP
* Change Port Range to 3000-3010
* Change the `Source` to Anywhere-IPv4`

Add a rule with:

* Change `Type` to Custom TCP
* Change Port Range to 3000-3010
* Change the `Source` to Anywhere-IPv6`

## Add rules for port 8080

Add a rule with:

* Change `Type` to Custom TCP
* Change Port Range to 8080
* Change the `Source` to Anywhere-IPv4`

* Change `Type` to Custom TCP
* Change Port Range to 8080
* Change the `Source` to Anywhere-IPv6`

[Next Tutorial](caddy.md)
