---
title : "Tạo Customer Gateway"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 5.2.2 </b> "
---

#### Tạo Customer Gateway

1. Truy cập vào **VPC**

   - Chọn **Customer Gateways**
   - Chọn **Create Customer Gateway**

![Create VPC](/images/12/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **Create Customer Gateway**

   - **Name tag**, nhập **```Customer Gateway```**
   - **IP address**, nhập **public IP address** của máy chủ **EC2 Customer Gateway**.
   - Chọn **Create Customer Gateway**

![Create VPC](/images/12/0002.png?featherlight=false&width=90pc)

3. Đợi khoảng 5 phút sau, hoàn tất tạo **Customer Gateway**

![Create VPC](/images/12/0003.png?featherlight=false&width=90pc)

{{% notice tip %}}
Lưu ý: theo như mô hình kiến trúc, Customer Gateway sẽ nằm ở VPC trên môi trường onpremise. Hiện tại chúng ta đang làm là khai báo với AWS rằng chúng ta sẽ có 1 Customer Gateway với địa chỉ IP public là địa chỉ public của EC2 instance : Customer Gateway nằm trong ASG VPN VPC
{{% /notice %}}

