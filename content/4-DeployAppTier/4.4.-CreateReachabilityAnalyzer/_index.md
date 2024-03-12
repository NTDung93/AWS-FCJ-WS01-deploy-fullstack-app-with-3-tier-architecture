---
title : "Using Reachability Analyzer"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4.4 </b> "
---


#### Using Reachability Analyzer

![Create VPC](/images/0000.png?featherlight=false&width=90pc)

1. Access to **VPC** interface

   - Select **Reachability Analyzer**
   - Select **Create and analyze path**

![Create VPC](/images/14/0001.png?featherlight=false&width=90pc)

2. Implement **Path Configuration**

   - Name tag, enter **```EC2 private with EC2 Public```**
   - For **Source type**, select **Instance**
   - Select **source** as **EC2 Public**
   - For **Destination type**, select **Instance**
   - For **Destination**, select **EC2 Private**
   - The remaining parameters are left to default.
   - Select **Create and analyze path**

![Create VPC](/images/14/0002.png?featherlight=false&width=90pc)

3. Wait 5 minutes will show the **Reachable** status

![Create VPC](/images/14/0003.png?featherlight=false&width=90pc)

4. Then see path details.

![Create VPC](/images/14/0004.png?featherlight=false&width=90pc)

5. View reverse path details.

![Create VPC](/images/14/0005.png?featherlight=false&width=90pc)