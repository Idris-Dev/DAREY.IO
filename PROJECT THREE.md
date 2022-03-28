# CREATED A SIMPLE TO-DO APPLICATION ON MERN WEB STACK
# STEP 1 – BACKEND CONFIGURATION
## updated and upgraded ubuntu server packages.
## Got the location of the Node.js software from the repo with 
## curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
## i installed the Node.js package with 'sudo apt-get install -y nodejs" and verified installation with node -v
![image](https://user-images.githubusercontent.com/101482368/158499708-7572f84f-f4a8-4815-9259-b7e80d6d854e.png)
# Application code setup by making a directory for the To_Do project 'mkdir Todo"
## changed directory to the ToDo directory and initialised the project with
## npm init 
![image](https://user-images.githubusercontent.com/101482368/158500234-29299f0f-5997-47f6-b755-e3fc5eb5949d.png)
## Time to INSTALL EXPRESSJS and create ROUTES DIRECTORIES
## I installed EXPRESS using npm
## npm install express
## create a file index.js with the command below 
## touch index.js
## Install the dotenv module
## npm install dotenv
![image](https://user-images.githubusercontent.com/101482368/158501152-a0c1256a-2ff6-4ed6-8e12-ea2e63dbcd89.png)
## Opened the index.js file with vi and pasted code into it
## Started the server with
## node index.js
![image](https://user-images.githubusercontent.com/101482368/158501665-212abbb9-87c7-4e61-a71d-1f18f91f6d54.png)
## opened TCP Port 5000 to allow incoming traffic 
##
## Accessed the site from the web browser
![image](https://user-images.githubusercontent.com/101482368/158502708-a0c99cbf-36f2-41ce-b249-d8f5380229ca.png)
## To-Do application needs to be able to Create a new task, Display list of all tasks and Delete a completed task standard HTTP request methods: POST, GET, DELETE.
## Routes folder for each of these actions would be created
## mkdir routes then chnage directory to routes folder cd routes
## created a file api.js with the command
## touch api.js
## pasted into api.js with 
## vim api.js
![image](https://user-images.githubusercontent.com/101482368/158504128-765b79b2-278d-4605-8aae-f2c9c300a2c0.png)
## Models need to be created since the app is going to make use of MongoDB (NoSql DB) but Mangoose would have to be insatlled before creating Models folder
## npm install mongoose
## mkdir models cd models and touch todo.js
![image](https://user-images.githubusercontent.com/101482368/158504726-d02b9677-2b4b-4b1b-b701-7130bcf3a295.png)
## Ran vim Todo.js and pasted the code
## updated our routes from the file api.js in ‘routes’ directory to make use of the new model.
## Opened api.js in the Routes folder and pasted the code then saved
# INSTALLING MONGODB DATABASE
# Created MONGODB Database using MLAB
## Created a file in the Todo directory and named it .env.
## touch .env   # vi .env
## updated the index.js to reflect the use of .env so that Node.js can connect to the database.
## delete existing content in the file, and update it with the code
![image](https://user-images.githubusercontent.com/101482368/158512558-81948a32-8b95-45ec-862e-ac637c258350.png)
## Started the server with 
## node index.js


tombe continued
##############1

