---
title : "Tạo Target group cho App Tier"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 5.2 </b> "
---
#### Tại sao cần tạo Target group?
- Vì khi đăng ký các ec2 instances vào target group, load balancer có thể theo dõi **health** của từng instance và **route traffic** tới **healthy instance** → ensure **high availability**. 	


#### Tạo Target group
1. Tại giao diện EC2, chọn **Target Groups** ở nhóm **Load balancing** ở sidebar, sau đó chọn **Create target group**
![Target group](/workshop01-AWS-FCJ-2024/images/5-2/01.png?width=50pc)

2. Tại giao diện tạo target group:
    - **Target group name** điền **`AppTierTargetGroup`**
    - **Protocol: HTTP, Port: 8080**
    - **VPC** chọn **my-vpc**
    - Kéo xuống dưới cùng click **Next** rồi click **Create target group**
![Target group](/workshop01-AWS-FCJ-2024/images/5-2/02.png?width=50pc)

3. Hoàn thành tạo target group
![Target group](/workshop01-AWS-FCJ-2024/images/5-2/03.png?width=50pc)