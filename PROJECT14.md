# Experience Continuous Integration with Jenkins | Ansible | Artifactory | SonarQube | PHP
This project is partly a continuation of the Ansible work from previous projects. It will require a lot of servers to simulate all the different environments from dev/ci all the way to production.

## SIMULATING A TYPICAL CI/CD PIPELINE FOR A PHP BASED APPLICATION
As part of the ongoing infrastructure development with Ansible started from Project 11, you will be tasked to create a pipeline that simulates continuous integration and delivery

Target end to end CI/CD pipeline is represented by the diagram below. 
![image](https://user-images.githubusercontent.com/101482368/162239085-f5ac2c25-3cb4-4e63-b0b7-fcf4409360d5.png)


Servers are going to be created based on the current environment that is being worked on.

The initial focus in this project will be on these three environments:
* CI
* Dev
* Pentest

What we want to achieve, is having Nginx to serve as a reverse proxy for our sites and tools. Each environment setup is represented in the below table and diagrams.
![image](https://user-images.githubusercontent.com/101482368/162241921-d45b0038-2d67-4a11-963e-f2bc104d6d42.png)
![image](https://user-images.githubusercontent.com/101482368/162242123-0f795dda-dd35-4fea-b74d-4b71eb5fa989.png)

Other Environments from Lower To Higher
![image](https://user-images.githubusercontent.com/101482368/162242701-793773ff-a0b3-422f-8c4b-15d0e6a8e6bb.png)

DNS requirements

Make DNS entries to create a subdomain for each environment. Assuming your main domain is idris.com. you would have a subdomain for Jenkins like this:https://ci.infradev.idris.com and so on for other environments

Ansible Inventory should look like this,
