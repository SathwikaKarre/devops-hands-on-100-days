# Task 1
Create a user named kareem with a non-interactive shell on App Server 1.

# Steps
## Connect to app server 1 by its username and password given.
ssh tony@stapp01
## Make it the root user to work few executed commands
sudo su -
## Check if user kareem already exists
cat /etc/passwd | grep kareem
## If kareem is not exist create a new user named kareem with a non-interactive shell.
sudo useradd kareem --shell /sbin/nologin

