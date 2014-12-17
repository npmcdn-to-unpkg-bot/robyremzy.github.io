---
layout: post
title: "OwnCloud Party"
modified:
categories:
excerpt: "Set-Up your own cloud with OwnCloud "
tags: []
image:
  feature:
date: 2014-12-01T16:00:42+01:00
---
## OwnCloud 7.0.3 (stable)

To see some some alternatives to Google Contacts and Google Calendar witch i like to use, let's give a try to [OwnCloud](http://owncloud.org/), a file hosting software system.  
Here first, i gonna install OwnCloud on a computer under [Ubuntu](https://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29), later on i might think about push it on a server or on a cloud storage service.

+   Install Owncloud/mysql on a Ubuntu 14.04 LTS distro.
+   Access by localhost and revers DNS.
+   Self-signed certificate for SSL and Android - firewall.
+   Manage contacts and calendar from users.

(ง ͡ʘ ͜ʖ ͡ʘ)ง

### Notions of Network
**This computer will be reachable from the Internet. So you want to put you local [IP adress in DMZ](https://en.wikipedia.org/wiki/DMZ_%28computing%29).**  
see or go to your router configuration to put you local IP (192.168.0.x) in DMZ.  
**You also want your computer to be assigned the same local IP adress under your potential DHCP. So you need to attribute your MAC address to the local IP in DMZ.**
see or go to your router configuration to do lease request of your local IP by sending a DHCPOFFER.  
**Your are now just a bit more secure but not completlly**
see this fabulous page to help you to start to think about your needs [by F.Boulogne](http://blog.cozycloud.cc/tutorial/2013/05/20/first-server-configuration-steps-before-self-hosting-web-services/)
*For big instance you may want to install things on a VirtualHost or a [Linux Containers](http://blog.bodhizazen.net/linux/lxc-linux-containers/) but here for Owncloud well as you wish*





### Update sources list Ubuntu 14.04 and Installation
{% highlight bash %}
sudo sh -c "echo 'deb http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_14.04/ /' >> /etc/apt/sources.list.d/owncloud.list"
sudo apt-get update
sudo apt-get install owncloud owncloud-client
{% endhighlight %}
key storage  
{% highlight bash %}
wget http://download.opensuse.org/repositories/isv:ownCloud:community/xUbuntu_14.04/Release.key
sudo apt-key add - < Release.key
{% endhighlight %}
###Set-Up the MySQL database
{% highlight mysql %}
mysql -u root -p
//password
create database owncloud;
CREATE USER 'owncloud'@'localhost' IDENTIFIED BY 'owncloud';
GRANT ALL PRIVILEGES ON owncloud.* TO 'owncloud'@'localhost' identified by 'PASSWORD_HERE';
FLUSH PRIVILEGES;
{% endhighlight %}

-`д´-  

### OwnCloud access

Reverse DNS (free propose un reverse dns ) : owncloudsksbir.hd.free.fr
Port d'entree qu'on va utiliser : 3443*  

Edit your `confi.php` to be able to use Owncloud on local network and internet.
{% highlight bash %}
sudo nano /var/www/owncloud/config/config.php
{% endhighlight %}
{% highlight php %}
    0 => 'localhost',
    1 => '192.168.0.x',
{% endhighlight %}

Go to [http://localhost/owncloud/](http://localhost/owncloud/) to set-up the Admin account  

> User  
> password  
> Select Mysql  
>> ---  
> Data folder : don't touch it  
>> ---  
> Name: owncloud  
> address: http://localhost/owncloud/  
> password: PASSWORD_HERE  
> Database: owncloud

◞(⚭⃚⃙͐·̫⚭⃚⃙͐)˩✧  


### Certificate, SSL, firewall
secure apache  
{% highlight bash %}
sudo mv /var/www/html/index.html /var/www/html/index.html.ori
sudo echo test > /var/www/html/index.html
{% endhighlight %}  

Creating and importing self-signed certificate to Android device  
http://forum.owncloud.org/viewtopic.php?f=19&t=23913




(☝ ՞ਊ ՞)☝
