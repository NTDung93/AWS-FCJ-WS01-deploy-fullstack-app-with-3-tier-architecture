---
title : "Tạo database subnet group"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 3.1 </b> "
---

#### Database subnet group là gì và tại sao chúng ta cần nó?
Database subnet group là một tập hợp các subnet mà bạn tạo ra trong VPC của bạn. Khi tạo một database instance, bạn cần phải chỉ định một database subnet group. Database subnet group phải chứa ít nhất một subnet trong mỗi AZ. Database subnet group đảm bảo rằng database instance có thể được triển khai trên nhiều AZ để có được tính sẵn sàng cao.

#### Tạo database subnet group
1. Tìm và truy cập vào dịch vụ **RDS**
![](/workshop01-AWS-FCJ-2024/images/3-1/01.png?width=50pc)

2. Chọn **Subnet groups** ở sidebar và click **Create DB subnet group**
![](/workshop01-AWS-FCJ-2024/images/3-1/02.png?width=50pc)

3. Ở giao diện tạo DB subnet group:
   - **Name** điền **`db-subnet-group`**
   - **Description** điền **`db-subnet-group`**
   - **VPC** chọn **my-vpc**
![](/workshop01-AWS-FCJ-2024/images/3-1/03.png?width=50pc)

4. Ở phần Add subnets:
   - **AZ** chọn **ap-southeast-1a** và **ap-southeast-1b**
   - **Subnets** chọn **Private DB Subnet 1** và **Private DB Subnet 2** (có thể vào lại list các subnet, xem CIDR của mỗi subnet để chọn cho đúng)
   - Sau đó click **Create**
![](/workshop01-AWS-FCJ-2024/images/3-1/04.png?width=50pc)

5. Hoàn thành tạo Subnet group.
![](/workshop01-AWS-FCJ-2024/images/3-1/05.png?width=50pc)