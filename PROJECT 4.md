# MEAN STACK DEPLOYMENT TO UBUNTU IN AWS
* In this project, I'm going to implement a simple Book Register web form using MEAN stack
# Step 1: 
# Installed NodeJs after upadting and upgrading ubuntu and added certificates and curled with 
* sudo apt -y install curl dirmngr apt-transport-https lsb-release ca-certificates
* curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
* Ran sudo apt install -y nodejs to install node.js
![image](https://user-images.githubusercontent.com/101482368/158625996-f8bcc548-a81e-4b8a-871c-4d82efd172a5.png)
* Step 2: Installed MongoDB (Nosql DB)
![image](https://user-images.githubusercontent.com/101482368/158626573-5f8b44c6-2617-426d-8641-59b23bf6b30b.png)
* installed MondoDB with "sudo apt install -y mongodb"
![image](https://user-images.githubusercontent.com/101482368/158627041-4da1b222-8563-4603-8252-c12b0034dfcf.png)
![image](https://user-images.githubusercontent.com/101482368/158627383-6532e46b-5a58-41cc-83cc-6e137573721b.png)
* then i installed the npm node package manager aptitude package manager 
* sudo apt-get install aptitude
*  sudo aptitude install -y npm
![image](https://user-images.githubusercontent.com/101482368/158630096-c6b76fbf-9e85-4863-924f-ca43559f57f4.png)
*  Installed body-parser package to help process JSON files passed in requests to the server
* ![image](https://user-images.githubusercontent.com/101482368/158630475-e734a8ed-8868-4363-b3e4-8abb2aee48ff.png)
* Created a folder named Books
* mkdir Books && cd Books
*  n the Books directory, Initialize npm project npm init
![image](https://user-images.githubusercontent.com/101482368/158631258-8ace8a51-73b7-48f3-bf3f-f5fc72ae87c1.png)
* Added a file to it named server.js and pasted code into it
# Step 3: Install Express and set up routes to the server
* i installed the mongoose package with sudo npm install express mongoose
![image](https://user-images.githubusercontent.com/101482368/158632154-7d74536b-4126-443a-81a0-627ccc929d28.png)
* created a folder named apps
* mkdir apps && cd apps and created a file routes.js in the folder
* created folder models in the apps folder and file named book.js in the models folder
![image](https://user-images.githubusercontent.com/101482368/158633664-c11229d1-b35b-4d15-a771-61934afe5b1f.png)
# Step 4 – Accessed the routes with AngularJS
* in the books directory, created a folder named Public and a file named script.js in the public directory
mkdir public && cd public 
* Also, In the public folder, created a file named index.html;
* in the Books directory. i started the Server 
* node server.js and opened port 3300 to allow incoming traffic to the server application
![image](https://user-images.githubusercontent.com/101482368/158635367-97be774b-f27a-4e17-892b-5e3088975d69.png)
* Accesed the application from the web browser using the server IP address
![image](https://user-images.githubusercontent.com/101482368/158637638-a2b106b0-3380-4bb0-b905-9ba71fddc847.png)
![image](https://user-images.githubusercontent.com/101482368/158637886-56e5384c-3345-41ca-9e97-3e333b443d2b.png)

End of Project 4


