---
title : "Create Subnets"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 2.5 </b> "
---

## Create Subnets

1. In VPC interface, choose **Subnets** on the sidebar, then click **Create subnet**
![Create subnet](/workshop01-AWS-FCJ-2024/images/2-5/01.png?width=50pc)

2. In **Create subnet** interface, choose the VPC just created is **my-vpc**
![Create subnet](/workshop01-AWS-FCJ-2024/images/2-5/02.png?width=50pc)

3. After choosing VPC, the **Subnet settings** will appear
    - **Subnet name**, enter **`Public Subnet 1`**
    - **Availability Zone**, choose AZ Singapore **ap-southeast-1a**
    - **IPv4 CIDR block**, enter **`10.10.1.0/24`** 
    - Choose **Create subnet**
![Create subnet](/workshop01-AWS-FCJ-2024/images/2-5/03.png?width=50pc)

4. Finish creating Subnet
![Subnet created](/workshop01-AWS-FCJ-2024/images/2-5/04.png?width=50pc)

5. Perform the same steps to create more subnets
    - **`Public subnet 2`** with CIDR **`10.10.2.0/24`** and AZ **ap-southeast-1b**.
![Subnet created](/workshop01-AWS-FCJ-2024/images/2-5/05.png?width=50pc)

    - **`Private subnet 1`** with CIDR **`10.10.3.0/24`** and AZ **ap-southeast-1a**.
![Subnet created](/workshop01-AWS-FCJ-2024/images/2-5/06.png?width=50pc)

    - **`Private subnet 2`** with CIDR **`10.10.4.0/24`** and AZ **ap-southeast-1b**.
![Subnet created](/workshop01-AWS-FCJ-2024/images/2-5/07.png?width=50pc)

    - **`Private DB Subnet 1`** with CIDR **`10.10.5.0/24`** and AZ **ap-southeast-1a**.
![Subnet created](/workshop01-AWS-FCJ-2024/images/2-5/08.png?width=50pc)

    - **`Private DB Subnet 2`** with CIDR **`10.10.6.0/24`** and AZ **ap-southeast-1b**.
![Subnet created](/workshop01-AWS-FCJ-2024/images/2-5/09.png?width=50pc)

    - Finish creating 6 subnets.
![Subnet created](/workshop01-AWS-FCJ-2024/images/2-5/10.png?width=50pc)

#### Allow auto-assign public IP address for 2 public subnets
6. In Subnets interface, choose **Public Subnet 1**, choose **Actions** and choose **Edit subnet settings**
![Edit subnet settings](/workshop01-AWS-FCJ-2024/images/2-5/11.png?width=50pc)

7. Tick **Enable auto-assign public IPv4 address**, then choose **Save**
![Edit subnet settings](/workshop01-AWS-FCJ-2024/images/2-5/12.png?width=50pc)
![Edit subnet settings](/workshop01-AWS-FCJ-2024/images/2-5/13.png?width=50pc)

8. Repeat the steps above to apply for **Public subnet 02**
![Edit subnet settings](/workshop01-AWS-FCJ-2024/images/2-5/14.png?width=50pc)

9. Go back to **Your VPCs** and view the **Resource map** of **my-vpc**
![Resource map](/workshop01-AWS-FCJ-2024/images/2-5/15.png?width=50pc)
