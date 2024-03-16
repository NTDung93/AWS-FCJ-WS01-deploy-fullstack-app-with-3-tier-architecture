---
title : "Create database instance"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---

## Create database instance

1. In the Amazon RDS interface, select **Databases** in the sidebar and then click **Create database**
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/01.png?width=50pc)

2. In the Create database interface:
   - **Creation method** select **Standard create**
   - **Engine type** select **MySQL**
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/02.png?width=50pc)

3. **Templates** select **Dev/Test**, **Deployment options** select **Multi-AZ DB instance** (to create the main instance in the current AZ, and a clone instance in the remaining AZ defined in the db subnet group to prevent failover)
→ This deployment method will be best practice as it meets the criteria of High availability and Data redundancy
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/03.png?width=50pc)

- But we can choose another option is **Free tier** to be suitable for the scope of the problem, and save costs
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/04.png?width=50pc)

4. In the Settings section:
   - **DB instance identifier** fill in **`database-1`**
   - **Master username** fill in **`admin`**
   - **Master password** fill in **`12345678`**
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/05.png?width=50pc)

5. In the Connectivity section:
   - **Computer resource** select **Dont connect to EC2**
   - **VPC** select **my-vpc**
   - **DB subnet group** select **db-subnet-group** we created
   - **Public access** select **No** (select **Yes** if you want to test connection from public network)
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/06.png?width=50pc)
   - **VPC SG** select **Choose existing**
   - **Existing VPC SG** select **DataTier-SG**
   - **AZ** select **ap-southeast-1a**
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/07.png?width=50pc)

6. In the **Additional configuration** section, fill in the db name as **`demodb`** (**master name: admin, pass: 12345678**)
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/08.png?width=50pc)

7. Scroll down to the bottom and select **Create database**:
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/09.png?width=50pc)

8. Complete creating the database instance
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/10.png?width=50pc)

## Reconfigure to test connection from public network
{{% notice note %}}
To be able to test the connection to the endpoint of the newly created db from the public network, we need to reconfigure some things as follows (after testing, remember to return everything to the initial state)
   - Go to the **private-db-route-table** route table, add a new route with destination **0.0.0.0/0** and target **internet gateway** we created
   - In the **DataTier-SG** security group, add a new inbound rule to allow All traffic access
   - Update the status of **Public access** in the **Connectivity** section in the db instance from **No** to **Yes**
{{% /notice %}}

## Test connection to the endpoint of the newly created db instance
1. In the **MySQL Workbench** software, create a new connection:
   - **Connection Name** fill in **`db-ws-01`** 
   - **Hostname** copy and paste the **endpoint** of the newly created db instance
   - **Port** fill in **`3306`**
   - **Username** fill in **`admin`**
   - **Password** click **Store in Vault** then enter **`12345678`**
   - Finally, click **Test Connection**
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/11.png?width=50pc)

2. If the connection is successful, the following message will appear:
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/12.png?width=50pc)

3. Access file **application.properties** and reconfigure **datasource url**, **username** and **password** as shown below
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/13.png?width=50pc)

4. Run app and check in the connection just created in MySQL, we see that the tables have been auto-generated thanks to the **code first** mechanism (just for testing because in this workshop we will use **database first**)
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/14.png?width=40pc)
