# SHELL SCRIPTING
## Automate user creation by applying your shell scripting skills in the hands-on assignment. Onboard a list of new Linux users from a CSV file using a shell script.
# STEP 1 Create a script file to be executed and pasted the script inside
## vi onboard.sh
## Copied the private key onboard.sh file to the ubuntu remote server using SCP command
![image](https://user-images.githubusercontent.com/101482368/158648677-abf7e397-48da-4b98-8c5b-2513bd662a8d.png)
## SSHed to be ubuntu server to see the onboard.sh script file
![image](https://user-images.githubusercontent.com/101482368/158649025-d640d83e-b43a-4c18-8939-12a947ac1f79.png)
## Create the project folder called Shell 
## then created a csv file names.csv which will store the name of our users in the Shell folder
![image](https://user-images.githubusercontent.com/101482368/158650342-3aced951-b831-45c0-80d1-f5f273c76059.png)
Created a private and public key file in the Shell folder which is used to update the Users 
![image](https://user-images.githubusercontent.com/101482368/158651665-795b61c6-cd18-4c6f-84f0-05f140fda0ac.png)
## Updated the script in the script file onboard.sh so that the script does not fail
![image](https://user-images.githubusercontent.com/101482368/158651665-795b61c6-cd18-4c6f-84f0-05f140fda0ac.png)
## Added developer group with sudo groupadd command
## Ran the command to make the script file onboard.sh executable
## sudo chmod +x onboard.sh
![image](https://user-images.githubusercontent.com/101482368/158653659-e8bc5714-7982-4bfe-995a-3f48952b53be.png)
## Switched to root user in the shell folder to be able to run the script
## user created successfully
![image](https://user-images.githubusercontent.com/101482368/158654508-605f1d9d-8218-4992-9c48-2840145dcc24.png)
![image](https://user-images.githubusercontent.com/101482368/158654802-40c35469-1074-4be5-b0b5-db76226afc87.png)
## checked developers group and ID and password created in the etc/passwd file
![image](https://user-images.githubusercontent.com/101482368/158655264-37782f22-9d71-4966-86b3-eba38b59533e.png)
## filtered with awk command
![image](https://user-images.githubusercontent.com/101482368/158656057-a27a5709-ea2a-4f2f-9a82-54b756a99cd7.png)
## Opened another terminal to test that the user can connect and created a private key file as the public key is already present in the ubuntu server
![image](https://user-images.githubusercontent.com/101482368/158657690-a23c696f-6d7a-4009-8b67-13b51a10f203.png)
## Updated permission to protect private key before connectiong as one of the Useers
## Connected as one of the user ( bisola) and was sucessful
![image](https://user-images.githubusercontent.com/101482368/158660036-7e34d213-45fb-4913-9677-4c3f0172e839.png)
![image](https://user-images.githubusercontent.com/101482368/158660543-54588bce-6ff8-4519-99af-691ede41b66d.png)
## connected as another user ( daddy )
![image](https://user-images.githubusercontent.com/101482368/158660911-ad823b6b-3615-42ee-989e-6d43b7b1a380.png)
################
END
