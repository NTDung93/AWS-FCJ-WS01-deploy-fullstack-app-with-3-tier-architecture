---
title : "Create EC2 Server"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---

## Create EC2 Instances in Subnets

1. Access the **AWS Management Console**:

    - Navigate to **EC2**
    - Click on **Instances**

   ![Create VPC](/images/6/0001.png?featherlight=false&width=90pc)

2. In the **EC2** interface:

    - Select **Instances**
    - Choose **Launch instances**

   ![Create VPC](/images/6/0002.png?featherlight=false&width=90pc)

3. Provide a **Name and tags** for the instance, enter **```EC2 Public```**

   ![Create VPC](/images/6/0003.png?featherlight=false&width=90pc)

4. Choose the **AMI**:

    - Select **Quick Start**
    - Choose **Amazon Linux 2**
    - Select an **AMI**

   ![Create VPC](/images/6/0004.png?featherlight=false&width=90pc)

5. Select an **Instance type** and opt to **Create a new key pair**

   ![Create VPC](/images/6/0005.png?featherlight=false&width=90pc)

6. In the **Create key pair** interface:

    - Specify the **Key pair name**, e.g., **```aws-keypair```** (optional name, you can set any).
    - Choose **Key pair type: RSA**
    - Select **Private key file format: .pem**

   ![Create VPC](/images/6/0006.png?featherlight=false&width=90pc)

7. Configure the **Network**:

    - Select the **VPC**: **ASG**
    - Choose the **Subnet**: **Public Subnet 1**
    - Enable **Auto-assign public IP**
    - For **Firewall (Security Group)**, select **Select existing security group**
    - Choose **Public subnet -SG**
    - Click **Launch instance**

   ![Create VPC](/images/6/0007.png?featherlight=false&width=90pc)

8. Complete the instance creation

   ![Create VPC](/images/6/0008.png?featherlight=false&width=90pc)

9. Wait for about 5 minutes until the **Status check** shows **2/2 checks passed**

   ![Create VPC](/images/6/0009.png?featherlight=false&width=90pc)

## Create EC2 in a Private Subnet

10. In the **EC2** interface:

    - Select **Instances**
    - Choose **Launch instances**

11. Provide a **Name and tags**, enter **```EC2 Private```**

   ![Create VPC](/images/6/00010.png?featherlight=false&width=90pc)

   ![Create VPC](/images/6/00011.png?featherlight=false&width=90pc)

12. Choose the **AMI**:

     - Select **Quick Start**
     - Choose **Amazon Linux 2**
     - Select an **AMI**

   ![Create VPC](/images/6/00012.png?featherlight=false&width=90pc)

13. Make an **instance type** selection. Choose **Key pair name: ```aws-keypair```**

   ![Create VPC](/images/6/00013.png?featherlight=false&width=90pc)

14. Configure the **Network**:

      - Select the **VPC**: **ASG** VPC
      - Choose the **Subnet**: **Private subnet 2**
      - Disable **Auto-assign public IP**. If not disabling it, ensure you've checked the configuration for **automatically allocating public IP for the subnet.**

   ![Create VPC](/images/6/00014.png?featherlight=false&width=90pc)

15. Complete the instance creation:

      - Click **View all instances**

   ![Create VPC](/images/6/00015.png?featherlight=false&width=90pc)

16. Select **EC2 Private**:

      - Choose **Details**
      - Store **Private IPv4 addresses**

   ![Create VPC](/images/6/00016.png?featherlight=false&width=90pc)
