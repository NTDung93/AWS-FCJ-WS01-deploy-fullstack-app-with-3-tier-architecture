---
title : "Tạo NAT Gateway"
date :  "`r Sys.Date()`" 
weight : 7
chapter : false
pre : " <b> 2.7 </b> "
---

#### Tạo NAT Gateway

1. Trong giao diện VPC, click chọn **NAT gateways** ở sidebar, sau đó chọn **Create NAT gateway**
![Create NAT gateway](/workshop01-AWS-FCJ-2024/images/2-7/01.png?width=50pc)

2. Trong giao diện create NAT gateway
    - **Name** nhập **`nat-gw-01`**
    - **Subnet** chọn **Public Subnet 1**
    - **EIP** click **Allocate Elastic IP**
    - Click **Create NAT gateway**
![Create NAT gateway](/workshop01-AWS-FCJ-2024/images/2-7/02.png?width=50pc)

3. Hoàn thành tạo NAT gateway trong **Public Subnet 1** của AZ đầu tiên
![Create NAT gateway](/workshop01-AWS-FCJ-2024/images/2-7/03.png?width=50pc)

4. Lặp lại các bước để tạo NAT gateway trong **Public Subnet 2** của AZ thứ hai
![Create NAT gateway](/workshop01-AWS-FCJ-2024/images/2-7/04.png?width=50pc)

5. Hoàn thành tạo NAT gateway trong **Public Subnet 2** của AZ thứ hai
![Create NAT gateway](/workshop01-AWS-FCJ-2024/images/2-7/05.png?width=50pc)