# Task 16
Day by day traffic is increasing on one of the websites managed by the Nautilus production support team. Therefore, the team has observed a degradation in website performance. Following discussions about this issue, the team has decided to deploy this application on a high availability stack i.e on Nautilus infra in Stratos DC. They started the migration last month and it is almost done, as only the LBR server configuration is pending. Configure LBR server as per the information given below:

a. Install nginx on LBR (load balancer) server.

b. Configure load-balancing with the an http context making use of all App Servers. Ensure that you update only the main Nginx configuration file located at /etc/nginx/nginx.conf.

c. Make sure you do not update the apache port that is already defined in the apache configuration on all app servers, also make sure apache service is up and running on all app servers.

d. Once done, you can access the website using StaticApp button on the top bar.

# Steps
## Connect to Load balancer server
ssh loki@stlb01
## Make the server as root access
sudo su -
## Check the status of nginx
systemctl status nginx (not installed nginx so install it)
## Check the OS of the server
cat /etc/os-release
## Install nginx on the load balancer server
yum install nginx -y
## Check the staus and restart of nginx
systemctl status nginx

systemctl restart nginx
## Check the app server 1,2,3 http status and check the port for httpd process
sudo su -       (make root)

systemctl status httpd

ss -luntp | grep httpd    (o/p:  tcp ........   0.0.0.0:6300) --- 6300 is the port number
## Do the below process in load balancer server
sudo su -    (Make the root access)

vi /etc/nginx/nginx.conf  (open conf file of nginx)
### Add the below logic in nginx conf file
#### Add the below logic under httpd 

 upstream myapp1 {

        server stapp01:6300;

        server stapp02:6300;

        server stapp03:6300;

    }

#### Add the below logic after server

location / {

            proxy_pass http://myapp1;

        }
# Using nginx as HTTP load balancer
The simplest configuration for load balancing with nginx may look like the following:

http {

    upstream myapp1 {

        server srv1.example.com;

        server srv2.example.com;

        server srv3.example.com;

    }

    server {

        listen 80;

        location / {

            proxy_pass http://myapp1;

        }

    }

}
## Restart and check the status of nginx
systemctl restart nginx

systemctl status nginx
## Check the syntax of nginx configuration by using below command
sudo nginx -t
## Check by using start website button
You will see content coming in website

