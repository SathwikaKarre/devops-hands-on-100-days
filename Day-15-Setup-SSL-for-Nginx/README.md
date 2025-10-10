# Task 15
The system admins team of xFusionCorp Industries needs to deploy a new application on App Server 1 in Stratos Datacenter. They have some pre-requites to get ready that server for application deployment. Prepare the server as per requirements shared below:

1. Install and configure nginx on App Server 1.

2. On App Server 1 there is a self signed SSL certificate and key present at location /tmp/nautilus.crt and /tmp/nautilus.key. Move them to some appropriate location and deploy the same in Nginx.

3. Create an index.html file with content Welcome! under Nginx document root.

4. For final testing try to access the App Server 1 link (either hostname or IP) from jump host using curl command. For example curl -Ik https://<app-server-ip>/.

# Steps
## Connect to App Server 1 with username and password
ssh tony@stapp01
## Check the SSL files are present under mentioned location
cd /tmp (you will find both mentioned files here)
## Check the status of nginx if not found install it 
systemctl status nginx

sudo yum install nginx -y 
## Move SSL files to appropriate location
mv /tmp/nautilus.crt /etc/pki/tls/certs
mv /tmp/nautilus.key  /etc/pki/tls/private
## Check if those SSl certs are present in the path
ls -l /etc/pki/tls/certs | grep "nautilus.crt"

ls -l /etc/pki/tls/private | grep "nautilus.key"
## Check conf file of nginx to see the IP and SSL cert paths
cd /etc/nginx/

ls -l

vi nginx.conf

server { mention the IP address of server for server name field}

uncomment settings for a TLS enabled server

we should give the server name as IP adress here also

change the paths and ssl certs for ssl_certificate and ssl_certificate_key as well (i.e: /etc/pki/tls/certs/nautilus.cert /etc/pki/tls/private/nautilus.key)
## Restart and check the status of nginx
systemctl restart nginx

systemctl status nginx
## Check if curl statement is working on jumphost
curl -Ik https://stapp01 (response will be 200 OK)
## Follow below steps to change the info in index.html to "Welcome!"
cd /usr/share/nginx/html/

ls -l

vi index.html ( type only Welcome! after deleting the file which is present already)
## Check if conf file has any errors using below command
nginx -t
