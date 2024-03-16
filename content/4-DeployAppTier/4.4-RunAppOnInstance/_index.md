---
title : "Run App on EC2 instance"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4.4 </b> "
---


#### Run App on EC2 instance

{{% notice info %}}
Idea: We will build the app's jar file, then upload the jar file to the s3 bucket. Then download the jar file to the ec2 instance and run the jar file on the instance.
{{% /notice %}}

1. Download java 17 on the instance with the command **`sudo yum install java-17-amazon-corretto-headless`**. Then check the download is successful with the command **`java -version`**
!![run app](/workshop01-AWS-FCJ-2024/images/4-4/01.png?width=50pc)

2. To generate the app's jar file, we go to the IDE, open the back end project, access **Maven**, right-click on **install** in **Lifecycle** and select **Run Maven Build**.
!![run app](/workshop01-AWS-FCJ-2024/images/4-4/02.png?width=50pc)

3. After creating the app's jar file, the jar file just created will be in the target folder
!![run app](/workshop01-AWS-FCJ-2024/images/4-4/03.png?width=50pc)

4. Access S3, access the created bucket, create a new folder named **`library-app-be`**. After creating the folder, we upload the jar file just created by dragging and dropping it into the folder
!![run app](/workshop01-AWS-FCJ-2024/images/4-4/04.png?width=50pc)

5. Before downloading s3 to the instance, we need to **make s3 public** by adding a policy to it:
   - Select the s3 bucket created, go to the **tab permission**
   - In **Bucket policy** select edit and paste the following code, then click **Save changes**
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::demowebapp-workshop-01/*"
        }
    ]
}
```
![run app](/workshop01-AWS-FCJ-2024/images/4-4/05.png?width=50pc)

6. Access the jar file in the bucket and copy the **Object URL** of it
![run app](/workshop01-AWS-FCJ-2024/images/4-4/06.png?width=50pc)

7. In the session manager, run the command **sudo wget <Object URL>** (**`sudo wget https://demowebapp-workshop-01.s3.ap-southeast-1.amazonaws.com/library-app-be/library-app-be-0.0.1-SNAPSHOT.jar`**) to download the jar file to the instance
![run app](/workshop01-AWS-FCJ-2024/images/4-4/07.png?width=50pc)

8. Run the command **`java -jar library-app-be-0.0.1-SNAPSHOT.jar`** to run the app on the instance
![run app](/workshop01-AWS-FCJ-2024/images/4-4/08.png?width=50pc)

9. To be able to temporarily test with **Postman**, we can temporarily assign **public-route-table** (for the purpose of being able to use IGW) to **private-subnet-1** (subnet containing ec2 instance) 
![run app](/workshop01-AWS-FCJ-2024/images/4-4/09.png?width=50pc)

10. Access postman, we can use **Public IPv4 address** or **Public IPv4 DNS** to call the APIs
![run app](/workshop01-AWS-FCJ-2024/images/4-4/10.png?width=50pc)
   - use **Public IPv4 address**
![run app](/workshop01-AWS-FCJ-2024/images/4-4/11.png?width=50pc)
   - use **Public IPv4 DNS**
![run app](/workshop01-AWS-FCJ-2024/images/4-4/12.png?width=50pc)

11. To keep the app running even after terminating the session, we can use **nohup** command. For example, **`nohup java -jar library-app-be-0.0.1-SNAPSHOT.jar &`**. Then we can close the session and the app will still run.
![run app](/workshop01-AWS-FCJ-2024/images/4-4/13.png?width=50pc)
   
12. To stop the app, we can run **`pkill -f 'java -jar library-app-be-0.0.1-SNAPSHOT.jar'`**
![run app](/workshop01-AWS-FCJ-2024/images/4-4/14.png?width=50pc)

{{% notice note %}}
But we need to make the app automatically run after the instance is rebooted. We will use **systemd** to do create service for the app (run java app as a service)
{{% /notice %}}

13. We will run the following commands:
   - **`sudo chmod +x /home/ec2-user/library-app-be-0.0.1-SNAPSHOT.jar`**
   - **`sudo vim /etc/systemd/system/library.service`**	

**Insert the code below into your-application.service:**

```
[Unit]
Description=Java Application as a Service
After=syslog.target

[Service]
User=ec2-user
ExecStart=ExecStart=/usr/bin/java -jar /home/ec2-user/library-app-be-0.0.1-SNAPSHOT.jar
SuccessExitStatus=143

[Install]
WantedBy=multi-user.target
```
   - **`cd /etc/systemd/system/`**
   - **`sudo chmod 777 library.service`**
   - **`sudo nano library.service`**
   - **`sudo systemctl daemon-reload`**
   - **`sudo systemctl enable library.service`**
   - **`sudo systemctl start library.service`**
   - **`sudo systemctl status library.service -l`**
   - **`sudo systemctl stop library.service`**