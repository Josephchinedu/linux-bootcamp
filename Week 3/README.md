Lab 1: Install a LAMP stack on an Azure Linux VM
1. Create a resource group
![resource group](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab1_rsgroup.PNG?raw=true)

2. Create a virtual machine
![vm](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab1_vm.PNG?raw=true)

3. Open port 80 for web traffic
![port 80](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab1_port80-1.PNG?raw=true)

![port 80](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab1_port80-2.PNG?raw=true)

4. SSH into your VM
![port 80](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab1_ssh.PNG?raw=true)

5. Install Apache, MySQL, and PHP
![Apache](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab1_apache.PNG?raw=true)

![Apache version](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab1_apache_v.PNG?raw=true)

![Apache live](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab1_apache_live.PNG?raw=true)

##### Verify and secure MySQL
![sql version](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab1_apache_sql_v.PNG?raw=true)

##### Verify PHP
![php](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab1_apache_php.PNG?raw=true)

![php live](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab1_apache_php_live.PNG?raw=true)

6. Install WordPress
##### Install WordPress package
![WordPress](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab1_wordpress.PNG?raw=true)


##### Configure WordPress
![WordPress](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab1_wordpress_config.PNG?raw=true)

![WordPress](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab1_wordpress_live.PNG?raw=true)

![WordPress](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab1_wordpress_dashboard.PNG?raw=true)

# Lab 2: Install a LAMP stack on an Amazon Linux AMI
1. Prepare the LAMP server
##### Connect to your instance.
![aws instance](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_new_instance.PNG?raw=true)

##### update all packages
![aws instance](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_update_pkg.PNG?raw=true)

##### install the Apache web server, MySQL, and PHP software packages
![aws instance](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_update_pkg.PNG?raw=true)

##### install lamp-mariadb10.2-php7.2 and php7.2
![php7.2](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_php.PNG?raw=true)


##### install multiple software packages and all related dependencies
![packages](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_pkg.PNG?raw=true)

##### Start the Apache web serve
![Apache](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_start_httpd.PNG?raw=true)

##### Use the systemctl command to configure the Apache web server to start at each system boot.
![Apache web server](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_systemctl.PNG?raw=true)

2. Test your Lamp server
##### Create a PHP file in the Apache document root.
![Lamp server](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_php_write.PNG?raw=true)

![PHP Live](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_aws-live.PNG?raw=true)

3. Secure the database server
##### Run mysql_secure_installation.
![mysql_secure_installation](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_secure.PNG?raw=true)

##### stop mariadb
![mysql_secure_installation](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_stopdb.PNG?raw=true)

##### enable mariadb
![mysql_secure_installation](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_enable3.PNG?raw=true)

4. Install phpMyAdmin
##### Install the required dependencies
![mysql_secure_installation](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_php_admin.PNG?raw=true)

##### Restart Apache.
![mysql_secure_installation](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_startapache.PNG?raw=true)

![mysql_secure_installation](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_phplogin.PNG?raw=true)

![mysql_secure_installation](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/week3_lab2_logined.PNG?raw=true)