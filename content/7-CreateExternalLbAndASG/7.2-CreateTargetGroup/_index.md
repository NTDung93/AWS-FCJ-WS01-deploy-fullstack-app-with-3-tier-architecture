---
title : "Create Target group for Web Tier"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 7.2 </b> "
---

#### Create Target group for App Tier
1. In the EC2 Dashboard, click on **Target Groups** under **Load Balancing** at sidebar, and then click on **Create target group**.
![Target group](/workshop01-AWS-FCJ-2024/images/5-2/01.png?width=50pc)

2. In the interface of creating Target group:
    - **Target group name** fill in **`WebTierTargetGroup`**.
    - **Protocol: HTTP, Port: 80** (this is the port that nginx listens).
    - **VPC** choose **my-vpc**
    - Scroll down and click **Next** then click **Create target group**.
![Target group](/workshop01-AWS-FCJ-2024/images/7-2/02.png?width=50pc)
![Target group](/workshop01-AWS-FCJ-2024/images/7-2/03.png?width=50pc)

3. Finish creating target group
![Target group](/workshop01-AWS-FCJ-2024/images/7-2/04.png?width=50pc)
