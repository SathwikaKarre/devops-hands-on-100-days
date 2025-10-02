# Task 2
Create a user named james on App Server 2 in Stratos Datacenter. Set the expiry date to 2424-03-17, ensuring the user is created in lowercase as per standard protocol.

# Steps
## Connect to AppServer 2 by its username and password
ssh steve@stapp02
## Check if james user is already existing by below command
cat /etc/passwd | grep james
## If user is not exist create a user named james 
sudo useradd james
## If user is already exist modify the user with expiry date
sudo usermod -e 2024-03-17 james (or) sudo chage -E 2024-02-17 james
## Check if expiry date is changed for james user
sudo chage -l james

