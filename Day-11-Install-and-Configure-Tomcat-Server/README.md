# Task 11
The Nautilus application development team recently finished the beta version of one of their Java-based applications, which they are planning to deploy on one of the app servers in Stratos DC. After an internal team meeting, they have decided to use the tomcat application server. Based on the requirements mentioned below complete the task:

a. Install tomcat server on App Server 2.

b. Configure it to run on port 6000.

c. There is a ROOT.war file on Jump host at location /tmp.

Deploy it on this tomcat server and make sure the webpage works directly on base URL i.e curl http://stapp02:6000

# Steps
## Check the ROOT.war under /tmp in jump host server
ls -l
## Copy the ROOT.war to app server 2 by using below command
scp /tmp/ROOT.war steve@stapp02:/tmp
## Check if you got ROOT.war in app server 2 by login
ssh steve@stapp02 (check under /tmp directory you will find ROOT.war)
## Check tomcat status 
sudo systemctl status tomcat (you will find no tomcat found)
## check the OS
cat /etc/os-release  (o/p: CentOS)
## Install tomcat server
sudo yum install tomcat
## Check status of tomcat server again
sudo systemctl status tomcat
## Change the port number of tomcat
cd /etc/tomcat

ls -l

sudo vi server.xml

Here check for connector port and change it to 6000
## Copy the ROOT.war to tomcat server where it hosts
sudo cp /tmp/ROOT.war /usr/share/tomcat/webapps/
## Restart the tomcat server 
sudo systemctl restart tomcat
## Check status of tomcat server again
sudo systemctl status tomcat
##  Check the curl http://stapp02:6000 
output will be some html output which means webpage is working on the URL.
