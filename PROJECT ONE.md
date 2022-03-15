# WEB STACK IMPLEMENTATION (LAMP STACK) 
##First step : Installed Apache using Ubuntu’s package manager ‘apt’ after updating list of packages with 'sudo apt update'
![image](https://user-images.githubusercontent.com/101482368/158427065-2a76099c-0a40-4498-8fd9-744d70d6c868.png)
##Verified that Apache is running
![image](https://user-images.githubusercontent.com/101482368/158427463-84b63cc6-d6b5-4901-990c-fa5ddec59672.png)
##Opened TCP port  80 to allow traffic from web browsers on the internet
![image](https://user-images.githubusercontent.com/101482368/158428218-575a4d42-728d-4ed6-92a9-51585379b93f.png)
##Accesed it from ubuntu shell
![image](https://user-images.githubusercontent.com/101482368/158429171-37592d63-8e1a-48ec-99c7-7e6c02f078d9.png)
##Accesed it from the internet (web browser)
![image](https://user-images.githubusercontent.com/101482368/158429710-2c597f3d-ed86-4c27-a349-eea6914e7ef7.png)
# Second Step 
##Installing Mysql-Server which is the Database server with "sudo apt install mysql-server"
##checked the version with sudo mysql -v
![image](https://user-images.githubusercontent.com/101482368/158431983-7d641af0-d789-4806-aa2e-32e7280d6b67.png)
##Ran the "sudo mysql_secure_installation" to remove some insecure default settings and lock down access to your database system
![image](https://user-images.githubusercontent.com/101482368/158432611-163d2f0d-713a-4e56-b070-32a5437a3b0a.png)
##Logged in to Mysql with "sudo mysql" and logged out with "exit"
![image](https://user-images.githubusercontent.com/101482368/158433095-346e484c-2c54-49dc-ab66-18894352ce8f.png)
##At this point, i have installed on my server; both Apache and Mysql.
#Third Step:
##Installing PHP package along with its mysql and Apache components which will allows PHP to communicate with MySQL-based databases and  enable Apache to handle PHP files respectively. The PHP package will help process code to display dynamic content to the end user.
![image](https://user-images.githubusercontent.com/101482368/158435180-2401b00b-1785-4a0c-907d-49ae92aef53b.png)
##checked version with php -v
![image](https://user-images.githubusercontent.com/101482368/158435374-bc893176-3287-40f3-b7db-e5409c40588c.png)
##At this point, your LAMP stack is completely installed and fully operational
# FOURTH STEP — 
##Time to test the setup by creating a virtual host for your website using apache
##Domain projectLamp is created in Apache on Ubuntu directory var/www/html directory using 
##Sudo mkdir /var/www/projectlamp
##Ownership of the directory assigned with 
##sudo chown -R $USER:$USER /var/www/projectlamp
##A new configration file is created in the /etc/apache2/sites-available directory using vi editor
![image](https://user-images.githubusercontent.com/101482368/158438237-ce82cc22-f9dd-4600-a6f5-bda8ad1e590b.png)
##using "sudo a2ensite projectlamp' to enable virtual host and 'sudo a2dissite 000-default' to disable default website
##Also ran sudo apache2ctl configtest to make sure config file doesnt contain syntax error 
![image](https://user-images.githubusercontent.com/101482368/158439233-03bd7632-8aa9-47ab-8e86-f1ebd37eaf63.png)
##Reloaded Apache with sudo systemctl reload apache2 for changes to take effect
##An index.html file is then created to make sure the virtual host works as expected nad it is created in the html webroot directory;
##sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html 
![image](https://user-images.githubusercontent.com/101482368/158440349-9db06bcf-3283-4dc5-80ac-8baaeccfc883.png)
##Opening the website URL with the IP address 
![image](https://user-images.githubusercontent.com/101482368/158440843-6e215e61-ae02-4f26-b8c2-19f0386a9f27.png)
#FIFTH STEP : ENABLING PHP ON THE WEBSITE
##enabling PHP to ensure index.php takes precedence over index.html in the Apache config directory by the changing the order using vi  
![image](https://user-images.githubusercontent.com/101482368/158442428-40cd4a15-5d2d-4959-ac0e-b12c99c49de3.png)
##then reloading Apache again with sudo systemctl reload apache2
##Lastly i create create a PHP script to test that PHP is correctly installed and configured on your server.
##New file named index.php inside your custom web root folder and adding a valid PHP code
![image](https://user-images.githubusercontent.com/101482368/158443273-f1d2d1d3-634b-43b8-8b5e-ef20451ae93a.png)
## Refreshed the page and new php output which indicates installiation works as expected
![image](https://user-images.githubusercontent.com/101482368/158443499-ab91e606-23ff-4d09-bf96-5d441bd7ad31.png)
