---
title : "Tạo Internet Gateway"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3.3 </b> "
---

#### Tạo Internet Gateway

1. Trong giao diện **VPC**

   - Chọn **Internet Gateways**
   - Chọn **Create internet gateway**

![Create VPC](/images/3/0001.png?featherlight=false&width=90pc)

2. Thực hiện cấu hình

   - **Name tag**, nhập **```Internet Gateway```**
   - Chọn **Create internet gateway**

![Create VPC](/images/3/0002.png?featherlight=false&width=90pc)

3. Hoàn thành tạo **Internet Gateway**

![Create VPC](/images/3/0003.png?featherlight=false&width=90pc)


4. Thực hiện **Attach VPC**

   - Chọn **Actions**
   - Chọn **Attach to VPC**
   - Chọn **ASG**, VPC ID sẽ được tự động điền.
   - Chọn **Attach intermet gateway**

![Create VPC](/images/3/0004.png?featherlight=false&width=90pc)

5. Khi attach thành công **State** internet gateway sẽ chuyển sang **Attached**

![Create VPC](/images/3/0005.png?featherlight=false&width=90pc)
