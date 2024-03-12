---
title : "Tạo NAT Gateway"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 4.3 </b> "
---

#### Tạo NAT Gateway

#### Tạo một địa chỉ Elastic IP

1. Truy cập **EC2**

   - Chọn **Elastic IPs**
   - Chọn **Allocate Elastic IP address**


![Create VPC](/images/8/0001.png?featherlight=false&width=90pc)


2. Trong giao diện **Allocate Elastic IP address**

   - **Public IPv4 address pool**, chọn **Amazon's pool of IPv4 addresses**
   - Chọn **Allocate**

![Create VPC](/images/8/0002.png?featherlight=false&width=90pc)

3. Chúng ta vừa tạo thành công một địa chỉ **Public IP Address**

![Create VPC](/images/8/0003.png?featherlight=false&width=90pc)

4. Truy cập vào **VPC**

   - Chọn **NAT Gateways**
   - **Create NAT gateway**

![Create VPC](/images/8/0004.png?featherlight=false&width=90pc)

5. Trong giao diện **NAT gateway**

   - **Name**, nhập **```NAT gateway```**
   - **Subnet**, chọn **Public subnet 2**
   - **Connectivity type**, chọn **Public**
   - **Elastic IP allocation ID**, chọn **Elastic IP** vừa tạo.

![Create VPC](/images/8/0005.png?featherlight=false&width=90pc)

6. Chọn **Create NAT gateway**

![Create VPC](/images/8/0006.png?featherlight=false&width=90pc)

7. Thành công tạo **NAT gateway**


![Create VPC](/images/8/0007.png?featherlight=false&width=90pc)


#### Tạo Route table - Private và gáng vào các private subnet.

8. Trong giao diện **VPC**

   - Chọn **Route Tables**
   - Chọn **Create route table**

![Create VPC](/images/8/0008.png?featherlight=false&width=90pc)

9. Trong giao diện **Route table**

   - **Name**, nhập **```Route table - Private```**
   - **VPC**, chọn **ASG** vpc
   - Chọn **Cretae route table**

![Create VPC](/images/8/0009.png?featherlight=false&width=90pc)

![Create VPC](/images/8/00010.png?featherlight=false&width=90pc)

10.  Hoàn thành tạo **Route table - Private**



![Create VPC](/images/8/00011.png?featherlight=false&width=90pc)

11. Trong giao diện **Route table - Private**

    - Chọn **Subnet Associations**
    - Chọn **Edit subnet associations**

![Create VPC](/images/8/00012.png?featherlight=false&width=90pc)

12. Trong giao diện **Edit subnet associations**

     - Chọn 2 private subnet
     - Chọn **Save associations**

![Create VPC](/images/8/00013.png?featherlight=false&width=90pc)

13. Trong giao diện **Route table - Private**


     - Chọn **Routes**
     - Chọn **Edit routes**

![Create VPC](/images/8/00014.png?featherlight=false&width=90pc)

14. Trong giao diện **Edit routes**


     - Chọn **Add route**
     - Chọn **Destination**: **0.0.0.0/0**
     - **Target**: **NAT Gateway**
     - Chọn **Save changes**

![Create VPC](/images/8/00015.png?featherlight=false&width=90pc)

![Create VPC](/images/8/00016.png?featherlight=false&width=90pc)

15. Kiểm tra lại **Routes**

![Create VPC](/images/8/00017.png?featherlight=false&width=90pc)

16. Kiểm tra ping amazon.com thành công từ EC2 Private.

```
ping amazon.com -c5
```

![Create VPC](/images/8/00018.png?featherlight=false&width=90pc)