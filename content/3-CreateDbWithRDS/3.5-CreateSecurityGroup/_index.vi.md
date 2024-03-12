---
title : "Tạo Security Group"
date :  "`r Sys.Date()`" 
weight : 5 
chapter : false
pre : " <b> 3.5 </b> "
---

#### Tạo Security Group

#### Tạo Security Group cho máy chủ nằm trong Public subnet

1. Trong giao diện **VPC**

   - Chọn **Security Group**
   - Chọn **Cretae security group**

![Create VPC](/images/5/0001.png?featherlight=false&width=90pc)


2. Thực hiện cấu hình **Security group**

   - **Security Group name**, nhập **```Public subnet - SG```**
   - **Description**, nhập **Allow SSH and Ping for servers in public subnet.**
   - Chọn **ASG** VPC 

![Create VPC](/images/5/0002.png?featherlight=false&width=90pc)

3. Thực hiện cấu hình **Inbound rules**

   - Trong **Inbound rules**, click **Add rule**.

   - Chọn **Type**: **SSH** và **Source**: **My IP**. **My IP** đại diện cho 1 địa chỉ public IPv4 bạn đang sử dụng(sẽ thay đổi khi bạn đổi mạng)

   - Chọn  **Add rule** để thêm 1 rule mới.

   - Chọn **Type**: **All ICMP - IPv4** và **Source**: **Anywhere**. Cho phép ping từ bất kì địa chỉ IP nào.

![Create VPC](/images/5/0003.png?featherlight=false&width=90pc)

4. Kiểm tra **Outbound rules** và chọn **Cretae security group**

![Create VPC](/images/5/0004.png?featherlight=false&width=90pc)

5. Hoàn thành tạo security group cho máy chủ nằm trong Public subnet

![Create VPC](/images/5/0005.png?featherlight=false&width=90pc)

#### Tạo Security Group cho máy chủ nằm trong Private subnet

6. Trong giao diện **VPC**

   - Chọn **Security Groups**
   - Chọn **Create security group**

![Create VPC](/images/5/0006.png?featherlight=false&width=90pc)

7. Thực hiện cấu hình **Security group**

   - Trong phần **Security group name** điền **Private subnet - SG**

   - Trong phần **Description** điền **Allow SSH and Ping for servers in private subnet.**

   - chọn **VPC**, lựa chọn **VPC** có tên **ASG**.

![Create VPC](/images/5/0007.png?featherlight=false&width=90pc)

8. Thực hiện cấu hình **Inbound rules**

   - Trong Inbound rules, chọn  Add rule.

   - Chọn **Type**: **SSH** và để nguyên **Source**: **Custom**. Chọn  vào search box và chọn **Public subnet SG**.Lựa chọn này cho phép tất cả những máy chủ được gán **Public subnet SG** được **SSH** vào các máy chủ được gán **Private subnet SG**.

![Create VPC](/images/5/0008.png?featherlight=false&width=90pc)

9. Chọn **Add rule** để thêm 1 rule mới.

   - Chọn **Type**: **All ICMP IPv4** và **Source**: **Anywhere**. Cho phép ping từ bất kì địa chỉ IP nào.
   - 
![Create VPC](/images/5/0009.png?featherlight=false&width=90pc)

10.  Chọn **Create security group**


![Create VPC](/images/5/00010.png?featherlight=false&width=90pc)

11.  Như vậy chúng ta đã tạo được **2 Security Group** cho các máy chủ nằm trong **public subnet và private subnet.**

   - Tiếp theo chúng ta sẽ tiến hành tạo 2 máy chủ EC2.

![Create VPC](/images/5/00011.png?featherlight=false&width=90pc)