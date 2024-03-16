---
title : "Create NAT Gateway"
date :  "`r Sys.Date()`" 
weight : 7
chapter : false
pre : " <b> 2.7 </b> "
---

## Create NAT Gateway

1. In the VPC interface, click **NAT gateways** on the sidebar, then click **Create NAT gateway**
![Create NAT gateway](/workshop01-AWS-FCJ-2024/images/2-7/01.png?width=50pc)

2. In the create NAT gateway interface
    - **Name** enter **`nat-gw-01`**
    - **Subnet** choose **Public Subnet 1**
    - **EIP** click **Allocate Elastic IP**
    - Click **Create NAT gateway**
![Create NAT gateway](/workshop01-AWS-FCJ-2024/images/2-7/02.png?width=50pc)

3. Finish creating NAT gateway in **Public Subnet 1** of the first AZ
![Create NAT gateway](/workshop01-AWS-FCJ-2024/images/2-7/03.png?width=50pc)

4. Repeat the steps to create NAT gateway in **Public Subnet 2** of the second AZ
![Create NAT gateway](/workshop01-AWS-FCJ-2024/images/2-7/04.png?width=50pc)

5. Finish creating NAT gateway in **Public Subnet 2** of the second AZ
![Create NAT gateway](/workshop01-AWS-FCJ-2024/images/2-7/05.png?width=50pc)