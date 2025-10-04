# Task 4
Your task is to grant executable permissions to the /tmp/xfusioncorp.sh script on App Server 1. Additionally, ensure that all users have the capability to execute it.

# Steps
## Connect to App server 1 using username and password
ssh tony@stapp01
## Check what permissions are there for the mentioned script
ls -l /tmp/xfusioncorp.sh
## Change the permission of the script by below mentioned commands
sudo chmod +r xfusioncorp.sh and sudo chmod +x xfusioncorp.sh (or) sudo chmod 555 xfusioncorp.sh       

4(read),2(write),1(execute) 
For execute read is mandatory so -->4+1 = 5
So, as mentioned for all users this access should be there we are giving 555 means read and execute for owners,groups and others.
## Verify the permissions for the mentioned script
ls -l /tmp/xfusioncorp.sh
## Execute the script to check if its executing as execute permissions are now given to it
bash /tmp/xfusioncorp.sh 
