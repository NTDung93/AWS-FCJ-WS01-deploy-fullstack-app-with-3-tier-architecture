---
title : "Tạo Route Table"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 3.4 </b> "
---

#### Tạo Route Table định tuyến đi ra ngoài internet thông qua Internet Gateway.


1. Trong giao diện **VPC**

   - Chọn **Route Tables**
   - Chọn **Create route table**

![Create VPC](/images/4/0001.png?featherlight=false&width=90pc)

2. Tiến hành cấu hình **Route table**

   - **Name**, nhập **```Route table-Public```**
   - **VPC**, chọn **ASG** VPC. VPC id sẽ được tự động điền vào.
   - Chọn **Cretae route table**

![Create VPC](/images/4/0002.png?featherlight=false&width=90pc)

3. Hoàn thành tạo **Route table**

![Create VPC](/images/4/0003.png?featherlight=false&width=90pc)

4. Thực hiện **Edit route**

   - Chọn **Actions**
   - Chọn **Edit routes**

![Create VPC](/images/4/0004.png?featherlight=false&width=90pc)

5. Trong giao diện **Edit routes**

   - Chọn **Add route**
   - Điền phần **Destination CIDR** : **```0.0.0.0/0```** đại diện cho Internet.
   - Trong phần **Target**  chọn **Internet Gateway**, sau đó chọn **Internet Gateway** chúng ta đã tạo. **Internet Gateway ID** sẽ được tự động điền.
   - Chọn **Save changes**

![Create VPC](/images/4/0005.png?featherlight=false&width=90pc)

6. Hoàn thành và kiểm tra lại **Routes**

![Create VPC](/images/4/0006.png?featherlight=false&width=90pc)

7. Đảm bảo **Route table - Public** đang được chọn.

   - Chọn **subnet associations**
   - Chọn **Edit subnet associations**

![Create VPC](/images/4/0007.png?featherlight=false&width=90pc)

8. Trong bước **Edit subnet associations**

   - Mở rộng cột **Subnet ID** bằng cách kéo thanh ngăn sang phải.
   - Chọn đúng **2 subnet public** chúng ta đã tạo.

![Create VPC](/images/4/0008.png?featherlight=false&width=90pc)

9.  Chọn **Save associations**

![Create VPC](/images/4/0009.png?featherlight=false&width=90pc)

10. Hoàn thành và kiểm tra lại **Subnet associations**

![Create VPC](/images/4/00010.png?featherlight=false&width=90pc)
