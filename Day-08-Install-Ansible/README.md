# Task 8
Install ansible version 4.10.0 on Jump host using pip3 only. Make sure Ansible binary is available globally on this system, i.e all users on this system are able to run Ansible commands.

# Steps
## Install Ansible with mentioned version on jump host
sudo pip3 install ansible==4.10.0
## Check if ansible is installed or not by using below command
ansible --version
## To check permissions and path of ansible use below command
ls -l $(which ansible)

o/p : -rwxr-xr-x 1 root root 6437 Aug 15 05:27 /usr/local/bin/ansible
