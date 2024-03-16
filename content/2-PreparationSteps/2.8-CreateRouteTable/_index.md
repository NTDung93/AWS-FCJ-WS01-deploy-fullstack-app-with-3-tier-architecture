---
title : "Create Route Table"
date :  "`r Sys.Date()`" 
weight : 8
chapter : false
pre : " <b> 2.8 </b> "
---

## Create Route Table

1. In the VPC interface, click **Route Tables** on the sidebar, then click **Create Route Table**
![Create route table](/workshop01-AWS-FCJ-2024/images/2-8/01.png?width=50pc)

2. In the Create route table interface:
    - **Name** enter **`public-route-table`**
    - **VPC** choose **my-vpc**
    - Click **Create route table**
![Create route table](/workshop01-AWS-FCJ-2024/images/2-8/02.png?width=50pc)

3. After successfully creating the route table, click **Edit routes**
![Edit routes](/workshop01-AWS-FCJ-2024/images/2-8/03.png?width=50pc)

4. In the Edit routes interface, choose **Add route**
![Add route](/workshop01-AWS-FCJ-2024/images/2-8/04.png?width=50pc)

5. Then add a route with **Destination** is **`0.0.0.0/0`** and **Target** is **workshop-01-igw** then click **Save changes**
![Add route](/workshop01-AWS-FCJ-2024/images/2-8/05.png?width=50pc)

6. After successfully creating, switch to the **Subnet associations** tab and click **Edit subnet associations**
![Edit subnet associations](/workshop01-AWS-FCJ-2024/images/2-8/06.png?width=50pc)

7. Choose 2 public subnets we have created then click **Save associations**
![Edit subnet associations](/workshop01-AWS-FCJ-2024/images/2-8/07.png?width=50pc)

8. Perform the same steps to create **private-route-table-01** for **private subnet 1**
![Create route table](/workshop01-AWS-FCJ-2024/images/2-8/08.png?width=50pc)

9. Add a route with **Destination** is **`0.0.0.0/0`** and **Target** is **nat-gw-01** then click **Save changes**
![Add route](/workshop01-AWS-FCJ-2024/images/2-8/09.png?width=50pc)

10. Choose **private subnet 1** then click **Save associations**
![Edit subnet associations](/workshop01-AWS-FCJ-2024/images/2-8/10.png?width=50pc)

#### Create route table for 2 private db subnets
11. Perform the same steps to create **private-db-route-table**:
    - **VPC** choose **my-vpc**
    - Add a route with **Destination** is **`0.0.0.0/0`** and **Target** is **igw** (to communicate with db instance from outside the vpc)
    - Assign this route table to 2 subnets **Private DB Subnet 1** and **Private DB Subnet 2**
![Create route table](/workshop01-AWS-FCJ-2024/images/2-8/11.png?width=50pc)
