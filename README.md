-	Create a key pair and select the sg that we created earlier that is monolith# infotrixs
Cloud Intern (AWS) Report

Task: Deploy application in monolithic and microservices architecture
❖ Description:
- For monolithic: 1 EC2 instance, deploy WordPress and MYSQL on the same instances
- For microservices: 2 EC2 instance, 1 for WordPress and 1 for MYSQL
- Configure the necessary security group for the instances
- EC2 instance type: t2-micro, AMI: ubuntu-*
❖ Create a welcome page in WordPress that will be the homepage
❖ Goal to this task to check your understanding level
❖ Create a video and report of how you completed it with proper screenshots

Monolithic: 
1.	Create a EC2 instance with Ubuntu OS
-	Lets start with Creating a security group for monolith server
-	Goto AWS console and search for security groups  
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/76575462-8d6e-44ef-b5ff-346b4398a7ef)
-	Click on create security group and Fill the details
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/a064c1bf-acb2-4367-a1ab-f9f3edf7568f)
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/66c03304-b785-440f-825c-b2264fc62641)
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/b1c40763-b0d5-45ac-8958-b065da6a5139)
-	Click create security group. It will create a sg.

-	Now go to EC2 and Click Launch instance 
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/2a8859a0-f60e-4e39-bf54-af31ba417d8e)
-	Now give a name for instance, select the ubuntu AMI and t2.micro instance type
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/314c0c20-3d9b-447f-aa7b-76ce636caf0e)
-	Create a key pair and select the sg that we created earlier that is monolith
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/421c3282-dc93-4020-a026-e63749fb771d)
-	Now hit the Launch instance
  ![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/cdba232f-0841-4dc1-95a3-333b41919b9c)
hat will create a instance.

-	Now log in to the monolith instance using ssh
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/fda6c3bb-a1f1-4fcd-87dc-9399b7912425)
2.	Installing Dependencies 
-	WordPress requires Apache2 and php to be installed
-	To install PHP, Apache and mysql, use following command:
       sudo apt update
         sudo apt install apache2 \
                 ghostscript \
                 libapache2-mod-php \
                 mysql-server \
                 php \
                 php-bcmath \
                 php-curl \
                 php-imagick \
                 php-intl \
                 php-json \
                 php-mbstring \
                 php-mysql \
                 php-xml \
                 php-zip
-	Copy the instance public IP and open it in 
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/5c56e9b4-af76-4c13-9414-d0d7b8389a5d)
3.	Install WordPress
-	Create the installation directory and download the file from WordPress.org:

sudo mkdir -p /srv/www
sudo chown www-data: /srv/www
curl https://wordpress.org/latest.tar.gz | sudo -u www-data tar zx -C /srv/www
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/b867d5e3-0c27-4c13-bc3e-3f52d489ba2b)
4.	Configure Apache for WordPress
- Create Apache site for WordPress. Create /etc/apache2/sites-available/wordpress.conf with    following lines:
<VirtualHost *:80>
    DocumentRoot /srv/www/wordpress
    <Directory /srv/www/wordpress>
        Options FollowSymLinks
        AllowOverride Limit Options FileInfo
        DirectoryIndex index.php
        Require all granted
    </Directory>
    <Directory /srv/www/wordpress/wp-content>
        Options FollowSymLinks
        Require all granted
    </Directory>
</VirtualHost>
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/57cf6ae2-53db-4a46-94f4-f4c09efdddf4)
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/53c7a112-9377-499e-aff1-e30e5e226994)
-	Enable the site with:
sudo a2ensite wordpress
-	Enable URL rewriting with:
sudo a2enmod rewrite
-	Disable the default “It Works” site with:
sudo a2dissite 000-default
sudo service apache2 reload
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/9a6eb7e4-c29d-4694-9786-4304b118101a)
1.	Configure Database
-	Run below commands
sudo mysql -u root
mysql> CREATE DATABASE wordpress;
mysql> CREATE USER wordpress@localhost IDENTIFIED BY '<your-password>';
mysql> GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,ALTER ON wordpress.* TO wordpress@localhost;
mysql> FLUSH PRIVILEGES; 
mysql> quit
sudo service mysql start
2.	Configure WordPress to connect to the database 
-	Now, let’s configure WordPress to use this database. First, copy the sample configuration file to wp-config.php:
sudo -u www-data cp /srv/www/wordpress/wp-config-sample.php /srv/www/wordpress/wp-config.php
-	Open the wp-config.php and change the 'DB_NAME', 'DB_USER', 'DB_PASSWORD' with our database’s name, user and password.
sudo vi /srv/www/wordpress/wp-config.php 
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/89c9f3cf-cd74-4a84-a1ab-afcbfb3cff20)
And save it by :wq
7.	Configure WordPress
-	Open http://localhost/ in your browser. You will be asked for title of your new site, username, password, and address e-mail. 
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/f07107fe-c08f-41fe-a2ba-d2fe9baa1295)
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/9250658a-e910-4c97-9a5f-8af4cced0cff)
-	Now Login with the credentials. You’ll see a welcome page.
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/a72ec0c5-2977-4a87-b729-dd29ce8ecec7)
-	Goto posts  add post and write something. It’ll Create a post.
-	Copy the url and open in a browser to access your website




