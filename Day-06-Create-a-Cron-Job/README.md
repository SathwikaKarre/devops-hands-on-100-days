# Task 6
1. Install cronie package on all Nautilus app servers and start crond service
2. Add a cron */5 * * * * echo hello > /tmp/cron_text for root user.

# Steps
## Connect to all app servers using username and password
ssh banner@stapp03
## Check what is the OS of this server
cat /etc/os-release
## Install Crontab in the server
sudo yum  install cronie -y
## Check the status of crontab
sudo systemctl status crond
(It is enabled but in inactive state to make it active start crontab)
## Start the crontab to make it active
sudo systemctl restart crond
(Now it will be in active state)
## Check if any cronjobs are there for root user
sudo crontab -u root -l (or) sudo crontab -l
## Check cronjobs for default user which is logged in 
crontab -l
## Update cron job for root user by below command 
sudo crontab -e

add cron job here which is given (*/5 * * * * echo hello > /tmp/cron_text)

Check after 5 min you will see hello in the text file mentioned.(For every 5 min script executes)

