# Task 9
There is a critical issue going on with the Nautilus application in Stratos DC. The production support team identified that the application is unable to connect to the database. After digging into the issue, the team found that mariadb service is down on the database server.

Look into the issue and fix the same

# Steps
## Login to DB Server from jump host
ssh peter@stdbserver
## Check status of mariadb with this command
sudo systemctl status mariadb

Check logs to get some idea for the failure (for me it is due to different owner for mariadb folder. Mariadb is running on mysql)

use --- journalctl -xe | grep mariadb to check yours

## Check below log 
check /var/log/mariadb/mariadb.log for detailed log using cat.

## Run below commands
run cd /var/run; 

ls -la and 

w.r.to mariadb folder make sure both username and group name must be mysql if not change it. (This is the error in my case)

## To change the owner use below command
run chown mysql:mysql mariadb

## Now run below command to restart mariadb
sudo systemctl restart mariadb (you will get no output)

## check status of mariadb by using below command
sudo systemctl status mariadb (It should be active and running state)

## Some other helpful commands for troubleshooting
df -h - To check disk space

free -m / top - To check for memory space

ls -ld /var/lib/mysql - To check permission issues

## To check port issues use below commands
sudo netstat -tulnp | grep 3306

sudo ufw status



