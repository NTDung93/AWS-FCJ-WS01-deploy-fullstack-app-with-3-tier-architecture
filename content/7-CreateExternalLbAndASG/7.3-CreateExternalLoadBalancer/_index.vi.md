---
title : "Tạo External Load Balancer"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 7.3 </b> "
---

#### Tạo Internal Load Balancer
1. Ở giao diện EC2, chọn **Load balancers** ở sidebar, sau đó click **Create load balancer**
![ILB](../../../images/5-3/01.png?width=50pc)

2. Tại giao diện chọn balancer type, click chọn **Create** của **Application Load Balancer**
![ILB](../../../images/5-3/02.png?width=50pc)

3. Tại màn hình tạo ALB:
    - **LB Name** điền **`web-tier-internal-lb`**
    - **Scheme** chọn **Internet-facing**
![ILB](../../../images/7-3/03.png?width=50pc)

4. Ở phần **Network mapping**:
    - **VPC: my-vpc**
    - Tick chọn **ap-southeast-1a**, sau đó chọn **Public Subnet 1**
    - Tick chọn **ap-southeast-1b**, sau đó chọn **Public Subnet 2**
![ILB](../../../images/7-3/04.png?width=50pc)

5. Ở phần **Security groups** chọn **InternetFacing-LB-SG**. Ở phần **Listeners and routing**, **default action** chọn **WebTierTargetGroup**. Lướt xuống dưới cùng và click **Create load balancer**.
![ILB](../../../images/7-3/05.png?width=50pc)

6. Hoàn thành tạo load balancer cho app tier.
![ILB](../../../images/7-3/06.png?width=50pc)