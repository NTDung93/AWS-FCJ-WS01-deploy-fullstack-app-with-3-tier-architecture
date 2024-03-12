---
title : "Tạo môi trường VPN"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 5.1 </b> "
---

#### Tạo môi trường VPN

Trước khi khởi tạo và cấu hình kết nối VPN Site to Site, chúng ta cần tạo môi trường giả lập chi nhánh (ASG VPN) như kiến trúc bên dưới.

![VPN](/images/5-CreateVPNenv/vpn.png?featherlight=false&width=90pc)

#### Nội dung

1. [Tạo ASG VPN VPC, 2 subnet, Internet Gateway](5.1.1-createvpnvpc/)
2. [Khởi tạo EC2 trên ASG VPN VPC](5.1.2-createec2vpn/)