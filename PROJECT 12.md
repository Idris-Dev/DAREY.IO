# Ansible Refactoring & Static Assignments (Imports and Roles)
# Step 1 — Jenkins job enhancement
* On Jenkins-Ansible server I created a new directory called ansible-config-artifact - we will store there all artifacts after each build
* Change permissions to this directory, so Jenkins could save files there
![image](https://user-images.githubusercontent.com/101482368/161060654-b2a631a6-24ae-4c0b-bb88-77c158694e49.png)
![image](https://user-images.githubusercontent.com/101482368/161061678-44fac9d6-6d01-45c4-b51d-3d7ef19939b3.png)
* From Jenkins web console -> Manage Jenkins -> Manage Plugins -> on Available tab, searched for Copy Artifact and installed the plugin without restarting Jenkins.
![image](https://user-images.githubusercontent.com/101482368/161062479-4b0aa720-7eee-4710-b35c-787b94dcc0ac.png)
* Created a new Freestyle project and name it save_artifacts and configured it to be triggerred by the be triggered by completion of the existing ansible project
![image](https://user-images.githubusercontent.com/101482368/161063102-eff30162-4600-46b5-bc45-47d432b3a415.png)
* The main idea of save_artifacts project is to save artifacts into /home/ubuntu/ansible-config-artifact directory. To achieve this, create a Build step and choose Copy artifacts from other project, specify ansible as a source project and /home/ubuntu/ansible-config-artifact as a target directory.
* I tested my set up by making some changes in README.MD file inside my ansible-config-mgt repository (right inside master branch). both Jenkins Jobs were successful.
![image](https://user-images.githubusercontent.com/101482368/161065430-6838c589-f5af-43bb-bbd6-8dcc726f897f.png)
* The files appeared inside /home/ubuntu/ansible-config-artifact directory and it will be updated with every commit to your master branch.
![image](https://user-images.githubusercontent.com/101482368/161067011-da369b43-ef72-457b-9b58-134d89c52faa.png)
# Step 2 — Refactor Ansible code by importing other playbooks into site.yml
* I pulled the latest code from my master branch to a new branch before I started with the code refactoring.
* Refactoring is essential in organizing your codes and playbooks in an environment where you have several servers with different requirements, OS , code changes, troubleshooting. Refactoring is simply a technique used to reduce complexity, enhance code readability, increase maintainability and extensibility and add proper comments without affecting the logic.
* It also means making changes to the source code without changing expected behaviour of the software.
* I created a new file and named it site.yml - This file will now be considered as an entry point into the entire infrastructure configuration. Other playbooks will be included here as a reference. In other words, site.yml will become a parent to all other playbooks that will be developed.
* I Created a new folder in root of the repository and named it static-assignments. The static-assignments folder is where all other children playbooks will be stored. This is merely for easy organization of your work.
* Then moved common.yml file into the newly created static-assignments folder.
* Inside site.yml file, I imported common.yml playbook. The screenshot of the above implementation is shown below:
![image](https://user-images.githubusercontent.com/101482368/161083325-da21a114-0137-44e9-9619-bee8ebd0d9dc.png)
* The code above uses built in import_playbook Ansible module.
* Run ansible-playbook command against the dev environment Here, I will apply some tasks to my dev servers, as wireshark is already installed on them, another playbook called common-del.yml will be created under static-assignments to delete the wireshark utility on these servers.
* I updated the site.yml with - import_playbook: ../static-assignments/common-del.yml.
![image](https://user-images.githubusercontent.com/101482368/161085681-3b7e984b-ca4a-44d5-9324-ace929c104e7.png)
![image](https://user-images.githubusercontent.com/101482368/161087539-b513d340-00d2-4bf8-a32e-f7c6b77ee149.png)
* I commited and pushed to github, it was successful as seen below:
* Also successfully copied to our new artifacts diectory:
![image](https://user-images.githubusercontent.com/101482368/161108832-0baab931-aee9-4167-acad-16a5c8115311.png)
* I ran the playbook against dev servers:
![image](https://user-images.githubusercontent.com/101482368/161116411-b0543868-df1e-4fef-9016-1cdfde286f94.png)
* Below shows output from some of the servers with wireshark uninstalled:
![image](https://user-images.githubusercontent.com/101482368/161116655-16547b17-7d8b-4940-8637-048774265b98.png)
![image](https://user-images.githubusercontent.com/101482368/161116960-fefc5e2f-21d3-420e-a34c-1987f7b65b8d.png)
## `Such a great learning on how to use import_playbooks module.
# Step 3 — Configure UAT Webservers with a role ‘Webserver’
* Configured two (2) new Web servers (RHEL 8 servers) as uat.
* created a directory called roles in the /etc/ansible directory using the ansible-galaxy utility
* ![image](https://user-images.githubusercontent.com/101482368/161119234-a5411cc2-499f-4c6a-8cf4-21e0072aaa59.png)
* I updated my inventory ansible-config-mgt/inventory/uat.yml file with IP addresses of my 2 new UAT Web servers.
![image](https://user-images.githubusercontent.com/101482368/161117667-07f37982-ef13-4dd9-850f-1981d7bc8133.png)
n /etc/ansible/ansible.cfg file, I uncommented roles_path string so Ansible could know where to find configured roles.
![image](https://user-images.githubusercontent.com/101482368/161119734-18abcc85-6ca6-4fb9-ad82-cf48e78d70e8.png)
*I started adding some logic to the webserver role. Inside tasks directory, and within the main.yml file, 
* I added some configuration tasks as shown below in the screenshot
* The tasks will implement the following:
- Install and configure Apache (httpd service).
- Clone Tooling website from GitHub https://github.com/your-name>/tooling.git.
- Ensure the tooling website code is deployed to /var/www/html on each of 2 UAT Web servers.
- Make sure httpd service is started
![image](https://user-images.githubusercontent.com/101482368/161120720-bb684d50-aa8b-43ba-a271-4b4205b56801.png)
# Step 4 — Reference ‘Webserver’ role
* Within the static-assignments folder, I created a new assignment for uat-webservers uat-webservers.yml. This is where I will reference the role (role webserver).
* Since site.yml is the entry point to our configuration, we need to reference our uat-webservers.yml role inside site.yml
![image](https://user-images.githubusercontent.com/101482368/161135063-93f2267e-1263-4ef9-a8d5-18f5969de414.png)
![image](https://user-images.githubusercontent.com/101482368/161127372-cfb51fe1-0601-46e5-9914-8e70dd1b5de7.png)
# Step 5 – Commit & Test
* I committed my changes, created a Pull Request and merged them to master branch.
* ![image](https://user-images.githubusercontent.com/101482368/161138782-1f965473-a01d-4c30-b859-be38ada5a71e.png)
* Roles folder was created manaually in the /etc/ansible directory 
 ![image](https://user-images.githubusercontent.com/101482368/161139545-bcd220fd-b08b-424f-9b93-fdbfabba0b06.png)
* I ran the playbook against your uat inventory and the output was sucessful
![image](https://user-images.githubusercontent.com/101482368/161144127-01872a98-906a-4db1-b327-20b9a7ed75e6.png)
* Checked to verify that apache and git were successfully installed on both UAT webservers
![image](https://user-images.githubusercontent.com/101482368/161144913-e159e53a-86f4-4e4c-940f-1b26b3f3bdb0.png)
![image](https://user-images.githubusercontent.com/101482368/161145058-95de4951-9cbe-4b3b-b3bf-8817695db9b4.png)
* My UAT Web servers are now configured and I can reach them from my browser:
![image](https://user-images.githubusercontent.com/101482368/161146621-69b11ec3-c550-432f-8504-82a00f177afe.png)
![image](https://user-images.githubusercontent.com/101482368/161146765-bdf8e828-db68-410c-9e27-8ff2a7ed4134.png)
################
* During the course of this i ran into a few hiccups with git and merging my sub branch with the main branch.but i manged to figure it out after watching video tutorial on github
####
## i am glad to say i have learnt how to deploy and configure UAT Web Servers using Ansible imports and roles!. this was packed 















