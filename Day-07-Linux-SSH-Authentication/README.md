# Task 7
Set up a password-less authentication from user thor on jump host to all app servers through their respective sudo users.

# Steps
## Generate Public private keys on jump host
ssh-keygen -t rsa
## Copy the public key once generated from jump host to all app servers
ssh-copy-id tony@stapp01  (similarly copy for app server 2 and 3)
## Check whether if you can able to connect to all app servers from jump host without password
ssh  tony@stapp01 (It will connect to app server 1 wthout asking for password similarly for app server 2 and 3)
## Check if public key is copied or not by using below commands in any one of the app servers after logged in.
cd ~/.ssh/
ls -l
cat authorized_keys (you will see the jump host public key here which is added)

