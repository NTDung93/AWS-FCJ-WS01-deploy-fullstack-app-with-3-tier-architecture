---
title : "Tạo Internal Load Balancer"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 5.3 </b> "
---

#### Tạo Internal Load Balancer
1. Ở giao diện EC2, chọn **Load balancers** ở sidebar, sau đó click **Create load balancer**
![ILB](/workshop01-AWS-FCJ-2024/images/5-3/01.png?width=50pc)

2. Tại giao diện chọn balancer type, click chọn **Create** của **Application Load Balancer**
![ILB](/workshop01-AWS-FCJ-2024/images/5-3/02.png?width=50pc)

3. Tại màn hình tạo ALB:
    - **LB Name** điền **`app-tier-internal-lb`**
    - **Scheme** chọn **Internal**
![ILB](/workshop01-AWS-FCJ-2024/images/5-3/03.png?width=50pc)

4. Ở phần **Network mapping**:
    - **VPC: my-vpc**
    - Tick chọn **ap-southeast-1a**, sau đó chọn **Private Subnet 1**
    - Tick chọn **ap-southeast-1b**, sau đó chọn **Private Subnet 2**
![ILB](/workshop01-AWS-FCJ-2024/images/5-3/04.png?width=50pc)

5. Ở phần **Security groups** chọn **Internal-LB-SG**. Ở phần **Listeners and routing**, **default action** chọn **AppTierTargetGroup**. Lướt xuống dưới cùng và click **Create load balancer**.
![ILB](/workshop01-AWS-FCJ-2024/images/5-3/05.png?width=50pc)

6. Hoàn thành tạo load balancer cho app tier.
![ILB](/workshop01-AWS-FCJ-2024/images/5-3/06.png?width=50pc)