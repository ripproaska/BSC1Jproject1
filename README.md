# BSC1Jproject1

##Project and learning journal 

##Computer Architecture 

The main theme of this project is to successfully run the operating system in the computer using another software known as virtual box. Virtual box is a cross-platform virtualization application it installs on your existing intel or AMD based computers, whether they are running windows, mac, Linux or Solaris operating systems at the same time. So the first system to install is Ubuntu. 
 - So to install the Ubuntu system in virtual box we need to start the new project naming the system Ubuntu. 
 
 - So after this we need to allocate the ram which can be default but as the Mcguin I put the same amount of ram for the box.
 
 -	This is my first time using the virtual box so I create new hard disk and then next.
 
 -	After the process it will ask us to choose a type of file for new virtual disk which I left in VDI (virtual disk image).
 
 •	Choose the option Dynamically allocated which is getting an allocation from physical hard drive. The recommendation is to not choose the fixed size because we are not a daily user of virtual box. So fixed size takes longer than the usual time to create the virtual hard drive for the desired operating system. So that there could be also possibility that our disk might get crashed while generating virtually fixed size for an operating system. 
 
 •	So after this the virtual disk will create a new which will create a new operating system.
 
 •	So now the location and size of the virtual box can be changed or left default we can use some other drive to install the drive. 
 
 •	The next thing to do to make the virtual hard drive useful is to add the downloaded Ubuntu disk image(.iso) boot on your virtual machine. Click on settings and storage. The under CD/DVD device next to empty, you’ll see a little folder icon.
 
 •	After this select the Ubuntu .iso that we were supposed to download for the Moodle page. And after that select ok.  And the virtual machine will start up.
 
 •	Just hit the continue to proceed. We are told to let the automatic download on but if we make it off this will save time during installation. With this option, installation time will extend to download the updates from the internet. My internet is not working properly at that time which took me hours to install the file, and also not need to install the third party software for graphic and flash etc. 
 
 •	Installation type to choose the potion erase disk and install Ubuntu. It will erase the virtual hard disk which is allocated to install Ubuntu virtually. It will not erase the full drive of computer hard disk but only the allocated space, for the option to be worry only if you are installing on a different pc not virtually. Since the installation is running on virtual disk it is recommended to choose only “erase disk and install Ubuntu”. The encrypt the new Ubuntu installation for security key for encryption purpose in next step. 
 
 •	After the process we are asked to choose the language, location, and keyboard layout. 
 
 •	So in a bit it will ask you to give a hostname, username and password we can encrypt the home directory if we want as well. 
 
 •	And after some installation your server will be ready to use. 
 
 •	So the first thing to do after the server boot up is to log in with the username and password.  And to make it visible to outside world we can change it to bridge adapter and restart it again. 

So now we need to run a web server in our Ubuntu. A web server is a computer system that process requests via HTTP, the basic network protocol used to distribute information on the world wide web. The team can refer to the entire system, or specifically to the software that accepts and supervises the HTTP request. So Apache is the most widely used web server software. It runs on 67% of all webservers in the world. It is fast, reliable and secure. It can be highly customized to meet the needs of many different environments by using extensions and modules. Most WordPress hosting providers use apache as their web server software. However, WordPress can run on other web server software as well.  

After the installation of Ubuntu, we can now develop the LAMP stack in the Ubuntu to host the server. LAMP stands for Linux, Apache, MySQL and PHP. It is the most widely used combination for setting up a web server. So to install and configure the LAMP stack we should start by installing Apache.

-	Sudo apt- get install apache2

Edit the main apache configuration file, apche2.conf, to adjust the keep alive setting:
- File: /etc/apache2/apache2.conf
-	keepAlive off 

The default multi-processing module (MPM) for apache is the event module, but by defeaut PHP uses the prefork module. Open the mpm_prefrok.conf file located in /etc/apache2/mods-available and edit the configuration. Below is the suggested values for a 2 GB linode.

Disable the event module and enable prefork:
 - sudo a2dismod mpm_event
  -sudo a2enmod mpm_prefork 

restart apache 
 - sudo service apache2 restart 

So now there is the several different ways to set up virtual hosts; however, below is the recommended method. By default, apache listens on all IP addresses available to it . 
- within the /etc/apache2/sites-available/ directory create a configuration file for your website, example.com. conf, replacing example.com with your own domain information. 

Create the referenced directories:
-	Sudo mkdir –p/vaar/www/html/example.com/public_html
-	Sudo mkdir /var/www/html/example.com/logs

Link your virtual host file form the sites-available directory to the sites-enabled directory 
-	Sudo a2ensite example.com.conf

Reload apache:
-	Sudo service apache2 reload 

Assuming that you have configured the DNS for your domain to point to your IP address, virtual hosting for your domain should now work. So after the installing and configuration of apache we need to set up for MYSQL.

Install the mysql-server package. 
-	Sudo apt-get install mysql-server
  Need to secure it with password.

Run mysql_secure_installation, a program that helps secure mysql. You will be presented with the opportunity to change the mysql root password, disable root logins outside of localhost, and remove test databases. 
-	mysql_secure_installation

So after this process I start to create mysql database 

Log into mysql.
-	Mysql –u root –p 
And here we need to enter the passoerd and mysql to prompt. 

Create a database and a user with permissions for it. In this example the database is called webdata, the user webuser and password.
-	Create database webdata;
-	Grant all on webdata. * to ‘webiser’ identified by ‘password’;

Exit mysql.
-	Quit

So now to install PHP extension and application repository;
-	Sudo apt-get install php5 php-pear

Once php5 is installed, tune the configuration file located in /etc/php5/apache2/php.ini to enable more descriptive error, logging and better performance. 

Create the log directory for PHP and give the apache user ownership 
-	Sudo mkdir/var/log/php
-	Sudo chown www-data/var/log/php

Reload apache 
-	Sudo service apache2 reload 

So the step by step process of the virtual box and Ubuntu with the LAMP installation in my computer is shown. Not only to install and configure the software this technique and features that virtual box provides are useful for several scenarios.
-	Running multiple operating systems simultaneously 
-	Easier software installations
-	Testing and disaster recovery. 
-	Infrastructure consolidation.

And when dealing with the virtualization I came to know about a lot of terminology like.
-	Host operating system

This is the operating system of the physical computer on which virtual box was installed. There are versions of virtual box for windows, mac, Linux.
-	Guest operating system

This is the operating system that is running inside the virtual machine. Theoretically, virtual box can run any operating system but to achieve near native performance of the guest code on your machine, we had to go through a lot of optimizations that are specific to certain operating systems. So while your favourite operating system may run as a guest, we officially support and optimize for a select few.
