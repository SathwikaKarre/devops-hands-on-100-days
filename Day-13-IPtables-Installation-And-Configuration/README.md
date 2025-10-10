# Task 13
We have one of our websites up and running on our Nautilus infrastructure in Stratos DC. Our security team has raised a concern that right now Apache’s port i.e 8089 is open for all since there is no firewall installed on these hosts. So we have decided to add some security layer for these hosts and after discussions and recommendations we have come up with the following requirements:

1. Install iptables and all its dependencies on each app host.

2. Block incoming port 8089 on all apps for everyone except for LBR host.

3. Make sure the rules remain, even after system reboot.

# Steps
## Connect to all app servers using username and password
ssh tony@stapp01 similarlly others
## Make the root access for all app servers
sudo su -
## Check the OS of this app servers
cat /etc/os-release  (o/p: Cent OS)
## Install the iptables and its dependencies on all app servers
yum install iptables-services -y
## To list the iptables along with line numbers
sudo iptables -L -n --line-numbers  

-L (list the iptables)

-n (show the ip adresses dont resolve to DNS like example.com)

--linenumbers (gives numbers to iptables)
## Now make the port closed for all app servers except LBR server by using below commands
sudo iptables -I INPUT 1 -p tcp --dport 8089 -s stlb01 -j ACCEPT   (stlb01 is accepted to access through 8089 port)

sudo iptables -I INPUT 2 -p tcp --dport 8089 -j DROP (all other app servers is droped from access through 8089 port)
## To make sure changes of iptables as it is after reboot use below command to save it
service iptables save
## Verify connecting using telnet
telnet stapp01 8089 , telnet stapp02 8089 , telnet stapp03 8089  (accessible when logged in with stlb01 server)

This is not accessibile through app server 1,2,3 when checked

Hence the commands we executed are correct and task is solved.
