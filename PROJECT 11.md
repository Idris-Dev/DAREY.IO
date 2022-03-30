# ANSIBLE AUTOMATION OF PROJECT 7 TO 10
## INSTALLED AND CONFIGURED ANSIBLE ON EC2 INSTANCE
![image](https://user-images.githubusercontent.com/101482368/160671263-827c9d29-bc01-40d4-902f-fc14972df07b.png)
## Created a new repo in github
![image](https://user-images.githubusercontent.com/101482368/160671728-9b1948d5-7d95-48d6-8d08-eef9f84d1976.png)
## Created a new freestyle project in Jenkins to be linked to github to store file and changes made to github repo
![image](https://user-images.githubusercontent.com/101482368/160672088-116b1ab0-b025-4358-aabf-bb49434f89e6.png)
![image](https://user-images.githubusercontent.com/101482368/160672662-5f4ef847-6d61-45b5-897e-26d1af2a4930.png)
## Made changes to README.md in github and verified in console output
![image](https://user-images.githubusercontent.com/101482368/160672980-62bcfa30-92c5-4d3f-8459-c416829df9e3.png)
## Configured auto build in jenkins
![image](https://user-images.githubusercontent.com/101482368/160673083-ba84fa76-b4b2-4391-87cc-df180042ab4a.png)
![image](https://user-images.githubusercontent.com/101482368/160673375-f0587edc-9221-4ed7-9c80-a6f7fe0514f0.png)
## Tested setup in the terminal 
![image](https://user-images.githubusercontent.com/101482368/160673659-2b16bcef-c671-44cb-a4b5-9ad7864cb605.png)
## Architecture at this point looks like this 
![image](https://user-images.githubusercontent.com/101482368/160673751-5dc40eee-6124-46b2-993f-b35eed49ba47.png)
## Step 2 – Prepared  development environment using Visual Studio Code
## configured VSC to connect to your newly created GitHub repository.
![image](https://user-images.githubusercontent.com/101482368/160674641-49d873df-f932-4540-be62-307a06beeb75.png)
# ANSIBLE DEVELOPMENT
## Created a new branch 
![image](https://user-images.githubusercontent.com/101482368/160682572-f324bdc7-5889-4f4c-8b3a-82dca637b4e2.png)
![image](https://user-images.githubusercontent.com/101482368/160682682-f85fb5ec-9359-4387-8b45-24bdf083c634.png)
## Created playbbok and inventory folder to store playbok files and keep hosts organized
![image](https://user-images.githubusercontent.com/101482368/160684077-7e4da8dc-f937-4ce9-aa5a-71fbd4e652df.png)
## created playbook file in the playbooks folder and created dev, staging, uat and prod file in the inventory folder
![image](https://user-images.githubusercontent.com/101482368/160685637-c9b35bbe-91b0-45ca-b101-78f42af014b9.png)
## Step 4 – Set up an Ansible Inventory
## added SSH agent and private key to be able to SSH into the remote jenk-ansible server
![image](https://user-images.githubusercontent.com/101482368/160690519-96d3f4aa-1501-4b6e-94b3-675520f0b14e.png)
## SSHed in the Jenkins server
![image](https://user-images.githubusercontent.com/101482368/160697470-654b0f57-5c41-4a10-9e90-e8429ca8e0d9.png)
## Configured inventory/dev folder with the private address ip of other servers to be SSHed into
![image](https://user-images.githubusercontent.com/101482368/160699271-4257e276-cd8b-4f18-ae14-fa2723a45676.png)
# Step 5 – Created a Common Playbook
## Updated your playbooks/common.yml file with following code:
![image](https://user-images.githubusercontent.com/101482368/160699932-34a8a9bc-0884-4f3e-8c77-d267e04611e3.png)
## Push the chnages in the branch created to Github
![image](https://user-images.githubusercontent.com/101482368/160701818-d9ec117c-20bf-4e89-afb6-2c43abea5d03.png)
![image](https://user-images.githubusercontent.com/101482368/160711974-fd6c93ef-2e56-4f50-89ab-f2a4f80d0605.png)
![image](https://user-images.githubusercontent.com/101482368/160711857-326a0fec-7549-4ce1-a5a0-f85edb383f10.png)
## Jenkins saves all the files and changes
![image](https://user-images.githubusercontent.com/101482368/160712374-15342004-bfe7-476c-ab68-003fa84dec26.png)
## files appear in the Jenskin-Ansible server
![image](https://user-images.githubusercontent.com/101482368/160712811-93acf20b-d8ea-4366-a5a7-a99a9c147f80.png)
![image](https://user-images.githubusercontent.com/101482368/160712930-994748bb-1633-4ec5-ba26-79ccfa529ed5.png)
## Checked out of the terminal and the feature branch and main branch are up to date
![image](https://user-images.githubusercontent.com/101482368/160713622-a6195b57-ea02-4325-bc9e-5a4582b93d89.png)
# Ran the first Ansible test
## executed ansible-playbook
![image](https://user-images.githubusercontent.com/101482368/160746543-31bfc449-3ab2-4f74-80e8-1a803fb8f6e6.png)
## Verified wireshark installation on all the servers
![image](https://user-images.githubusercontent.com/101482368/160746845-061f46c8-7636-4efc-af8e-5aed570bf6b6.png)
![image](https://user-images.githubusercontent.com/101482368/160746870-cf804485-68ad-4bf0-89ba-04611ff0381f.png)
![image](https://user-images.githubusercontent.com/101482368/160746953-d891b347-1a16-4e63-8336-9936429b7886.png)
![image](https://user-images.githubusercontent.com/101482368/160746989-dae02d39-3087-4007-8438-886ca48d5a2e.png)
![image](https://user-images.githubusercontent.com/101482368/160747066-eaf8578f-9abb-480e-98f9-43a300f24e05.png)
## Updated architecture with jenkins auntomation and ansible playbook implementation looks like this
![image](https://user-images.githubusercontent.com/101482368/160747393-55b4eaed-62f0-4e93-9a12-920c08dd5a26.png)

######################################
END












