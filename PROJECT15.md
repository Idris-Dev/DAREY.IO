# AWS CLOUD SOLUTION FOR 2 COMPANY WEBSITES USING A REVERSE PROXY TECHNOLOGY
The goal of this project is to build a secure infrastructure inside the AWS VPC network for idris.com which uses WordPress CMS for its main business website, and a Tooling Website https://github.com/Idris-Dev/tooling for the DevOps team. As part of the company’s desire for improved security and performance, a decision has been made to use a reverse proxy technology from NGINX to achieve this.

The major requirements for this project are cost, security and scalability.  Hence, implementing the architecture designed below, we have to ensure that infrastructure for both websites, WordPress and Tooling, is resilient to Web Server’s failures, can accomodate to increased traffic and, at the same time, has reasonable cost.
![image](https://user-images.githubusercontent.com/101482368/162261930-596a95f1-410d-4a03-92c2-89067562db9d.png)

Prior to starting this AWS Cloud Project, the following requirements were fulfilled;
* I create an AWS Master account. (Also known as Root Account)
* Within the Root account, I created a sub-account and named it DevOps.
* Within the Root account, I also created an AWS Organization Unit (OU named it Dev. where we will launch Dev resources
* Moved the DevOps account into the Dev OU.
![image](https://user-images.githubusercontent.com/101482368/162281456-61d80163-256b-4e43-82af-f1381e7280e4.png)
* Logged-in to the newly created AWS account using the new email address.
* I created a domain name www.idrisu.com 
![image](https://user-images.githubusercontent.com/101482368/162282527-5baa140c-0bee-425f-9dbe-93c4144a21c1.png)
* Created a hosted zone in AWS, and mapped it to www.idrisu.com
![image](https://user-images.githubusercontent.com/101482368/162283588-b6388b8c-bb7b-4ca0-af2f-fdc774359ce1.png)

# SETTING UP A VIRTUAL PRIVATE NETWORK (VPC)
Create a VPC with 2 public subnets and $ private subnets as shown in the architecture
![image](https://user-images.githubusercontent.com/101482368/162291078-d8b7cb33-2bcc-4068-938c-588ce7a70311.png)
![image](https://user-images.githubusercontent.com/101482368/162291855-cbff0ed6-1c8b-40e7-b973-91e2006a4566.png)
![image](https://user-images.githubusercontent.com/101482368/162296301-545d1627-b66b-4dc8-9276-dab328bd6b14.png)
Edited a route in public route table, and associate it with the Internet Gateway. (This is what allows a public subnet to be accisble from the Internet)
![image](https://user-images.githubusercontent.com/101482368/162302483-4ec64d60-8808-456a-ba61-9c65435978ce.png)
![image](https://user-images.githubusercontent.com/101482368/162304454-1e8092c7-8a0d-4385-8de4-c79460242a2e.png)
Create a Nat Gateway and assign one of the Elastic IPs (*The other 2 will be used by Bastion hosts)
![image](https://user-images.githubusercontent.com/101482368/162307894-d9b58893-8504-43fd-89f4-f7f87b111b5c.png)
![image](https://user-images.githubusercontent.com/101482368/162310618-e1d48892-e013-4052-a3ee-53b125e1d6ee.png)

Created a SecurityGroup for:
* Nginx Servers: Access to Nginx should only be allowed from a Application Load balancer (ALB). At this point, I have not created a load balancer, therefore I will update the rules later.
* Bastion Servers: Access to the Bastion servers should be allowed only from workstations that need to SSH into the bastion servers. Hence, you can use your workstation public IP address
* Application Load Balancer: ALB will be available from the Internet
* Webservers: Access to Webservers should only be allowed from the Nginx servers. Since we do not have the servers created yet, just put some dummy records as a place holder, we will update it later.
* Data Layer: Access to the Data layer, which is comprised of Amazon Relational Database Service (RDS) and Amazon Elastic File System (EFS) must be carefully desinged – only webservers should be able to connect to RDS, while Nginx and Webservers will have access to EFS Mountpoint.
![image](https://user-images.githubusercontent.com/101482368/162325087-72a51246-ac5a-478b-8fb0-3d76e633cdf4.png)

Proceeded to set up compute resources inside the VPC which include;
* EC2 Instances
* Launch Templates
* Target Groups
* Autoscaling Groups
* TLS Certificates
* Application Load Balancers (ALB)

## Compute Resources for Nginx
Provisioned EC2 Instances for Nginx in 2 AZs in the N.Virginia region.

Launch 3 EC2 instances (Red Hat Free Tier) with default settings and a security group that allows access from all traffic (0.0.0.0/0)
![image](https://user-images.githubusercontent.com/101482368/162340570-3a8ee9bf-3d07-43fb-8665-f4173e4f78b7.png)

Set up the Nginx server for AMI installation:
* yum install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
* yum install -y dnf-utils http://rpms.remirepo.net/enterprise/remi-release-8.rpm
* yum install wget vim python3 telnet htop git mysql net-tools chrony -y
* systemctl start chronyd
* systemctl enable chronyd

Configure Selinux policies with the following. These policies are required for the webserver to function properly:
* setsebool -P httpd_can_network_connect=1
* setsebool -P httpd_can_network_connect_db=1
* setsebool -P httpd_execmem=1
* setsebool -P httpd_use_nfs 1  

Install amazon EFS utils for mounting the target on the Elastic file system:
* git clone https://github.com/aws/efs-utils
* cd efs-utils
* yum install -y make
* yum install -y rpm-build
* make rpm 
* yum install -y  ./build/amazon-efs-utils*rpm

Install self-signed certificate for Nginx instance:
* sudo mkdir /etc/ssl/private
* sudo chmod 700 /etc/ssl/private
* openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/ACS.key -out /etc/ssl/certs/ACS.crt
* sudo openssl dhparam -out /etc/ssl/certs/dhparam.pem 2048

Create an AMI out of the EC2 instance
![image](https://user-images.githubusercontent.com/101482368/162347954-88d13e97-7b4b-4075-a53e-bc20b77f584c.png)

Configure Target Groups
![image](https://user-images.githubusercontent.com/101482368/162347846-ee039e8d-ac78-4363-8199-8fa96826668a.png)

Configure Autoscaling For Nginx
![image](https://user-images.githubusercontent.com/101482368/162349884-d8017b74-ded2-49de-a793-3576091fb64a.png)

Repeated the process for Bastion and Webserver

Launch Templates
![image](https://user-images.githubusercontent.com/101482368/162351841-78d32c01-885d-4923-8bde-d46b5f2c78bb.png)

Target groups 
![image](https://user-images.githubusercontent.com/101482368/162351020-b15f3835-d5af-4b8d-847b-1b709c82b644.png)

Autoscaling Group
![image](https://user-images.githubusercontent.com/101482368/162352400-3bb0ca6d-f5b4-4381-8146-02127f1e1342.png)

## TLS Certificates From Amazon Certificate Manager (ACM
TLS certificates is needed to handle secured connectivity to your Application Load Balancers (ALB).
![image](https://user-images.githubusercontent.com/101482368/162364739-3e3dd257-bc43-4e31-9a24-30126d7d2bee.png)

## CONFIGURE APPLICATION LOAD BALANCER (ALB)
Internet facing Application Load Balancer is created To Route Traffic To NGINX
Nginx EC2 Instances will have configurations that accepts incoming traffic only from Load Balancers. No request should go directly to Nginx servers. With this kind of setup, we will benefit from intelligent routing of requests from the ALB to Nginx servers across the 2 Availability Zones. We will also be able to offload SSL/TLS certificates on the ALB instead of Nginx. Therefore, Nginx will be able to perform faster since it will not require extra compute resources to valifate certificates for every request.
![image](https://user-images.githubusercontent.com/101482368/162369273-b01f5ad0-ad22-46ef-bd68-ef7b55cf3a3b.png)

Setup EFS
This project utilizes EFS service and mount filesystems on the Nginx and Webservers to store dat
* Created an EFS filesystem
* Created an EFS mount target per AZ in the VPC, associate it with both subnets dedicated for data layer
* Associated the Security groups created earlier for data layer.
* Created an EFS access point. (Give it a name and leave all other settings as default)
![image](https://user-images.githubusercontent.com/101482368/162369987-a267596b-5498-4912-b09a-64d5adcc6ec0.png)
![image](https://user-images.githubusercontent.com/101482368/162370052-86f545d6-65cc-4768-899d-1414f57ccee6.png)

## Setup RDS
* On KMS Console, choose Symmetric and Click Next. Assign an Alias.
* Select user with admin privileges as the key administrator
* Click Create Key
![image](https://user-images.githubusercontent.com/101482368/162370880-a6fc37ca-a272-47a9-b70d-a99a56e9a21f.png)
To ensure that yout databases are highly available and also have failover support in case one availability zone fails, we will configure a multi-AZ set up of RDS MySQL database instance. In our case, since we are only using 2 AZs, we can only failover to one

## DB Subnet Group
On the RDS Management Console, created a DB subnet group with the two private subnets(10.0.5.0/24 and 10.0.7.0/24) in the two Availability Zones.
![image](https://user-images.githubusercontent.com/101482368/162372175-e2fa4399-2237-46d8-8d71-d055fa5294b6.png)
* Create an RDS Instance for mysql 8.*.*
* Select the VPC, select the subnet group that was created earlier and the database security group
* Configured VPC and security (ensure the database is not available from the Internet)
* Configure backups and retention
* Encrypted the database using the KMS key created earlier
* Enabled CloudWatch monitoring and export Error and Slow Query logs (for production, also include Audit)
![image](https://user-images.githubusercontent.com/101482368/162373480-8a771c16-884d-4f33-a0c5-e44d93d63709.png)

## Configuring DNS with Route53
We need to ensure that the main domain for the WordPress website can be reached, and the subdomain for Tooling website can also be reached using a browser.

Created other records such as CNAME, alias and A records.
NOTE that we can use either CNAME or alias records to achieve the same thing. But alias record has better functionality because it is a faster to resolve DNS record, and can coexist with other records on that name.
i had create an alias record for the root domain and direct its traffic to the ALB DNS name.
Then created an alias record for tooling.<yourdomain>.com and direct its traffic to the ALB DNS name.
  ![image](https://user-images.githubusercontent.com/101482368/162377269-f4f8a0c8-e143-4082-935f-48b9911ce25a.png)

  I have just created a secured, scalable and cost-effective infrastructure to host 2 enterprise websites using various Cloud services from AWS. At this point, your infrastructure is ready to host real websites’ load.

  ###################
