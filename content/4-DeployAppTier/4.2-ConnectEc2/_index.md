---
title : "Connect to EC2 instance"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---

## Connect to EC2 instance

1. On the EC2 instances interface, select the instance you just created and click **Connect**
![connect ec2](/workshop01-AWS-FCJ-2024/images/4-2/01.png?width=50pc)

2. Switch to the **Session Manager** tab and click Connect
![connect ec2](/workshop01-AWS-FCJ-2024/images/4-2/02.png?width=50pc)

3. Successfully connect to the instance
![connect ec2](/workshop01-AWS-FCJ-2024/images/4-2/03.png?width=50pc)

4. Run the command **`sudo -su ec2-user`** to switch from user to ec2-user, and have root administrative rights for the instance
![connect ec2](/workshop01-AWS-FCJ-2024/images/4-2/04.png?width=50pc)

5. Then run the command **`ping 8.8.8.8`** (IP address of Google’s DNS server) to test whether our instance can connect to the outside internet through igw or not
![connect ec2](/workshop01-AWS-FCJ-2024/images/4-2/05.png?width=50pc)