# Task 5
1. Install the required SELinux packages.  
2. Permanently disable SELinux for the time being; it will be re-enabled after necessary configuration changes.
3. No need to reboot the server, as a scheduled maintenance reboot is already planned for tonight.
4. Disregard the current status of SELinux via the command line; the final status after the reboot should be disabled.
   
# Steps
## Connect to App Server by using username and password
ssh tony@stapp01
## Check what current OS it is 
cat /etc/os-release (Assume if it is centOS)
## Check status of selinux before by using below command
sestatus
## Install selinux in centOS by using below command
sudo yum install selinux-policy selinux-policy-targeted
## Go to conf path of selinux to make SELINUX to disabled instead of enforcing or any
path : cat /etc/selinux/conf
change : SELINUX = disabled (only if its in other state like enforcing or any)
## Check the selinux status again
sestatus (o/p: disabled)


