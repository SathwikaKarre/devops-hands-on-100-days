# Task 10
The production support team of xFusionCorp Industries is working on developing some bash scripts to automate different day to day tasks. One is to create a bash script for taking websites backup. They have a static website running on App Server 2 in Stratos Datacenter, and they need to create a bash script named blog_backup.sh which should accomplish the following tasks. (Also remember to place the script under /scripts directory on App Server 2).

a. Create a zip archive named xfusioncorp_blog.zip of /var/www/html/blog directory.

b. Save the archive in /backup/ on App Server 2. This is a temporary storage, as backups from this location will be clean on weekly basis. Therefore, we also need to save this backup archive on Nautilus Backup Server.

c. Copy the created archive to Nautilus Backup Server server in /backup/ location.

d. Please make sure script won't ask for password while copying the archive file. Additionally, the respective server user (for example, tony in case of App Server 1) must be able to run it.

# Steps
## Connect to App server 2 
ssh steve@stapp02
## Create an file named blog_backup.sh under /scripts directory
touch blog_backup.sh
## Give execute permissions to this shell script
chmod +x blog_backup.sh
## Write shell script with mentioned tasks
#!/bin/bash

echo "create a zip archive"

zip -r /backup/xfusioncorp_blog.zip /var/www/html/blog

echo "copy the zip file to the backup server"

scp /backup/xfusioncorp_blog.zip clint@stbkp01:/backup

echo "execution success"

save by using :wq! to the shell script file
## To make sure script passsword less execution of the script use below commands
ssh-keygen -t rsa (generates public and private key of that user or server)

ssh-copy-id clint@stbkp01 (copies public key in authorized keys of backup server)

So, now execute script and the script will execute successfully


