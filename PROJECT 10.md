# LOAD BALANCER SOLUTION WITH NGINX AND SSL/TLS
## created Nginic LB server with port 80 and 443 opened to allow incoming traffic
## Updated/etc/hosts file for local DNS with Web Servers’ names and their local IP addresses
![image](https://user-images.githubusercontent.com/101482368/160530552-2d7183b3-87c8-42b2-9ae4-ebab5b4c77cd.png)
## installed Niginix after running update
![image](https://user-images.githubusercontent.com/101482368/160532531-500ed4a5-0aa3-4e4f-972b-e3c4c2e3d608.png)
## Configured Nginx LB using Web Servers’ names defined in /etc/hosts
![image](https://user-images.githubusercontent.com/101482368/160533157-ceb936e7-8d7f-42db-a30d-9b36f168ab34.png)
## restarted Nginx server
![image](https://user-images.githubusercontent.com/101482368/160533503-4aa72ae9-0f09-41f3-b85d-8a49f39eb9e1.png)
## REGISTERED A NEW DOMAIN NAME AND CONFIGURED SECURE CONNECTION USING SSL/TLS CERTIFICATES
![image](https://user-images.githubusercontent.com/101482368/160538662-fe6cffc3-941a-45af-a03f-5a44524bad77.png)
## Configured name server of my new domain. replaced with the name server from the domain created in hosted zone in Route 53 AWS
![image](https://user-images.githubusercontent.com/101482368/160541523-b4e52a17-0215-4ba2-83a0-e93fbcd8c462.png)
![image](https://user-images.githubusercontent.com/101482368/160541482-9fa1cad9-b555-47f3-8452-8fe9e4aae94c.png)
# created Record that is poiting to Nginx LB Elastic IP address
![image](https://user-images.githubusercontent.com/101482368/160542557-7f4ddf59-d071-4fe9-b916-2ebdf40c9eb5.png)
![image](https://user-images.githubusercontent.com/101482368/160542719-9a8268d8-1457-429f-a688-1e26cf8fdc4d.png)
## update Nginx config with registered domain name "idrisu.com
![image](https://user-images.githubusercontent.com/101482368/160543944-fecf7406-f4a9-4089-aaa0-deb1e04a8f2d.png)
## snap is running
![image](https://user-images.githubusercontent.com/101482368/160544109-a636912b-665a-45f6-9a65-47066f42848c.png)
## Installed certbot and request for an SSL/TLS certificate
![image](https://user-images.githubusercontent.com/101482368/160544377-76a99f75-4a1e-49ea-a3a9-da946d0de396.png)
## successfully received and deployed certificate to www.idrisu.com
![image](https://user-images.githubusercontent.com/101482368/160544882-5b2754b3-22af-47da-8591-89a1b188d8c0.png)
## Verified secure on the web browser at www.idrisu.com
![image](https://user-images.githubusercontent.com/101482368/160545605-d37d91f3-8c15-43ff-8c22-671e1af98fa5.png)
## test renewal command in dry run mode
![image](https://user-images.githubusercontent.com/101482368/160546001-b167d9a2-dd59-404b-a44d-0ca6fcc37e3c.png)
## Scheduled job that is to run renew command periodically.by configuring a cronjob to run the command twice a day.
![image](https://user-images.githubusercontent.com/101482368/160546625-6b4fec25-3b58-48ca-84a7-cc49347698c3.png)

##############################################
end
