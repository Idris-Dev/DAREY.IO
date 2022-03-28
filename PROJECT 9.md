# CONTINOUS INTEGRATION PIPELINE FOR TOOLING WEBSITE
# Tooling website deployment automation with continuous integration. with Jenkins
## Step 1: INSTALL AND CONFIGURE JENKINS SERVER
## Installed JDK (since Jenkins is a Java-based application) with "sudo apt install default-jdk-headless"
## Verified that jenkins is also running
![image](https://user-images.githubusercontent.com/101482368/160409394-d70ef732-eeef-4da8-928c-f9feee489d24.png)
## Opened port 8080 in jenkins server security group to allow incoming traffic 
![image](https://user-images.githubusercontent.com/101482368/160409746-950cf3bf-7d46-447e-8aee-ba3878f58e3f.png)
## Performed initial jenkins set up from the browser
![image](https://user-images.githubusercontent.com/101482368/160410544-c846ace3-b2a8-4197-9d27-17fb418b9fe4.png)
## Installed suggested plugins and Created an Admin user
![image](https://user-images.githubusercontent.com/101482368/160411332-295b9dbe-52eb-4f85-97f6-c8ba2b442eba.png)
![image](https://user-images.githubusercontent.com/101482368/160411603-a706dbce-1b67-4744-a118-3496931ee59a.png)
## Step 2 – Configured Jenkins to retrieve source codes from GitHub using Webhooks
## Enabled webhooks in your GitHub repository settings
![image](https://user-images.githubusercontent.com/101482368/160412943-4c45ae29-65c0-49b8-8c79-ac85306732d8.png)
## Created a freestyle project in the Jenkins webconsole
![image](https://user-images.githubusercontent.com/101482368/160413635-19ac52d5-45fd-475c-a10c-5046f1c5c7f9.png)
## Connected Jenkins with Github repository
![image](https://user-images.githubusercontent.com/101482368/160416035-b7d0c5a0-69a0-445c-bc4f-13c70d50cca6.png)
## web console output
![image](https://user-images.githubusercontent.com/101482368/160416405-88118831-2986-43f4-a4b4-7192752e39e9.png)
## Configured triggering the job from GitHub webhook:
## Configure build triggers and post build actions
![image](https://user-images.githubusercontent.com/101482368/160417906-72de7fa0-d142-4a23-9e6a-69f98a3fa44e.png)
## build #1
![image](https://user-images.githubusercontent.com/101482368/160458601-88c8ba13-32e9-40ba-abe6-9db2e15b6474.png)
## 2ND BUILD runs automatically after configuring webhook build triggers
![image](https://user-images.githubusercontent.com/101482368/160465325-d645145f-230f-48d0-ad94-8e2b9aa6ff28.png)
# STEP 3: CONFIGURE JENKINS TO COPY FILES TO NFS SERVER VIA SSH
## Installed "Publish Over SSH " Plug-in that will be used to copy artifacts from Jenkins local server storage to NFS Server
![image](https://user-images.githubusercontent.com/101482368/160468058-ee646c59-ec25-478d-8b41-b95dc409e5ae.png)
## Configured the job/project to copy artifacts over to NFS server.
![image](https://user-images.githubusercontent.com/101482368/160473334-efe72d9a-4955-4704-9a07-91b2ae3c6c22.png)
## configured to send all files into our remote directory by adding "post build actions" with source being ** all
![image](https://user-images.githubusercontent.com/101482368/160474550-0aa9020d-f0b0-435d-92ef-ea032efc8da3.png)
## Successfully configured Jenkins to SSH into NFS server 
![image](https://user-images.githubusercontent.com/101482368/160478580-4400cdae-0851-4e06-ac5c-8625d489eefa.png)
![image](https://user-images.githubusercontent.com/101482368/160478695-c08a8814-4205-4139-8fbc-e2829c9bf0b0.png)
## Verified that the README.md file in the /mnt/apps in NFS server is updated
![image](https://user-images.githubusercontent.com/101482368/160479108-1ff216af-d28c-48a8-a1ac-c905cb0a27c0.png)

#######################
END


