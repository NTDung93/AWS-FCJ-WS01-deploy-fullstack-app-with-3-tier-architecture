---
title : "Connect to EC2 instance"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 6.4 </b> "
---

#### Connect to EC2 instance
1. Similar to connecting to the app server instance, we connect through **Session manager**.
![](/workshop01-AWS-FCJ-2024/images/6-4/01.png?width=50pc)

2. Switch to ec2-user.
![](/workshop01-AWS-FCJ-2024/images/6-4/02.png?width=50pc)

3. Check the connection by pinging the ip of the Google DNS server → connected to the internet through IGW.
![](/workshop01-AWS-FCJ-2024/images/6-4/03.png?width=50pc)

4. Download **NPM** to the instance:
    - **`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash`**
    - **`source ~/.bashrc`** to reload the bash shell configuration file to apply the npm just downloaded
![](/workshop01-AWS-FCJ-2024/images/6-4/04.png?width=50pc)
    - Run **`nvm install 16`** then run **`nvm use 16`** to download and use **Node.js version 16**
![](/workshop01-AWS-FCJ-2024/images/6-4/05.png?width=50pc)

5. To copy code from the **library-app-fe** folder from the **S3 bucket** we run the following commands:
    - **`cd`** to go to the **user’s home directory**
    - **`aws s3 cp s3://demowebapp-workshop-01/library-app-fe/ web-tier --recursive`** to copy all files from the library-app-fe folder and its sub-folders to the web-tier folder on the instance (if the web-tier folder does not exist, the instance will automatically create a new folder)
![](/workshop01-AWS-FCJ-2024/images/6-4/06.png?width=50pc)

6. Download the dependencies:
    - **`cd web-tier`** to access the folder
    - **`ls -ltr`** to list the files and sub-folders of web-tier
![](/workshop01-AWS-FCJ-2024/images/6-4/07.png?width=50pc)
    - **`npm install`** to download the necessary libraries or dependencies
![](/workshop01-AWS-FCJ-2024/images/6-4/08.png?width=50pc)
![](/workshop01-AWS-FCJ-2024/images/6-4/09.png?width=50pc)
    - **`npm run build`** to build the source code
![](/workshop01-AWS-FCJ-2024/images/6-4/10.png?width=50pc)
    - **`sudo amazon-linux-extras install nginx1 -y`** to download nginx (nginx acts as a web server to help the app run on port 80, as well as help direct API calls to the internal load balancer)
7. Config Nginx:
    - **`cd /etc/nginx`**
    - **`ls`**
    - We will see the **nginx.conf** file in the nginx folder. We need to **delete** this file and **replace** it with the file we have configured and uploaded to the s3 bucket.
![](/workshop01-AWS-FCJ-2024/images/6-4/11.png?width=50pc)
    - **`sudo rm nginx.conf`**
    - **`sudo aws s3 cp s3://demowebapp-workshop-01/nginx.conf .`** to copy the file from the bucket to the nginx folder
![](/workshop01-AWS-FCJ-2024/images/6-4/12.png?width=50pc)
    - **`sudo service nginx restart`** to restart Nginx
    - **`chmod -R 755 /home/ec2-user`** to grant Nginx access to all files
    - **`sudo chkconfig nginx on`** to run the Nginx service automatically every time the instance restarts