---
title : "Tạo Subnet"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 3.2 </b> "
---

#### Tạo subnet

1. Trong giao diện **VPC**

   - Chọn **Subnets**
   - Chọn **Create subnet**

![Create VPC](/images/2/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **Create subnet**

   - Chọn **ASG** VPC

![Create VPC](/images/2/0002.png?featherlight=false&width=90pc)

3. Thực hiện **subnet settings**

   - **Subnet name**, nhập **```Public Subnet 1```**
   - Chọn AZ **ap-southeast-1a**
   - **IPv4 CIDR block**, nhập **```10.10.1.0/24```** theo kiến trúc mô tả 
   - Chọn **Create subnet**

![Create VPC](/images/2/0003.png?featherlight=false&width=90pc)

4. Hoàn thành tạo **subnet**

![Create VPC](/images/2/0004.png?featherlight=false&width=90pc)

5. Thực hiện các bước tương tự tạo thêm các subnet

   - **Public subnet 2** với **CIDR** là **10.10.2.0/24** nằm trong **Availability Zone ap-southeast-1b**.

![Create VPC](/images/2/0005.png?featherlight=false&width=90pc)

   - **Private subnet 1** với **CIDR** là **10.10.3.0/24** nằm trong **Availability Zone ap-southeast-1a.**


![Create VPC](/images/2/0006.png?featherlight=false&width=90pc)

   - **Private subnet 2** với **CIDR** là **10.10.4.0/24** nằm trong **Availability Zone ap-southeast-1b**

![Create VPC](/images/2/0007.png?featherlight=false&width=90pc)


{{% notice tip %}}
Bạn có thể thấy có 2 cột là **Availability Zone** và **Availability Zone ID**. Để tránh việc tài nguyên EC2 được sử dụng **không đồng đều**, (chúng ta thường có xu hướng dùng AZ a để chạy **primary và AZ** b để stand by chẳng hạn) nên AWS sẽ gán ngẫu nhiên **Availability Zone vào Availability Zone ID**. Chúng ta có thể hiểu rằng Availability Zone là 1 dạng alias , còn Availability Zone ID mới chính là yếu tố định danh. Ví dụ ở hình trên Availability Zone ap-southeast-1a được gán Availability Zone ID là apse1-az2. Ở một AWS account khác , Availability Zone ap-southeast-1a có thể có Availability Zone ID là apse1-az1.
{{% /notice %}}

![Create VPC](/images/2/0008.png?featherlight=false&width=90pc)

#### Cho phép tự động cấp phát public ip address cho 2 public subnet.

{{% notice tip %}}
Một điểm đáng chú ý nữa là các subnet về cơ bản đều giống nhau, thông qua cấu hình route table và cấp phát public IP address mà chúng ta mới phân chia ra Public và Private Subnet.
{{% /notice %}}


6. Trong giao diện **VPC**

   - Chọn **Subnets**
   - Chọn **Public Subnet 1**
   - Chọn **Actions**
   - Chọn **Edit subnet settings**

![Create VPC](/images/2/0009.png?featherlight=false&width=90pc)


7. Trong mục **Auto-assign IP settings**

   - Chọn **Enable auto-assign publi IPv4 address**
   - Chọn **Save**

![Create VPC](/images/2/00010.png?featherlight=false&width=90pc)

8. Sau đó thực hiện tương tự với  **Public subnet 2.**

![Create VPC](/images/2/00011.png?featherlight=false&width=90pc)

![Create VPC](/images/2/00012.png?featherlight=false&width=90pc)


