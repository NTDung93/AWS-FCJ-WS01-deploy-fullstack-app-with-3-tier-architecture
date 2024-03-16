---
title : "Tạo các Subnet"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 2.5 </b> "
---

#### Tạo các Subnet"

1. Trong giao diện VPC, chọn **Subnets** ở side bar và chọn **Create subnet**
![Create subnet](/workshop01-AWS-FCJ-2024/images/2-5/01.png?width=50pc)

2. Trong giao diện **Create subnet**, chọn VPC vừa tạo là **my-vpc**
![Create subnet](/workshop01-AWS-FCJ-2024/images/2-5/02.png?width=50pc)

3. Sau khi chọn VPC sẽ xuất hiện phần **Subnet settings**
    - **Subnet name**, nhập **`Public Subnet 1`**
    - **Availability Zone**, chọn AZ Singapore **ap-southeast-1a**
    - **IPv4 CIDR block**, nhập **`10.10.1.0/24`** 
    - Chọn **Create subnet**
![Create subnet](/workshop01-AWS-FCJ-2024/images/2-5/03.png?width=50pc)

4. Hoàn thành tạo Subnet
![Subnet created](/workshop01-AWS-FCJ-2024/images/2-5/04.png?width=50pc)

5. Thực hiện tương tự các bước trên, tạo thêm các subnet
    - **`Public subnet 2`** với CIDR là **`10.10.2.0/24`** và AZ **ap-southeast-1b**.
![Subnet created](/workshop01-AWS-FCJ-2024/images/2-5/05.png?width=50pc)

    - **`Private subnet 1`** với CIDR là **`10.10.3.0/24`** và AZ **ap-southeast-1a**.
![Subnet created](/workshop01-AWS-FCJ-2024/images/2-5/06.png?width=50pc)

    - **`Private subnet 2`** với CIDR là **`10.10.4.0/24`** và AZ **ap-southeast-1b**.
![Subnet created](/workshop01-AWS-FCJ-2024/images/2-5/07.png?width=50pc)

    - **`Private DB Subnet 1`** với CIDR là **`10.10.5.0/24`** và AZ **ap-southeast-1a**.
![Subnet created](/workshop01-AWS-FCJ-2024/images/2-5/08.png?width=50pc)

    - **`Private DB Subnet 2`** với CIDR là **`10.10.6.0/24`** và AZ **ap-southeast-1b**.
![Subnet created](/workshop01-AWS-FCJ-2024/images/2-5/09.png?width=50pc)

    - Hoàn thành tạo 6 subnets.
![Subnet created](/workshop01-AWS-FCJ-2024/images/2-5/10.png?width=50pc)

#### Cho phép tự động cấp phát public IP address cho 2 public subnet
6. Trong giao diện Subnets, chọn **Public Subnet 1**, chọn **Actions** và chọn **Edit subnet settings**
![Edit subnet settings](/workshop01-AWS-FCJ-2024/images/2-5/11.png?width=50pc)

7. Tick chọn **Enable auto-assign public IPv4 address**, sau đó chọn **Save**
![Edit subnet settings](/workshop01-AWS-FCJ-2024/images/2-5/12.png?width=50pc)
![Edit subnet settings](/workshop01-AWS-FCJ-2024/images/2-5/13.png?width=50pc)

8. Lặp lại các bước trên để apply cho **Public subnet 02**
![Edit subnet settings](/workshop01-AWS-FCJ-2024/images/2-5/14.png?width=50pc)

9. Vào lại **Your VPCs** và xem phần **Resource map** của **my-vpc**
![Resource map](/workshop01-AWS-FCJ-2024/images/2-5/15.png?width=50pc)