---
title : "Sử dụng Reachability Analyzer"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4.4 </b> "
---

#### Sử dụng Reachability Analyzer

![Create VPC](/images/0000.png?featherlight=false&width=90pc)

1. Truy cập vào giao diện **VPC**

   - Chọn **Reachability Analyzer**
   - Chọn **Create and analyze path**

![Create VPC](/images/14/0001.png?featherlight=false&width=90pc)

2. Thực hiện **Path Configuration**

   - Name tag, nhập **```EC2 private with EC2 Public```**
   - Đối với **Source type**, chọn **Instance**
   - Chọn **source** là **EC2 Public**
   - Đối với **Destination type**, chọn **Instance**
   - Đối với **Destination**, chọn **EC2 Private**
   - Các thông số còn lại để mặc định. 
   - Chọn **Create and analyze path**

![Create VPC](/images/14/0002.png?featherlight=false&width=90pc)

3. Đợi 5 phút sau sẽ hiển trạng thái **Reachable**

![Create VPC](/images/14/0003.png?featherlight=false&width=90pc)

4. Sau đó, xem path details.

![Create VPC](/images/14/0004.png?featherlight=false&width=90pc)

5. Xem reverse path details.

![Create VPC](/images/14/0005.png?featherlight=false&width=90pc)

