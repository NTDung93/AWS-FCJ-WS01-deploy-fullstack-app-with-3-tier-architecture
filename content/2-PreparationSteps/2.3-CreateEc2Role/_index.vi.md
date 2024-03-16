---
title : "Tạo IAM EC2 Role"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---

#### Tạo IAM EC2 Role

1. Tìm dịch vụ **IAM** trên thanh tìm kiếm và click chọn
![IAM](/workshop01-AWS-FCJ-2024/images/2-3/01.png?width=50pc)
2. Chọn **Roles** ở sidebar, sau đó chọn **Create role**
![Create role](/workshop01-AWS-FCJ-2024/images/2-3/02.png?width=50pc)
3. Trong giao diện tạo Role, ở bước **Select trusted entity**:
    - **Trusted entity type** chọn **AWS Service**
    - **Use case** chọn **EC2**
    - Click **Next**
![Select trusted entity](/workshop01-AWS-FCJ-2024/images/2-3/03.png?width=50pc)
4. Trong giao diện tạo Role, ở bước **Add permissions**:
    - Tìm, chọn role **AmazonSSMManagedInstanceCore** (cho phép kết nối an toàn tới instance mà không cần SSH key) và **AmazonS3ReadOnlyAccess** (cho phép instance downloadn code từ S3)
    - Chọn **Next**
![Add permissions](/workshop01-AWS-FCJ-2024/images/2-3/04.png?width=50pc)
5. Trong giao diện tạo Role, ở bước **Name, review, and create**:
    - Điền tên của role là **`ec2role`**
    - Kiểm tra lại 3 steps vừa setup
    - Chọn **Create role**
![Name, review, and create](/workshop01-AWS-FCJ-2024/images/2-3/05.png?width=50pc)
![Name, review, and create](/workshop01-AWS-FCJ-2024/images/2-3/06.png?width=50pc)
![Name, review, and create](/workshop01-AWS-FCJ-2024/images/2-3/07.png?width=50pc)
6. Hoàn thành tạo role
![Role created](/workshop01-AWS-FCJ-2024/images/2-3/08.png?width=50pc)