# Task 18
xFusionCorp Industries is planning to host a WordPress website on their infra in Stratos Datacenter. They have already done infrastructure configuration—for example, on the storage server they already have a shared directory /vaw/www/html that is mounted on each app host under /var/www/html directory. Please perform the following steps to accomplish the task:

a. Install httpd, php and its dependencies on all app hosts.

b. Apache should serve on port 6000 within the apps.

c. Install/Configure MariaDB server on DB Server.

d. Create a database named kodekloud_db6 and create a database user named kodekloud_roy identified as password LQfKeWWxWD. Further make sure this newly created user is able to perform all operation on the database you created.

e. Finally you should be able to access the website on LBR link, by clicking on the App button on the top bar. You should see a message like App is able to connect to the database using user kodekloud_roy

# Steps
## Connect to all app servers along with DB server
ssh tony@stapp01 and similarly 2 and 3
## Make the root user 
sudo su -
## Check the OS n all servers 
cat /etc/os-release    (o/p: CentOS)
## Install mariaDB on DB Server
yum install mariadb-server mariadb -y
## Install httpd,php on all app servers along with all dependencies
sudo  dnf install php php-opcache php-gd php-curl php-mysqlnd
sudo yum install httpd -y
## Enable and check the status of mariadb 
systemctl enable mariadb
systemctl status mariadb
systemctl restart mariadb

check the status again as its disabled before
## Enable and check the status of httpd,php on all app servers
systemctl enable httpd php; systemctl restart httpd php; systemctl status httpd php
## Check where Apache is running now
vi /etc/httpd/conf/httpd.conf

search for listen keyword

change port i.e; Listen 6000 and save it
## Restart httpd
systemctl restart httpd
## In database server login to mysql 
sudo -u root mysql

Now we are inside mariadb so now execute the commands
## Create a database in maraidb
create database kodekloud_db6;

show databases;
## Create a user mentioned and grant all privilages
GRANT ALL PRIVILEGES ON kodekloud_db6.* TO 'kodekloud_roy'@'%' identified by 'LQfKeWWxWD';   (This will create user if not exists and grant all privilages)

select user,host from mysql.user;

show grants;


