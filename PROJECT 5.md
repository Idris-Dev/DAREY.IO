# Client/Server Architecture Using A MySQL Relational Database Management System
## IMPLEMENT A CLIENT SERVER ARCHITECTURE USING MYSQL DATABASE MANAGEMENT SYSTEM (DBMS)
## Created and configured two Linux-based virtual servers (EC2 instances in AWS).
![image](https://user-images.githubusercontent.com/101482368/158712284-5be5dd1f-6d2d-4f4f-a1ac-a8d0da6bd9ed.png)
## On mysql server Linux Server I installed MySQL Server software
![image](https://user-images.githubusercontent.com/101482368/158713259-3975d00f-56e0-4b95-82f6-3740ddf1e8f0.png)
## On mysql client  Linux Server I installed MySQL Client software
![image](https://user-images.githubusercontent.com/101482368/158713374-7b03b8e8-52e5-42d0-879b-a6fdfca4b0aa.png)
## Opened port 3306 in the security group inbound rule to allow db traffic to he mysql server
![image](https://user-images.githubusercontent.com/101482368/158712734-ff571713-8f13-45e0-a0bd-805a46957298.png)
## Configured Mysql server to allow connection from remote server
![image](https://user-images.githubusercontent.com/101482368/158713660-abf11a3d-49d9-4984-b8f0-4713c3246a78.png)
## Ran secure installation cmd for mysql sudo mysql_secure_installation and configred 
![image](https://user-images.githubusercontent.com/101482368/158714813-dbad2815-d915-410c-9ffd-9b23a571a9aa.png)
## Connected and created User in mysql
![image](https://user-images.githubusercontent.com/101482368/158715313-ecf054f8-91f8-4f7f-951a-1252eaaea98e.png)
Created database (idris_db)  and granted privileg to user to access the db
![image](https://user-images.githubusercontent.com/101482368/158715872-74682b70-a858-47ed-9d3b-0db34b767fd0.png)
## Restarted mysql with sudo systemctl restart mysql
## connected to the Mysql server from client server
![image](https://user-images.githubusercontent.com/101482368/158715872-74682b70-a858-47ed-9d3b-0db34b767fd0.png)
## Connected to the mysql server from the client server and ran command to show databases;
show databases;
![image](https://user-images.githubusercontent.com/101482368/158717867-998c8c7f-d8a5-431a-be0f-ae95d104f545.png)
######################
end

