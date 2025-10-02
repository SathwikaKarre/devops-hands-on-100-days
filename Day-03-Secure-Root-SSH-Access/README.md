# Task 3
Your task is to disable direct SSH root login on all app servers within the Stratos Detacenter.

# Steps
## Connect to all App servers by username and password
ssh tony@stapp01 similar way connect for all servers
## Change the PermitRootLogin to "No" in all app servers
sudo vi /etc/ssh/sshd_config  and change the permitrootlogin to "no"
## Restart to apply the changes
sudo systemctl restart sshd
## Check whether PermitRootLogin is "No" by using below command
sudo cat /etc/ssh/sshd_config | grep -i "PermitRootlogin"
