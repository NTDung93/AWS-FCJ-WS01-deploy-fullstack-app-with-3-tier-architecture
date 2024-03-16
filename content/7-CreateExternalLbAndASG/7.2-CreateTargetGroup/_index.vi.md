---
title : "Tạo Target group cho Web Tier"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 7.2 </b> "
---
#### Tạo Target group
1. Tại giao diện EC2, chọn **Target Groups** ở nhóm **Load balancing** ở sidebar, sau đó chọn **Create target group**
![Target group](/workshop01-AWS-FCJ-2024/images/5-2/01.png?width=50pc)

2. Tại giao diện tạo target group:
    - **Target group name** điền **`WebTierTargetGroup`**
    - **Protocol: HTTP, Port: 80** (đây là port mà nginx listen)
    - **VPC** chọn **my-vpc**
    - **Health check path** điền **`/health`**
    - Kéo xuống dưới cùng click **Next** rồi click **Create target group**
![Target group](/workshop01-AWS-FCJ-2024/images/7-2/02.png?width=50pc)
![Target group](/workshop01-AWS-FCJ-2024/images/7-2/03.png?width=50pc)

1. Hoàn thành tạo target group
![Target group](/workshop01-AWS-FCJ-2024/images/7-2/04.png?width=50pc)
