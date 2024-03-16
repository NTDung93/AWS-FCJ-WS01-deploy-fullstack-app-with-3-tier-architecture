---
title : "Create Internal Load Balancer"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 5.3 </b> "
---

#### Create Internal Load Balancer

1. At EC2 Dashboard, click on **Load Balancers** from the left-hand menu and then click on **Create Load Balancer**.
![ILB](/workshop01-AWS-FCJ-2024/images/5-3/01.png?width=50pc)

2. In the interface of choosing a load balancer type, select **Application Load Balancer** and click on **Create**.
![ILB](/workshop01-AWS-FCJ-2024/images/5-3/02.png?width=50pc)

3. In the ALB creation screen:
    - **LB Name** enter **`app-tier-internal-lb`**
    - **Scheme** select **Internal**
![ILB](/workshop01-AWS-FCJ-2024/images/5-3/03.png?width=50pc)

4. In the **Network mapping** section:
    - **VPC: my-vpc**
    - Tick **ap-southeast-1a**, then select **Private Subnet 1**
    - Tick **ap-southeast-1b**, then select **Private Subnet 2**
![ILB](/workshop01-AWS-FCJ-2024/images/5-3/04.png?width=50pc)

5. In the **Security groups** section, select **Internal-LB-SG**. In the **Listeners and routing** section, select **AppTierTargetGroup** for the **default action**. Scroll down to the bottom and click on **Create load balancer**.
![ILB](/workshop01-AWS-FCJ-2024/images/5-3/05.png?width=50pc)

6. Complete the load balancer creation for the app tier.
![ILB](/workshop01-AWS-FCJ-2024/images/5-3/06.png?width=50pc)

