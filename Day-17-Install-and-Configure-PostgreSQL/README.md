# Task 17
The Nautilus application development team has shared that they are planning to deploy one newly developed application on Nautilus infra in Stratos DC. The application uses PostgreSQL database, so as a pre-requisite we need to set up PostgreSQL database server as per requirements shared below:

PostgreSQL database server is already installed on the Nautilus database server.

a. Create a database user kodekloud_top and set its password to GyQkFRVNr3.

b. Create a database kodekloud_db4 and grant full permissions to user kodekloud_top on this database.

Note: Please do not try to restart PostgreSQL server service.
# Steps
## Connect to Nautilus database server using username and password
ssh peter@stdb01
## Check the status of postgresql
systemctl status postgresql
## Use below command to enter postgresql terminal
sudo -u postgres psql
## Check for user names using below command
\du
## Check for list of databases using below command
\l
## Create the new user in postgresql server
create user kodekloud_top with password 'GyQkFRVNr3';
## Check if user is created in postgresql server 
\du
## Create a database in postgresql server using below command 
create database kodekloud_db4;
## Check if database is created
\l
## Grant all privilages for the database using below command
grant all privileges on database kodekloud_db4 to user kodekloud_top;
## Check if database has full permissions using below command 
\l
