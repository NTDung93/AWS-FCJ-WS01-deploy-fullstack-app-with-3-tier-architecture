---
title : "Tạo VPC cho VPN"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 5.1.1 </b> "
---

#### Tạo môi trường VPN

1. Truy cập giao diện **VPC**

   - Chọn **Yours VPC**
   - Chọn **Create VPC**

![Create VPC](/images/9/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **Cretae VPC**

   - **Resource**, chọn **VPC only**
   - **Name**, nhập **```ASG VPN```**
   - **IPv4 CIDR block**, nhập **```10.11.0.0/16```**

![Create VPC](/images/9/0002.png?featherlight=false&width=90pc)

3. Chọn **Create VPC**

![Create VPC](/images/9/0003.png?featherlight=false&width=90pc)

4. Tạo VPC thành công

![Create VPC](/images/9/0004.png?featherlight=false&width=90pc)

5. Truy cập giao diện **VPC**

   - Chọn **Subnets**
   - Chọn **Create subnet**

![Create VPC](/images/9/0005.png?featherlight=false&width=90pc)

6. Trong giao diện **Create subnet**

   - Chọn **ASG VPN** vpc

![Create VPC](/images/9/0006.png?featherlight=false&width=90pc)


7. Trong giao diện **Subnet settings**

   - **Subnet name**, nhập **```VPN Public```**
   - Lựa chọn **Availability Zone**: **ap-southeast-1a**
   - Chọn **IPv4 CIDR block** là **10.11.1.0/24** theo kiến trúc mô tả

![Create VPC](/images/9/0007.png?featherlight=false&width=90pc)

8. Tạo thành công **VPN Public**

![Create VPC](/images/9/0008.png?featherlight=false&width=90pc)

9. Trong giao diện **VPC**

   - Chọn **Subnets**
   - Chọn **VPN Public**
   - Chọn **Actions**
   - Chọn **Edit subnet settings**

![Create VPC](/images/9/0009.png?featherlight=false&width=90pc)

10. Thực hiện **Auto-assign IP settings**

    - Chọn **Enable auot-assign public IPv4 address**
    - Chọn **Save**

![Create VPC](/images/9/00010.png?featherlight=false&width=90pc)

11. Cấp phát IP thành công

![Create VPC](/images/9/00011.png?featherlight=false&width=90pc)

12. Trong giao diện **VPC**

    - Chọn **Internet Gateway**
    - Chọn **Create internet gateway**

![Create VPC](/images/9/00012.png?featherlight=false&width=90pc)

13. Trong giao diện **Create internet gateway**

    - **Name tag**, nhập **```Internet Gateway VPN```**
    - Chọn **Create internet gateway**

![Create VPC](/images/9/00013.png?featherlight=false&width=90pc)

14. Sau khi tạo **Internet Gateway VPN** thành công và **State** là **Detached**. Tiếp theo chúng ta cần Attach Internet Gateway vào VPC ASG VPN.

    - Chọn **Actions**
    - Chọn **Attach to VPC**

![Create VPC](/images/9/00014.png?featherlight=false&width=90pc)

15. Chọn **VPC ASG VPN**, VPC ID sẽ được tự động điền.

    - Chọn **Attach Internet Gateway**

![Create VPC](/images/9/00015.png?featherlight=false&width=90pc)

16. **Attach** thành công khi **State** là **Attached**

![Create VPC](/images/9/00016.png?featherlight=false&width=90pc)

17. Tiếp theo chúng ta cần tạo Route Table định tuyến đi ra ngoài internet thông qua Internet Gateway. Trong giao diện **VPC**

    - Chọn **Route Tables**
    - Chọn **Create route table**

![Create VPC](/images/9/00017.png?featherlight=false&width=90pc)

18. Trong giao diện **Cretae route table**

    - **Name**, nhập **```Route table VPN - Public```**
    - Chọn **VPC** có tên **ASG VPN** , **VPC id** sẽ được tự động điền vào.
    - Chọn **Create route table**

![Create VPC](/images/9/00018.png?featherlight=false&width=90pc)

![Create VPC](/images/9/00019.png?featherlight=false&width=90pc)


19. Tạo route table thành công. Trong giao diện **Route table VPN - Public**

    - Chọn **Route**
    - Chọn **Edit route**

![Create VPC](/images/9/00020.png?featherlight=false&width=90pc)

20. Trong giao diện **Edit routes**

    - Chọn **Add route**
    - Điền phần **Destination CIDR** : **0.0.0.0/0** đại diện cho Internet.
    - Trong phần **Target** chọn **Internet Gateway**, sau đó chọn **Internet Gateway VPN** chúng ta đã tạo. **Internet Gateway ID** sẽ được tự động điền.
    - Chọn **Save changes**

![Create VPC](/images/9/00021.png?featherlight=false&width=90pc)

![Create VPC](/images/9/00022.png?featherlight=false&width=90pc)

21. Hoàn thành và kiểm tra route

22. Trong giao diện **Route table VPN - Public**

    - Chọn **Subnet associations**
    - Chọn **Edit subnet associations**

![Create VPC](/images/9/00023.png?featherlight=false&width=90pc)


23. Trong giao diện **Edit subnet associations**

    - Mở rộng cột Subnet ID bằng cách kéo thanh ngăn sang phải.
    - Chọn **subnet VPN Public**.
    - Chọn **Save associations**

![Create VPC](/images/9/00024.png?featherlight=false&width=90pc)

24.  Hoàn thành và kiểm tra lại **Routes**

![Create VPC](/images/9/00025.png?featherlight=false&width=90pc)
