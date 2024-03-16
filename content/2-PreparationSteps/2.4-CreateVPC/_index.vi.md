---
title : "Tạo mới VPC"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 2.4 </b> "
---

#### Tạo mới VPC

1. Truy cập trang web AWS và tìm **VPC**
![VPC](/workshop01-AWS-FCJ-2024/images/2-4/01.png?width=50pc)

2. chọn **Your VPCs**, rồi chọn **Create VPC**
![Create VPC](/workshop01-AWS-FCJ-2024/images/2-4/02.png?width=50pc)

3. Tiến hành các bước tạo VPC:
    - **Resource**, chọn **VPC only**
    - **Name tag**, nhập **`my-vpc`**
    - **IPv4 CIDR**, nhập **`10.10.0.0/16`**
![Create VPC](/workshop01-AWS-FCJ-2024/images/2-4/03.png?width=50pc)

4. chọn **Create VPC**
![Create VPC](/workshop01-AWS-FCJ-2024/images/2-4/04.png?width=50pc)

5. Hoàn thành tạo VPC
![VPC created](/workshop01-AWS-FCJ-2024/images/2-4/05.png?width=50pc)

6. Xem chi tiết VPC vừa tạo, vào Edit VPC setting:
    - Check 2 option **Enable DNS resolution** và **Enable DNS hostnames**
    - Nhấn button **Save**
![VPC created](/workshop01-AWS-FCJ-2024/images/2-4/06.png?width=50pc)     