---
title : "Tạo EC2 Instance"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 5.1.2 </b> "
---

#### Tạo EC2 để làm Customer Gateway

1. Truy cập vào **VPC**

   - Chọn **Security Group**
   - Chọn **Create security group**

![Create VPC](/images/10/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **Create security group**

   - **Security group name**, nhập **```VPN Public -SG```**
   - Trong phần **Description** điền **Allow IPSec, SSH and Ping for servers in public subnet**.
   - **VPC**, chọn **ASG VPN** vpc

![Create VPC](/images/10/0002.png?featherlight=false&width=90pc)

3. Tiến hành cấu hình **Inbound rules**

   - Chọn **Add rule**
   - Chọn **Type**: **SSH** và **Source**: **My IP**. My IP đại diện cho 1 địa chỉ public IPv4 bạn đang sử dụng.
   - Click **Add rule** để thêm 1 rule mới.
   - Chọn **Type**: **All ICMP IPv4** và **Source**: **Anywhere**. Cho phép ping từ bất kì địa chỉ IP nào.
   - Click **Add rule** để thêm 1 rule mới.
   - Chọn **Type**: **Custom UDP** , **Port:400** và **Source** : **Anywhere**.
   - Click **Add rule** để thêm 1 rule mới.
   - Chọn **Type**: **Custom TCP** , **Port:500** và **Source** : **Anywhere**

![Create VPC](/images/10/0003.png?featherlight=false&width=90pc)

4. Kiểm tra **Outbound rules** và chọn **Create security group**

![Create VPC](/images/10/0004.png?featherlight=false&width=90pc)

5. Hoàn thành tạo **VPN Public - SG**. Như vậy chúng ta đã tạo được Security Group. Tiếp theo chúng ta sẽ tiến hành tạo máy chủ EC2 đóng vai trò Customer Gateway.
   
![Create VPC](/images/10/0005.png?featherlight=false&width=90pc)

![Create VPC](/images/10/0005.png?featherlight=false&width=90pc)

6. Truy cập vào **EC2**

   - Chọn **Instances**
   - Chọn **Launch instances**

![Create VPC](/images/10/0006.png?featherlight=false&width=90pc)

7. Trong giao diện **Launch instances**

   - **Name**, nhập **```Customer Gateway instance```**

![Create VPC](/images/10/0007.png?featherlight=false&width=90pc)

8. Thực hiện chọn **AMI**

   - Chọn **Quick Start**
   - Chọn **Amazon Linux**
   - Chọn **AMI**

![Create VPC](/images/10/0008.png?featherlight=false&width=90pc)

9. Phần chọn **Instance type** và chọn **Key pair**: **aws-keypair**(keypair đã tạo chung với các instance)

![Create VPC](/images/10/0009.png?featherlight=false&width=90pc)

10. Thực hiện cấu hình **Network**

    - **VPC**, chọn **ASG VPN** vpc
    - **Subnet**, chọn **VPN Public**
    - **Auto-assign public IP**, chọn **Enable**
    - **Firewall**, chọn **Select existing security group**
    - Chọn **VPN Public - SG**
    - Kiểm tra lại và chọn **Launch instance**

![Create VPC](/images/10/00010.png?featherlight=false&width=90pc)

11. Hoàn tất tạo **EC2 instance**

    - Chọn **View all instances**

![Create VPC](/images/10/00011.png?featherlight=false&width=90pc)

12. Xem chi tiết **Customer Gateway instance**

![Create VPC](/images/10/00012.png?featherlight=false&width=90pc)
