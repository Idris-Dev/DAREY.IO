# WEB SOLUTION WITH WORDPRESS ( THREE TIER ARCHITECTURE )
## Launched a Redhat linux server (ec2 instance on AWS ) that will serve as Web server and created 3 additional volumes to be attached to the instance in the same AZ
![image](https://user-images.githubusercontent.com/101482368/158858344-8903cdab-9f18-4bcc-a5d3-d0556656c29d.png)
## Created and attached 3 volumes to the instance created
![image](https://user-images.githubusercontent.com/101482368/158859096-a5a01f8d-1d20-4ee0-8019-43ba24406c16.png)
## opened server and viewed the 3 volumes created and attached to the server
![image](https://user-images.githubusercontent.com/101482368/158861511-e11ea8af-b34f-4e7d-aad5-aa5061b35b2e.png)
## used gdisk utility to create a single partition in each of the volume
![image](https://user-images.githubusercontent.com/101482368/158862105-37771a53-0f64-411d-8706-54a81c452f3f.png)
## Created a partition in each of the disk
![image](https://user-images.githubusercontent.com/101482368/158873255-ec2d83e8-040a-4fb1-9081-ca3e3812f620.png)
## Installed lvm2 package using sudo yum install lvm2. Run sudo lvmdiskscan command to check for available partitions.
![image](https://user-images.githubusercontent.com/101482368/158874035-a0185df0-edb0-4c6a-87e3-d66e627b539e.png)
## Used pvcreate utility to mark each of 3 disks as physical volumes (PVs) to be used by LVM and ran sudo pvs to verify
![image](https://user-images.githubusercontent.com/101482368/158874841-b0601982-7073-4c1d-a022-951e57a1d2ee.png)
## added all 3 PVs to a volume group (VG). Named the VG webdata-vg, verfied that it was created,
## Use lvcreate utility to create 2 logical volumes. apps-lv (Use half of the PV size), and logs-lv Use the remaining space of the PV size
![image](https://user-images.githubusercontent.com/101482368/158875735-720951d4-1e04-4ce0-bf74-ebb9e0391656.png)
## Verified the entire setup  sudo vgdisplay -v #view complete setup - VG, PV, and LV
## sudo lsblk
![image](https://user-images.githubusercontent.com/101482368/158877968-71dd98d9-4bff-4c2c-b269-d4bfd494746f.png)
## Used mkfs.ext4 to format the logical volumes with ext4 filesystem
## Created /var/www/html directory to store website files
## Created /home/recovery/logs to store backup of log data
## Mounted /var/www/html on apps-lv logical volume
![image](https://user-images.githubusercontent.com/101482368/158878915-3e694038-eb08-4b1b-84a1-0e951a42ef13.png)
## Used rsync utility "sudo rsync -av /var/log/. /home/recovery/logs/ "to backup all the files in the log directory /var/log into /home/recovery/logs (This is required before mounting the file system)
## Mount /var/log on logs-lv logical volume. (Note that all the existing data on /var/log will be deleted. 
## Restored log files back into /var/log directory
![image](https://user-images.githubusercontent.com/101482368/158880060-26b6e228-6785-4e2b-ac88-361bc3b9018c.png)
Updated /etc/fstab file using the UIID of the device so that the mount configuration will persist after restart of the server.
![image](https://user-images.githubusercontent.com/101482368/158881510-5829d578-5912-4325-8567-05b3846e9bc9.png)
## Tested the configuration and reloaded the daemon
## Verified the setup by running df -h
![image](https://user-images.githubusercontent.com/101482368/158881995-6776ab72-59d9-4625-82e4-0b8aead10f88.png)
# Creating Database Sever using Redhat Linux server (ec2)
Created a   Database server and atached 3 volumes
![image](https://user-images.githubusercontent.com/101482368/158884028-5e7ae3c6-eefc-465b-b32f-22d4a2e78334.png)
## used gdisk utility to create partition in each of the volume in the db server
![image](https://user-images.githubusercontent.com/101482368/158885330-753419ce-7242-4eef-b408-e225ff4ee501.png)
##  Installed lvm2 package using sudo yum install lvm2. Run sudo lvmdiskscan command to check for available partitions.
![image](https://user-images.githubusercontent.com/101482368/158886118-10bd3dea-0513-4510-84fa-5d97baecef0a.png)
## Used pvcreate utility to mark each of 3 disks as physical volumes (PVs) to be used by LVM and ran sudo pvs to verify
![image](https://user-images.githubusercontent.com/101482368/158886593-08d4ace5-4d79-4ce5-90ec-56440e09b293.png)
## added all 3 PVs to a volume group (VG). Named the VG webdata-vg, verfied that it was created,
## Use lvcreate utility to create 2 logical volumes. db-lv (Use half of the PV size), and logs-lv Use the remaining space of the PV size
## verify that Logical Volume has been created successfully by running sudo lvs
![image](https://user-images.githubusercontent.com/101482368/158887527-7fb462fa-596e-4b55-b6f3-7112473f7c8a.png)
## Verified the entire setup with sudo lsblk
![image](https://user-images.githubusercontent.com/101482368/158888002-2de39245-b468-4a89-b6d1-4746c2cd3815.png)
## Used mkfs.ext4 to format the logical volumes with ext4 filesystem
## Created /db directory to store db files
## Created /home/recovery/logs to store backup of log data
## Mounted /db on db-lv logical volume
![image](https://user-images.githubusercontent.com/101482368/158888966-dadc5e24-ff65-4771-933e-e5cd6bedf87a.png)
## Used rsync utility "sudo rsync -av /var/log/. /home/recovery/logs/ "to backup all the files in the log directory /var/log into /home/recovery/logs (This is required before mounting the file system)
## Mounted /var/log on logs-lv logical volume
![image](https://user-images.githubusercontent.com/101482368/158889749-4cb066ed-d613-420c-9a2f-a254c7ceb958.png)
## Restore log files back into /var/log directory
## Updated /etc/fstab file so that the mount configuration will persist after restart of the server.
![image](https://user-images.githubusercontent.com/101482368/158890570-796a74a4-b1f1-45a7-a2a4-e19a4af79ff3.png)
## Tested the configuration and reloaded the daemon
## Verified the setup by running df -h
![image](https://user-images.githubusercontent.com/101482368/158890933-c3c0ae56-0b7b-493d-bb78-15d3a12de930.png)
# Step 3 — Install WordPress on your Web Server EC2
## update server and installed wget, apache and its dependencies
![image](https://user-images.githubusercontent.com/101482368/158892348-b6c32ede-8f16-4a24-bc0c-47a0e49f89fd.png)
## Installed PHP and its dependencies and restarted Apache
![image](https://user-images.githubusercontent.com/101482368/158894553-482b5940-3c69-47d5-8676-28272dda3bb7.png)
## Downloaded wordpress and copied wordpress to var/www/html
![image](https://user-images.githubusercontent.com/101482368/158895276-a1818c88-efd5-46d1-ac08-1f49115340d3.png)
## Configured SELinux Policies
![image](https://user-images.githubusercontent.com/101482368/158895486-7a580b31-343a-46b1-8db8-5010b156ef4b.png)
# Step 4 — Install MySQL on your DB Server EC2
![image](https://user-images.githubusercontent.com/101482368/158897148-6fdfa5b1-cfec-4d37-b838-794a03fc3f87.png)
# Step 5 — Configured DB to work with WordPress
![image](https://user-images.githubusercontent.com/101482368/158897768-0a1bfa33-5a88-4f0a-9bcc-39a6ce44f168.png)
## Step 6 — Configure WordPress to connect to remote database
## opened SG port 3306 to allow traffic from wordpress server
![image](https://user-images.githubusercontent.com/101482368/158898064-3e10b049-802e-4d59-a849-bd1a227fa8b7.png)
## installed mysql-client on the wordpress server to be able to connect to the DB server
![image](https://user-images.githubusercontent.com/101482368/158898404-bc85f393-03d5-44a0-aa86-1e12b61d2b96.png)
## connected to the database and ran show databases; command 
![image](https://user-images.githubusercontent.com/101482368/158901228-5a689959-2dc7-45bb-8fad-6522ba2f39b3.png)



