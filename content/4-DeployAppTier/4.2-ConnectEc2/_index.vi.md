---
title : "Kết nối tới EC2 instance"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 4.2 </b> "
---

#### Kết nối tới EC2 instance

1. Trên giao diện các EC2 instances, chọn instance vừa tạo và bấm **Connect**
![connect ec2](/workshop01-AWS-FCJ-2024/images/4-2/01.png?width=50pc)

2. Chuyển qua tab **Session Manager** và click Connect
![connect ec2](/workshop01-AWS-FCJ-2024/images/4-2/02.png?width=50pc)

3. Connect thành công vào instance
![connect ec2](/workshop01-AWS-FCJ-2024/images/4-2/03.png?width=50pc)

4. Chạy lệnh **`sudo -su ec2-user`** để chuyển từ user sang ec2-user, và có những quyền quản trị root đối với instance
![connect ec2](/workshop01-AWS-FCJ-2024/images/4-2/04.png?width=50pc)

5. Tiếp đó chạy lệnh **`ping 8.8.8.8`** (IP address của Google’s DNS server) để test xem instance của ta có thể kết nối với internet bên ngoài thông qua igw không
![connect ec2](/workshop01-AWS-FCJ-2024/images/4-2/05.png?width=50pc)