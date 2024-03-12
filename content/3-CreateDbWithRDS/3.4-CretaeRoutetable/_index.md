---
title : "Create Route Table"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 3.4 </b> "
---

## Create Route Table for Outbound Internet Routing via Internet Gateway

1. In the **VPC** interface:

   - Select **Route Tables**.
   - Click on **Create route table**.
   
   ![Create VPC](/images/4/0001.png?featherlight=false&width=90pc)

2. Configure the **Route table**:

   - Enter a **Name**: **```Route table-Public```**
   - Choose the **VPC**: Select **ASG** VPC (VPC ID will auto-fill).
   - Click on **Create route table**.
   
   ![Create VPC](/images/4/0002.png?featherlight=false&width=90pc)

3. Complete creating the **Route table**.

   ![Create VPC](/images/4/0003.png?featherlight=false&width=90pc)

4. To make route edits:

   - Select **Actions**.
   - Choose **Edit routes**.
   
   ![Create VPC](/images/4/0004.png?featherlight=false&width=90pc)

5. In the **Edit routes** interface:

   - Click on **Add route**.
   - Fill in the **Destination CIDR**: **```0.0.0.0/0```** representing the Internet.
   - In the **Target** section, select **Internet Gateway**, then choose the created **Internet Gateway** (Gateway ID auto-fills).
   - Click **Save changes**.
   
   ![Create VPC](/images/4/0005.png?featherlight=false&width=90pc)

6. Review and confirm the updated **Routes**.

   ![Create VPC](/images/4/0006.png?featherlight=false&width=90pc)

7. Ensure that **Route table - Public** is selected.

   - Select **Subnet Associations**.
   - Click on **Edit subnet associations**.
   
   ![Create VPC](/images/4/0007.png?featherlight=false&width=90pc)

8. In the **Edit subnet associations** step:

   - Adjust the width of the **Subnet ID** column by dragging the pane to the right.
   - Select the appropriate **2 public subnets** that were created.
   
   ![Create VPC](/images/4/0008.png?featherlight=false&width=90pc)

9. Click on **Save associations**.

   ![Create VPC](/images/4/0009.png?featherlight=false&width=90pc)

10. Review and confirm the updated **Subnet associations**.

   ![Create VPC](/images/4/00010.png?featherlight=false&width=90pc)
