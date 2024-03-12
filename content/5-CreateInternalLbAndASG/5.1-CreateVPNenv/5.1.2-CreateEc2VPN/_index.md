---
title : "Create EC2 as a Customer Gateway"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 5.1.2 </b> "
---
## Create EC2 as a Customer Gateway

1. **Access to VPC**

   - Select **Security Group**
   - Select **Create security group**

   ![Create VPC](/images/10/0001.png?featherlight=false&width=90pc)

2. **In the Create security group interface**

   - **Security group name**: Enter **`VPN Public -SG`**
   - **Description**: Allow IPSec, SSH, and Ping for servers in the public subnet.
   - **VPC**: Select **ASG VPN** VPC

   ![Create VPC](/images/10/0002.png?featherlight=false&width=90pc)

3. **Configure Inbound rules**

   - Select **Add rule**
   - **Type**: **SSH**, **Source**: **My IP** (Your public IPv4 address).
   - Click **Add rule** to add a new rule.
   - **Type**: **All ICMP IPv4**, **Source**: **Anywhere** (Allow ping from any IP address).
   - Click **Add rule** to add a new rule.
   - **Type**: **Custom UDP**, **Port: 400**, **Source**: **Anywhere**.
   - Click **Add rule** to add a new rule.
   - **Type**: **Custom TCP**, **Port: 500**, **Source**: **Anywhere**.

   ![Create VPC](/images/10/0003.png?featherlight=false&width=90pc)

4. Check **Outbound rules** and select **Create security group**

   ![Create VPC](/images/10/0004.png?featherlight=false&width=90pc)

5. Complete the creation of **VPN Public - SG**. A Security Group has been created. Next, we will proceed to create an EC2 server that plays the Customer Gateway role.

   ![Create VPC](/images/10/0005.png?featherlight=false&width=90pc)

6. **Access to EC2**

   - Select **Instances**
   - Select **Launch instances**

   ![Create VPC](/images/10/0006.png?featherlight=false&width=90pc)

7. In the **Launch instances** interface

   - **Name**: Enter **`Customer Gateway instance`**

   ![Create VPC](/images/10/0007.png?featherlight=false&width=90pc)

8. Executing **AMI** Selection

   - Select **Quick Start**
   - Select **Amazon Linux**
   - Select **AMI**

   ![Create VPC](/images/10/0008.png?featherlight=false&width=90pc)

9. Select **Instance type** and select **Key pair**: **aws-keypair** (keypair created with instances)

   ![Create VPC](/images/10/0009.png?featherlight=false&width=90pc)

10. Configure **Network**

    - **VPC**: Select **ASG VPN** VPC
    - **Subnet**: Select **VPN Public**
    - **Auto-assign public IP**: Select **Enable**
    - **Firewall**: Select **Select existing security group**
    - Select **VPN Public - SG**
    - Check again and select **Launch instance**

    ![Create VPC](/images/10/00010.png?featherlight=false&width=90pc)

11. Finish creating the **EC2 instance**

    - Select **View all instances**

    ![Create VPC](/images/10/00011.png?featherlight=false&width=90pc)

12. View details of the **Customer Gateway instance**

   ![Create VPC](/images/10/00012.png?featherlight=false&width=90pc)
