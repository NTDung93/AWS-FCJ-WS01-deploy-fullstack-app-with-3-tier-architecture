---
title : "Create Auto Scaling Group"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 7.5 </b> "
---

#### Create Auto Scaling Group
1. In interfatce of EC2, choose **Auto scaling group** at sidebar, then click **Create auto scaling group.**
![](/workshop01-AWS-FCJ-2024/images/5-5/01.png?width=50pc)

2. In the interface of creating ASG:
    - **Name** fill in **`WebTierASG`**
    - **Launch template** choose **WebTier-LaunchTemplate**
    - Scroll downw and click **Next**
![](/workshop01-AWS-FCJ-2024/images/7-5/02.png?width=50pc)

3. In the interface of configuring Network:
    - **VPC: my-vpc**
    - **AZs and subnets** choose **Public Subnet 1** and **Public Subnet 2**
    - Click **Next**
![](/workshop01-AWS-FCJ-2024/images/7-5/03.png?width=50pc)

4. In the next configuration interface:
    - **Load balancing** choose **Attach to an existing load balancer**
    - Choose **Choose from your load balancer target group** then choose **WebTierTargetGroup**
    - Scroll downw and click **Next**
![](/workshop01-AWS-FCJ-2024/images/7-5/04.png?width=50pc)

5. In the next configuration interface:
    - **Desired capacity**: **2**
    - **Min desired capacity**: **2**
    - **Max desired capacity**: **2**
    - Scroll downw and click **Next**
    - **Next** to the last step then click **Create auto scaling group**
![](/workshop01-AWS-FCJ-2024/images/7-5/05.png?width=50pc)

6. Finish creating ASG:
![](/workshop01-AWS-FCJ-2024/images/7-5/06.png?width=50pc)

7. After creating ASG successfully, 2 new ec2 instances will be created:
![](/workshop01-AWS-FCJ-2024/images/7-5/09.png?width=50pc)

8. Now we can open web by **DNS name** of **web-tier-external-lb**
![](/workshop01-AWS-FCJ-2024/images/7-5/08.png?width=50pc)

