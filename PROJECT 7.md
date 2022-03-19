# DEVOPS TOOLING WEBSITE SOLUTION
## In this project, I will be implementing a solution that consists of following components: AWS Infrastructure, RHEL webser, ubuntu DB server, RHEL NFS server, PHP and GITHUB as code repo
## Set up 3 web servers, 1 DB server and 1 NFS server that will be used in the project
![image](https://user-images.githubusercontent.com/101482368/159011273-c5159c75-b511-4703-8685-001dd88bd4d7.png)
## Attached 3 EBS volumes to the NFS server for partitioning
# configure a single partition on each of the volume
![image](https://user-images.githubusercontent.com/101482368/159012568-396c3e8b-8415-4ecb-9519-bcfc4c116ddc.png)
## used pvcreate t create physical volume on each of the disk (volume) to be used by the LVM and verified creation
![image](https://user-images.githubusercontent.com/101482368/159013351-266f598d-6b1b-459d-adc0-da1a590d738a.png)
## Used vgcreate utility to add all 3 PVs to a volume group (VG). Name the VG webdata-vg
## verified the entire setup 
![image](https://user-images.githubusercontent.com/101482368/159015590-f6242bfc-cf2b-4a9d-a54e-db0153c1d57e.png)
## Used mkfs.NFS to format the logical volumes with NFS filesystem
![image](https://user-images.githubusercontent.com/101482368/159017094-d505576e-7a85-4d7d-9076-2b968a8230c6.png)
## Created a mount directory /mnt and mounted the LV to used by the webserver and webser logs
![image](https://user-images.githubusercontent.com/101482368/159019785-2b05f962-92cc-41c2-9518-32db398542e3.png)
## I installed the NFS and it dependencies on the NFS SERVER and started the service
![image](https://user-images.githubusercontent.com/101482368/159022167-d8ad2085-01a1-484f-bbd5-2136fa04b87c.png)
## set up permission that will alow web servers connect to the NFS server and restarted the servic
![image](https://user-images.githubusercontent.com/101482368/159026467-bc791dcc-3d59-4bb8-9beb-b99dc3e8835c.png)
![image](https://user-images.githubusercontent.com/101482368/159027207-97d9923c-a179-4de6-9893-f65b5b60ea3e.png)
## Configured access to NFS for clients within the same subnet
![image](https://user-images.githubusercontent.com/101482368/159028208-139258c5-a402-4bc7-b698-32ec265163c1.png)
## Checked which port is used by NFS and opened it using Security Groups
![image](https://user-images.githubusercontent.com/101482368/159028611-329d55c4-8a18-4002-a155-c7bbf8095f3f.png)
## Opened TCP and UDP Port 111 and 2049 to allowing webser to be able to connect to the NFS server using web server subnet cidr 
![image](https://user-images.githubusercontent.com/101482368/159029939-3a21ecc8-6c58-4d40-8ec1-516eb45e4a88.png)
# TIME TO CONFIGURE THE DATABASE SERVER
## installed mysql-server on DB derver 
## Connected to the mysl 
## created Database tooling
## created user webaccess, granted user privileges to access tooling databse;
![image](https://user-images.githubusercontent.com/101482368/159030832-0d59c1fe-c775-4a53-9708-63be63e0256a.png)
# STEP Launched the 3 webserver and installed the NFS client on all of them
![image](https://user-images.githubusercontent.com/101482368/159107706-6792980e-e5f4-4a93-994f-c73e018cc232.png)
## Mounted /var/www/ and target the NFS server’s export for apps and verified that it mounted succesfully on all 3 web servers
![image](https://user-images.githubusercontent.com/101482368/159107878-f2406e5e-3f67-4dbf-b1da-ae8b19d718f6.png)
## Made sure that the changes will persist on Web Server after reboot.
![image](https://user-images.githubusercontent.com/101482368/159108068-8b082ac9-4fdc-4dac-baac-9aafe0ec52fd.png)
## Installed Remi’s repository, Apache and PHP
## Verified that Apache files and directories are available on the Web Server in /var/www and also on the NFS server in /mnt/apps.
![image](https://user-images.githubusercontent.com/101482368/159108516-1eaf3d7c-5d23-41a1-9b3a-100a88713352.png)
![image](https://user-images.githubusercontent.com/101482368/159108535-73c2864c-65f8-4364-a5d5-d348d8816da8.png)
![image](https://user-images.githubusercontent.com/101482368/159108553-88abb8d0-89d0-4663-8dc7-faff7509196b.png)
![image](https://user-images.githubusercontent.com/101482368/159108577-e38a761d-eecc-437a-ae99-f1c01aee8908.png)
## Mount /var/log/httpd and target the NFS server’s export for logs on the 3 web servers
![image](https://user-images.githubusercontent.com/101482368/159109448-a37a6932-d050-4c60-b775-b781f4b92e89.png)
## Fork the tooling source code from Darey.io Github Account
![image](https://user-images.githubusercontent.com/101482368/159109739-0114d64d-63f9-4724-b34c-d43455fd95fe.png)
## Deploy the tooling website’s code to the Webserver. Ensure that the html folder from the repository is deployed to /var/www/html
![image](https://user-images.githubusercontent.com/101482368/159110106-953a6db0-ea9b-4a44-a7d4-accde5f3eb35.png)
## opened TCP port 80 on the Web Server.
![image](https://user-images.githubusercontent.com/101482368/159110296-739e7a0e-eeaf-46d2-8489-1b451dd08eb0.png)
## 
![image](https://user-images.githubusercontent.com/101482368/159110500-6a5dd1af-904f-428a-8fac-91749a95ac41.png)
## Started appache and accessed webserver IP addr from the web browser
![image](https://user-images.githubusercontent.com/101482368/159110617-f75fa7ba-dffa-473c-9a7c-b42fbe9cb3f9.png)
![image](https://user-images.githubusercontent.com/101482368/159114148-36cb7f79-b49c-4d6d-bfc1-39be4a2ed7b8.png)
##logged into the browser with the username admin created in the user table in the databases
![image](https://user-images.githubusercontent.com/101482368/159113922-45c9b529-04b1-443e-8606-0d72b127ad7b.png)
####################################




