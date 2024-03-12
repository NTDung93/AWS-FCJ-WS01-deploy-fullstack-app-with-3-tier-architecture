---
title : "Create VPC"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---
## Create VPC

1. Access the **AWS Management Console** interface:
   - Locate and click on **VPC**
   - Choose **VPC**

![Create VPC](/images/1/0001.png?featherlight=false&width=90pc)

2. Within the **VPC** interface:
   - Select **Your VPC**
   - Click on **Create VPC**

![Create VPC](/images/1/0002.png?featherlight=false&width=90pc)

3. Follow these steps to create a VPC:
   - Choose **Resource** and select **VPC only**
   - Enter **Name tag** as **`ASG`**
   - Set **IPv4 CIDR** to **`10.10.0.0/16`**

![Create VPC](/images/1/0003.png?featherlight=false&width=90pc)

::: warning Important Note
For the **Tenancy** configuration, it's recommended to keep the default setting. Switching to **Dedicated** may restrict the creation of certain **EC2 Instance types** within the VPC, as they require the default tenancy.
:::

4. Click on **Create VPC**

![Create VPC](/images/1/0004.png?featherlight=false&width=90pc)

5. Complete the process of creating the **VPC**

![Create VPC](/images/1/0005.png?featherlight=false&width=90pc)

6. Review the details of the newly created VPC. Ensure that **Enable DNS resolution and DNS Hostname** is disabled:
   - Go to **Edit VPC settings**
   - Navigate to **DNS settings**
   - Choose and then click **Save**

![Create VPC](/images/1/0006.png?featherlight=false&width=90pc)
