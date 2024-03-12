---
title : "Create EC2 Instance Connect Endpoint (Optional)"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 4.5 </b> "
---

#### EC2 Instance Connect Endpoint

In step 4.2 test connection, to access **EC2 Private** you need to:
1. Use the **pscp** tool to copy the key pair from our machine to **EC2 Public**
2. Access **EC2 Public**
3. Grant permission to **key pair**
4. SSH to **EC2 Private** server

-> As you can see, now **EC2 Public** acts as **Bastion Host** and we need to pay for this instance. So is there a way to save costs, reduce configuration steps while still accessing **EC2 Private** and ensuring security?

On June 13, 2023, AWS launched the **EC2 Instance Connect Endpoint (EIC Endpoint)** function to help customers access EC2 instances without needing **public IP addresses**, through the protocol **SSH** and **RDP**.

**EIC Endpoint** replaces **Bastion Host**, which means eliminating the workload: patching, managing, auditing and the cost of the previous **Bastion Host** instance. There are no additional costs for **EIC Endpoint**, however [data transfer costs](https://000034.awsstudygroup.com/en/8-data-transfer-overview/) will apply

#### Architecture description **EIC Endpoint**

![Create VPC](/images/4-CreateEc2Server/4.5-eic/0001.png?featherlight=false&width=90pc)

1. Create Security Group for **EIC Endpoint**

   - In the search box, enter: **security groups**, in the features section select **Security groups**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0002.png?featherlight=false&width=90pc)

   - Select **Create security group**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0003.png?featherlight=false&width=90pc)

  - In the **Security group name** section, enter ``EIC Endpoint``
  - In the **Description** section, enter ``Allow SSH for MyIP``
  - In the VPC section, select **ASG VPC**
  - Select **Add rule**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0004.png?featherlight=false&width=90pc)

  - In the **Type** section, select protocol **SSH**
  - In the **Source** section, select **My IP** with the meaning: only allow your IP address with SSH protocol to pass through this Security group
  - The remaining values ​​remain the same.
  - Select **Create security group**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0005.png?featherlight=false&width=90pc)

2. Create **EC2 Instance Connect Endpoint**

   - In the search box, enter: ``endpoint services`` , in the Features section select **endpoint services**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0006.png?featherlight=false&width=90pc)

   - Select **Create endpoint**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0007.png?featherlight=false&width=90pc)

   - In the **Name tag** section, enter: ``EC2 private endpoint``
   - In the **Service category** section, select: **EC2 Instance Connect Endpoint**
   - In **VPC** section, select **ASG-VPC**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0008.png?featherlight=false&width=90pc)

   - In the **Security groups** section, select: **EIC Endpoint** created in step 1
   - In the **Subnet** section, select: **subnet-0da7e5096deb895e1 (Private subnet 2)** is the subnet of EC2 Private
   - Select **Create endpoint**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0009.png?featherlight=false&width=90pc)

   - Wait for Status to change to **Available** and go to the next step
![Create VPC](/images/4-CreateEc2Server/4.5-eic/00010.png?featherlight=false&width=90pc)

3. Access EC2 Private via **EC2 Instance Connect Endpoint**

- At the EC2 interface, check the **box** of EC2 Private
- In the **Public IPv4 address** section, check and see: there is no Public IP value - meaning we cannot access this EC2 via Public IP
- Select **Connect**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/00011.png?featherlight=false&width=90pc)

- In the **Connection Type** section, select **Connect using EC2 Instance Connect Endpoint**
- In the **EC2 Instance Connect Endpoint** section, select the EIC just created in step 2
- Select **Connect**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/00012.png?featherlight=false&width=90pc)

- Congratulations, you have successfully accessed EC2 Private via **EC2 Instance Connect Endpoint** only from your IP address
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/00013.png?featherlight=false&width=90pc)

Note:
- Normally, you will do the lab using a user with AdministratorAccess permission . In the opposite case, you need to refer to the documentation to grant the User permission to operate the above steps. [IAM permissions to use EC2 Instance Connect Endpoint](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/permissions-for-ec2-instance-connect-endpoint.html)