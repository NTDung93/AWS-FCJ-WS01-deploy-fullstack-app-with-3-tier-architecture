---
title : "Tùy chỉnh AWS VPN Tunnel"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5.2.5 </b> "
---

#### Tùy chỉnh AWS VPN Tunnel

1. Truy cập vào giao diện **VPC**

   - Chọn **Site-to-Site VPN connections**
   - Chọn **VPN** vừa tạo.
   - Chọn **Actions**
   - Chọn **Modify VPN tunnel options**

![Create VPC](/images/13/00023.png?featherlight=false&width=90pc)

2. Chọn **VPN Tunnel outside IP address**

![Create VPC](/images/13/00024.png?featherlight=false&width=90pc)

3. Chọn **Confirm UP tunnel modification** và các thông số còn lại mặc định.

![Create VPC](/images/13/00025.png?featherlight=false&width=90pc)

4. Đối với **Tunnel activity log**, chọn **Enable**

   - Chọn **Amazon CloudWatch log group** (nếu chưa có bạn có thể tạo trong CloudWatch)
   - Đối với **Output format**, chọn **text**
   - Chọn **Save changes**

![Create VPC](/images/13/00026.png?featherlight=false&width=90pc)

5. Truy cập vào **CloudWatch**

   - Chọn **Log groups**
   - Chọn **Log streams**
   - Chọn một stream.

![Create VPC](/images/13/00027.png?featherlight=false&width=90pc)

6. Vào xem **Log events**

![Create VPC](/images/13/00028.png?featherlight=false&width=90pc)

7. Bạn thực hiện tương tự với tunnel còn lại.

![Create VPC](/images/13/00029.png?featherlight=false&width=90pc)

8. Phải đảm bảo cả 2 tunnel đã **UP**

![Create VPC](/images/13/00030.png?featherlight=false&width=90pc)