Microservices
1.	Create a security group for both WordPress server and Mysql server
-	Add inbound rules ssh and http for wordpress sg
  -	Create another sg for mysql and make ssh and 3302 port open
![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/376e596d-a297-4663-aa91-685aebc978d6)
-	Click create security group to create them.
1.	Launch instances
-	Go to EC2 console and create two ubuntu instances as we created for monolith, name them WordPress and Mysql 
Attach wordpress sg which we created earlier to the WordPress instance

-	Attach mysql sg to the Mysql instance and launch the instances
3.	Install mysql

-	ssh into the mysql server
-	-	Use the commands to install mysql
sudo apt update 
sudo apt install mysql-server -y
-	As default the mysql doesn’t accept remote connections
-	To make mysql accept remote connections, Change the bind-address to the database server’s private IP to configure the Mysql to accept remote connections:
sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf 
-	Restart mysql
sudo systemctl restart mysql
-	Log in to mysql as root, create the database and remote user, and grant the remote user access to the database. Replace 172.31.47.58 with your wordpress server’s private IP:
sudo mysql -u root -p
CREATE DATABASE wordpress;
CREATE USER 'wpuser'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON wordpress.* TO 'wpuser'@'localhost';
CREATE USER 'wpuser'@'172.31.47.58' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON wordpress.* TO 'wpuser'@'172.31.47.58';
FLUSH PRIVILEGES;
Exit
4.	Install and Configure WordPress

-	Log in into wordpress server using ssh
-	To install dependencies
sudo apt update
sudo apt install apache2 \
                 ghostscript \
                 libapache2-mod-php \
                 mysql-server \
                 php \
                 php-bcmath \
                 php-curl \
                 php-imagick \
                 php-intl \
                 php-json \
                 php-mbstring \
                 php-mysql \
                 php-xml \
                 php-zip
-	To install WordPress run the following commands
sudo mkdir -p /srv/www
sudo chown www-data: /srv/www
curl https://wordpress.org/latest.tar.gz | sudo -u www-data tar zx -C /srv/www
-	Create Apache site for WordPress. Create /etc/apache2/sites-available/wordpress.conf with following lines:
<VirtualHost *:80>
    DocumentRoot /srv/www/wordpress
    <Directory /srv/www/wordpress>
        Options FollowSymLinks
        AllowOverride Limit Options FileInfo
        DirectoryIndex index.php
        Require all granted
    </Directory>
    <Directory /srv/www/wordpress/wp-content>
        Options FollowSymLinks
        Require all granted
    </Directory>
</VirtualHost>
-	Run this commands
sudo a2ensite wordpress
sudo a2enmod rewrite 
sudo a2dissite 000-default
sudo service apache2 reload

5.	Configure WordPress to Use a Remote Database

-	Now, let’s configure WordPress to use this database. First, copy the sample configuration file to wp-config.php:
sudo -u www-data cp /srv/www/wordpress/wp-config-sample.php /srv/www/wordpress/wp-config.php
-	Edit the wordpress configuration file as we edited for monolithic setup. DB_HOST = mysql server’s Privite IP
sudo vi /srv/www/wordpress/wp-config.php

- Test remote login with the new remote user.

![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/828ceb4c-7468-4251-9b3b-963f0eaa8b0c)
-	Open http://localhost/ in your browser. You will be asked for title of your new site, username, password, and address e-mail.

  ![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/2e1c69fe-9e15-4017-a4ee-db71c6e86276)
-	Log in with your credentials and you can see a welcome page

![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/39f2bcc0-10f2-4b40-91d3-862ab48502c4)
-	Goto posts  add post and write something. It’ll Create a post.
-	Copy the url and open in a browser to access your website.

![image](https://github.com/saivamsipranay/infotrixs/assets/123617597/b6e5b9b5-d193-49f5-98d8-e6d4d4ec2a42)

