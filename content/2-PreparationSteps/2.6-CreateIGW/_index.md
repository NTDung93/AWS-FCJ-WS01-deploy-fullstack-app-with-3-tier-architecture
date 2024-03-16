---
title : "Create Internet Gateway"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 2.6 </b> "
---

## Create Internet Gateway

1. In the VPC interface, choose **Internet gateways** on the sidebar, then click **Create internet gateway**
![Create internet gateway](/workshop01-AWS-FCJ-2024/images/2-6/01.png?width=50pc)

2. In **Create internet gateway** interface
    - **Name tag**, enter **`workshop-01-igw`**
    - Click **Create internet gateway**
![Create internet gateway](/workshop01-AWS-FCJ-2024/images/2-6/02.png?width=50pc)

3. In the detail of the created IGW
    - Choose **Actions**
    - Choose **Attach to VPC**
![Create internet gateway](/workshop01-AWS-FCJ-2024/images/2-6/03.png?width=50pc)

4. In **Attach to VPC**
    - Choose VPC **my-vpc**
    - Choose **Attach internet gateway**
![Create internet gateway](/workshop01-AWS-FCJ-2024/images/2-6/04.png?width=50pc)

5. Finish creating and attaching IGW to VPC
![Create internet gateway](/workshop01-AWS-FCJ-2024/images/2-6/05.png?width=50pc)