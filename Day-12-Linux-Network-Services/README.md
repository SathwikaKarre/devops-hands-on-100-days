# Task 12
Our monitoring tool has reported an issue in Stratos Datacenter. One of our app servers has an issue, as its Apache service is not reachable on port 5003 (which is the Apache port). The service itself could be down, the firewall could be at fault, or something else could be causing the issue.

Use tools like telnet, netstat, etc. to find and fix the issue. Also make sure Apache is reachable from the jump host without compromising any security settings.

Once fixed, you can test the same using command curl http://stapp01:5003 command from jump host.

Note: Please do not try to alter the existing index.html code, as it will lead to task failure.

# Steps
## Check the connection status of all app servers
telnet stapp01 5003  (connection failed)

telnet stapp02 5003  (connection success)

telnet stapp03 5003  (connection success)
## Connect to app server 1
ssh tony@stapp01

sudo su -
## Check the status of httpd service
systemctl status httpd    (failed- because already its listening)
## Check if its listening by using below command
netstat -lntp | grep 5003  (o/p is one [tcp 444/sendmail]which is listening so kill that)

kill 444

netstat -lntp | grep 5003  (o/p is none)
## Restart and check the status
sudo systemctl restart httpd

sudo systemctl status httpd

Still connection is not working then its an firewall issue
## Check the firewall issue using below command
iptables -L -n

you are seeing the only 22 port is enabled remaining all are rejected so you need to enable the 5003 port and you should keep this at start of ip tables.
## Open firewall port in ip tables in linux i.e-5003
sudo iptables -I INPUT 1 -p tcp --dport 5003 -j ACCEPT

This will make sure the 5003 port will be at first row of ip tables to enable firewall
## Again restart and check the status
sudo systemctl restart httpd

sudo systemctl status httpd
## Check by using curl http://stapp01:5003
you will get output of some html format which means the webapp is working fine on URL.


