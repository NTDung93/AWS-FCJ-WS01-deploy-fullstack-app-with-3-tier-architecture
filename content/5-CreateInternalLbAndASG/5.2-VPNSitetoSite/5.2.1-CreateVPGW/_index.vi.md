---
title : "Tạo Virtual Private Gateway"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 5.2.1 </b> "
---

#### Tạo Virtual Private Gateway

1. Truy cập vào **VPC**

   - Chọn **Virtual Private Gateway**
   - Chọn **Create Virtual Private Gateway**

![Create VPC](/images/11/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **Create Virtual Private Gateway**

   - **Name tag**, nhập **```VPN Gateway```**
   - Chọn **Amazon default ASN**
   - Chọn **Create virtual private gateway**

![Create VPC](/images/11/0002.png?featherlight=false&width=90pc)

3. Chúng ta cần thực hiện **Attach to VPC**

   - Chọn **Actions**
   - Chọn **Attach to VPC**

![Create VPC](/images/11/0003.png?featherlight=false&width=90pc)


4. Trong giao diện **Attach to VPC**

   - Chọn **VPC ASG.**
   - Chọn **Attach to VPC**

![Create VPC](/images/11/0004.png?featherlight=false&width=90pc)

5. Hoàn tất và xem **State** là **Attached**

![Create VPC](/images/11/0005.png?featherlight=false&width=90pc)