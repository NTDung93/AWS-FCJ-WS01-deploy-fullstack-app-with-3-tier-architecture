---
title : "Các bước chuẩn bị"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

#### Tường lửa trong VPC

Trong phần này, chúng ta sẽ cùng tìm hiểu các tính năng bảo mật cơ bản trong Amazon VPC như tính năng tường lửa Security Group và Network Access Control Lists.

Một security group hoạt động như một tường lửa ảo cho EC2 Instance, giúp kiểm soát lưu lượng truy cập. Một Instance trong VPC có thể được gán tối đa 5 Security group do SG chỉ hoạt động ở tầng Instance mà không họat động ở tầng Subnet. 

{{% notice note %}}
Security groups hoạt động ở mức máy ảo, không phải ở mức subnet. Tuy nhiên, mỗi máy ảo trong một subnet có thể được gán với nhiều bộ Security group khác nhau.
{{% /notice %}}

Danh sách kiểm soát truy cập mạng (ACL) là lớp bảo mật tùy chọn cho VPC, nó hoạt động như một tường lửa để kiểm soát lưu lượng ra và vào cho một hoặc nhiều subnet. 
Ta có thể thiết lập network ACL với các rule tương tự như security groups, nhằm bổ sung thêm một lớp bảo mật nữa cho VPC.

#### Nội dung

- [Security groups](2.1-securitygroup/)
- [Network ACLs](2.2-networkacls/)
  
