# LOAD BALANCER SOLUTION WITH APACHE
# Created EC2 to configure as Apache load Balancer
![image](https://user-images.githubusercontent.com/101482368/159372448-8414fd8f-fcaa-446e-bdcf-7d0622b367ee.png)
## Iinstalled Apache on EC2 LB and restarted Apache
![image](https://user-images.githubusercontent.com/101482368/159373383-be97444f-fc6a-495f-afeb-8f0d84227183.png)
![image](https://user-images.githubusercontent.com/101482368/159373570-41b97c32-2e4d-4a04-ae6c-4d661af58038.png)
## Configured load balancer
![image](https://user-images.githubusercontent.com/101482368/159374847-88d23235-ffe9-4da7-bbd3-8dadeede8341.png)
## Verified that configuration works by accessing LB public IP from the web browser
![image](https://user-images.githubusercontent.com/101482368/159377163-868d5f8a-e921-4690-80bd-0354672813ed.png)
![image](https://user-images.githubusercontent.com/101482368/159377245-d6329be4-77d9-4564-afd3-017ac57f8c72.png)
## Verified that both webservers receive Get by refeshing the webpage (apache lb) new records appear in each server's and it was even distributed
![image](https://user-images.githubusercontent.com/101482368/159377714-aa60382d-aa7a-40c6-8198-4e16a706647d.png)
## Configured Local DNS Names Resolution in the LB server
![image](https://user-images.githubusercontent.com/101482368/159378525-470e57ef-bdd3-4525-9e52-3948d959231c.png)
## Updated B config file with configured local DNS names
![image](https://user-images.githubusercontent.com/101482368/159378994-cc2eb15e-e762-4b9c-9aea-4fd9e674f1cf.png)
## Curled the webservers locally from the LB terminal
![image](https://user-images.githubusercontent.com/101482368/159379340-d2268d52-9dfe-4492-9ad7-e7086009b41e.png)
## updated architecture to include LB to evenly distribute traffic btw webservers
![image](https://user-images.githubusercontent.com/101482368/159379493-044e2397-e6d0-4cd4-ad1e-da0cfcab2815.png)
########################################################
end
