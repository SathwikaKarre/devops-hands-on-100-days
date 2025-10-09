# Task 14
The production support team of xFusionCorp Industries has deployed some of the latest monitoring tools to keep an eye on every service, application, etc. running on the systems. One of the monitoring systems reported about Apache service unavailability on one of the app servers in Stratos DC.

Identify the faulty app host and fix the issue. Make sure Apache service is up and running on all app hosts. They might not have hosted any code yet on these servers, so you don’t need to worry if Apache isn’t serving any pages. Just make sure the service is up and running. Also, make sure Apache is running on port 3004 on all app servers.

# Steps
## Connect to all app servers
ssh tony@stapp01 similarlly connect to server 2 and 3 as well
## Check the status of httpd in all app servers using below command
sudo systemctl status httpd -l

-l here indicates the lines info is not hidden.

If status is inactive follow below steps in all servers if status is active everything is fine.
## Check httpd.conf to see what port is defined inside it (it will be anyway 5003)
vi /etc/httpd/conf/httpd.conf
## Check if any of the other process are running on this port using below command
netstat -luntp | grep 3004   (o/p: [tcp ...... 443(pid)])

-l (show listening sockects)

-u (udp)

-n (numeric addresses or ports)

-t (tcp)

-p (process id)
## Kill the PID which is running on port 5003
kill 443
## Restart and check the status again for httpd (Apache)
sudo systemctl restart httpd

sudo systemctl status httpd

Now the status of httpd will be active.
## Check by using curl command whether you are able to see html output 
curl http://stapp01:3004

You will see html output that means Apache(httpd) is running successfully and status of it is active.
