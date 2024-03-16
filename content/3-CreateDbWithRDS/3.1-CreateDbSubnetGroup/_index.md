---
title : "Create database subnet group"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---
#### What is Database subnet group and why do we need it?
A database subnet group is a collection of subnets that you create in your VPC. When you create a database instance, you need to specify a database subnet group. The database subnet group must contain at least one subnet in each AZ. The database subnet group ensures that the database instance can be deployed across multiple AZs for high availability.

#### Create database subnet group
1. Find and access the **RDS** service
![](/workshop01-AWS-FCJ-2024/images/3-1/01.png?width=50pc)

2. Choose **Subnet groups** in the sidebar and click **Create DB subnet group**
![](/workshop01-AWS-FCJ-2024/images/3-1/02.png?width=50pc)

3. In the create DB subnet group interface:
   - **Name** fill in **`db-subnet-group`**
   - **Description** fill in **`db-subnet-group`**
   - **VPC** choose **my-vpc**
![](/workshop01-AWS-FCJ-2024/images/3-1/03.png?width=50pc)

4. In the Add subnets section:
   - **AZ** choose **ap-southeast-1a** and **ap-southeast-1b**
   - **Subnets** choose **Private DB Subnet 1** and **Private DB Subnet 2** (you can go back to the list of subnets, see the CIDR of each subnet to choose the right one)
   - Then click **Create**
![](/workshop01-AWS-FCJ-2024/images/3-1/04.png?width=50pc)

5. Complete creating Subnet group.
![](/workshop01-AWS-FCJ-2024/images/3-1/05.png?width=50pc)