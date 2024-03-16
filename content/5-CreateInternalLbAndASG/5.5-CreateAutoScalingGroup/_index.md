---
title : "Create Auto Scaling Group"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 5.5 </b> "
---

#### Create Auto Scaling Group
1. In interfatce of EC2, choose **Auto scaling group** at sidebar, then click **Create auto scaling group.**
![](/workshop01-AWS-FCJ-2024/images/5-5/01.png?width=50pc)

2. In the interface of creating ASG:
    - **Name** fill in **`AppTierASG`**
    - **Launch template** choose **AppTier-LaunchTemplate**
    - Scroll downw and click **Next**
![](/workshop01-AWS-FCJ-2024/images/5-5/02.png?width=50pc)

3. In the interface of configuring Network:
    - **VPC: my-vpc**
    - **AZs and subnets** choose **Private Subnet 1** and **Private Subnet 2**
    - Click **Next**
![](/workshop01-AWS-FCJ-2024/images/5-5/03.png?width=50pc)

4. In the next configuration interface:
    - **Load balancing** choose **Attach to an existing load balancer**
    - Choose **Choose from your load balancer target group** then choose **AppTierTargetGroup**
    - Scroll downw and click **Next**
![](/workshop01-AWS-FCJ-2024/images/5-5/04.png?width=50pc)

5. In the next configuration interface:
    - **Desired capacity**: **2**
    - **Min desired capacity**: **2**
    - **Max desired capacity**: **2**
    - Scroll downw and click **Next**
    - **Next** to the last step then click **Create auto scaling group**
![](/workshop01-AWS-FCJ-2024/images/5-5/05.png?width=50pc)

6. Finish creating ASG:
![](/workshop01-AWS-FCJ-2024/images/5-5/06.png?width=50pc)

7. After creating ASG successfully, 2 new ec2 instances will be created:
![](/workshop01-AWS-FCJ-2024/images/5-5/07.png?width=50pc)

{{% notice note %}}
→ Now we have 3 ec2 instances, now we can terminate the My App Server 1 instance (but recommend to keep it for easy troubleshooting later)
{{% /notice %}}

{{% notice note %}}
→If terminate any instance in ASG, the new instance will be launched by ASG immediately
{{% /notice %}}

8. Try to terminate both instances in ASG, 2 new instances will be launched immediately by ASG
![](/workshop01-AWS-FCJ-2024/images/5-5/08.png?width=50pc)

