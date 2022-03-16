# WEB STACK IMPLEMENTATION (LEMP STACK)

# STEP 1 – INSTALLING THE NGINX WEB SERVER after updating and upgrading server package with sudo apt update and sudo apt upgrade
## sudo apt install nginx
 ![image](https://user-images.githubusercontent.com/101482368/158487628-b472ea79-07b3-4c93-80e6-9b49d81b3315.png)
## accessed Nginix from ubuntu shell 
![image](https://user-images.githubusercontent.com/101482368/158487714-5133854c-42d0-4f33-b962-4dabf62b2126.png)
## Accessed Niginix from the local server via public IP address
![image](https://user-images.githubusercontent.com/101482368/158487899-14182429-212d-4d27-b98a-264ea3be10f8.png)
# STEP 2 — INSTALLING MYSQL
## sudo apt install mysql-server and running the secure installation package to remove some insecure default settings and lock down access to your database system and start the interactive script by running:
## 'sudo mysql_secure_installation
![image](https://user-images.githubusercontent.com/101482368/158488681-62b122cc-85ee-4aa7-9947-583deb11b5b1.png)
# STEP 3 – INSTALLING PHP
## Installed PHP along the mysql and PHP fpm module to allow PHP communicate with database and tell Nginx to pass PHP requests to this software for processing.
## sudo apt install php-fpm php-mysql
![image](https://user-images.githubusercontent.com/101482368/158489897-63c212c3-aec1-4c48-9940-6e966387f5bf.png)
# STEP 4: with PHP installed, PHP needs to be configured to use the processor
## projectlemp domain is created in /var/www/htmld directory
## sudo mkdir /var/www/projectLEMP
## Assign ownership of the directory with the $USER environment variable, which will reference your current system user
## sudo chown -R $USER:$USER /var/www/projectLEMP
## ![image](https://user-images.githubusercontent.com/101482368/158490581-0c5dde12-1150-40dc-b4bd-fa98073a6d25.png)
## Opened a new configuration file in Nginx’s sites-available directory
## sudo nano /etc/nginx/sites-available/projectLEMP
## Activated configuration by linking to the config file from Nginx’s sites-enabled directory:
## Tested configuration for syntax errors by typing:
## sudo nginx -t
## ![image](https://user-images.githubusercontent.com/101482368/158491939-6bb6a85b-6e44-406b-ab81-a7633f674c74.png)
## Disable default Nginix host with 
## sudo unlink /etc/nginx/sites-enabled/default
## Reloaded Nginix to apply changes
## Created an index.html file in the /var/www/html web root directory to test thatthe new server blocks works as expected
## sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html
## ![image](https://user-images.githubusercontent.com/101482368/158492503-357b752a-ed1b-4011-8445-5da9c14a7244.png)
## Opened web browser with IP address with new output
![image](https://user-images.githubusercontent.com/101482368/158492629-d7ab2f80-79b7-4f17-93ce-21697f5f8233.png)
# STEP 5 – TESTING PHP WITH NGINX
## created a test PHP file to test PHP with NGINIX
## sudo vi /var/www/projectLEMP/info.php
## Accessed page from the web browser by visiting the public IP address set up in Nginx configuration file, followed by /info.php:
![image](https://user-images.githubusercontent.com/101482368/158493332-184188fe-63c2-404a-8e75-6800582775a2.png)
# STEP 6 – RETRIEVING DATA FROM MYSQL DATABASE WITH PHP
## Created Databse 
## mysql> CREATE DATABASE `example_database`;
## Created a new user and granted him full privileges on the database.
## CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';
## Gave user permission over the example_database database
## GRANT ALL ON example_database.* TO 'example_user'@'%';
![image](https://user-images.githubusercontent.com/101482368/158494020-e6cb9dd1-410b-4f48-bf27-87bbe0a23a8e.png)
## Exited and tested if the new user has proper permission log into mysql.
## mysql -u example_user -p
## show databases
## ![image](https://user-images.githubusercontent.com/101482368/158494403-a906d01e-8e6c-4f9a-b815-97899b35da72.png)
## create a test table named todo_list. From the MySQL shell
## CREATE TABLE example_database.todo_list (
item_id INT AUTO_INCREMENT,
content VARCHAR(255),
PRIMARY KEY(item_id)
);
## Inserted into table in database performed a select function on the table in the databse
![image](https://user-images.githubusercontent.com/101482368/158496465-e50ed624-f5a7-4bd4-bb77-4cded9bdfe46.png)
## Created a new PHP file with PHP script in your custom web root directory that will connect to mysql and query for content.
## vi /var/www/projectLEMP/todo_list.php
## Accessed the page from the web browser
![image](https://user-images.githubusercontent.com/101482368/158498374-5ad46707-db85-474a-9e20-4da7a2ec9632.png)
##################### END

