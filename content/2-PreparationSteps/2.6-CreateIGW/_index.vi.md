---
title : "Tạo Internet Gateway"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 2.6 </b> "
---

#### Tạo Internet Gateway

1. Ở giao diện VPC, chọn **Internet gateways** ở sidebar, sau đó chọn **Create internet gateway**
![Create internet gateway](/workshop01-AWS-FCJ-2024/images/2-6/01.png?width=50pc)

2. Ở giao diện Create internet gateway
    - **Name tag** nhập **`workshop-01-igw`**
    - Click **Create internet gateway**
![Create internet gateway](/workshop01-AWS-FCJ-2024/images/2-6/02.png?width=50pc)

3. Ở phần detail của IGW vừa tạo
    - Chọn **Actions**
    - Chọn **Attach to VPC**
![Create internet gateway](/workshop01-AWS-FCJ-2024/images/2-6/03.png?width=50pc)

4. Ở phần **Attach to VPC**
    - Chọn VPC **my-vpc**
    - Chọn **Attach internet gateway**
![Create internet gateway](/workshop01-AWS-FCJ-2024/images/2-6/04.png?width=50pc)

5. Hoàn thành tạo và gán IGW với VPC
![Create internet gateway](/workshop01-AWS-FCJ-2024/images/2-6/05.png?width=50pc)