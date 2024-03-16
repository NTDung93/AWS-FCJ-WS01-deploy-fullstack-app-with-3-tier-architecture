---
title : "Create EC2 instance"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 6.3 </b> "
---

#### Create EC2 instance
1. Similar to creating an instance for the App server, create an instance for the **web server** with the following changes:
    - **Instance name** fill in **`My Web Server 1`**
    - **Subnet** select **Public Subnet 1**
    - **Security group** select **WebTier-SG**
    - **Advanced details**, **IAM instance profile** select **ec2role**
    - Finally, select **Launch instance**
![](/workshop01-AWS-FCJ-2024/images/6-3/01.png?width=50pc)
![](/workshop01-AWS-FCJ-2024/images/6-3/02.png?width=50pc)

2. Complete creating an EC2 instance for the **web server**
![](/workshop01-AWS-FCJ-2024/images/6-3/03.png?width=50pc)