---
title : "Tạo AMI cho Web Tier"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 7.1 </b> "
---

#### Tạo AMI từ instance
1. Truy cập vào dịch vụ EC2:
    - Chọn **Instances** ở sidebar
    - Chọn instance **My Web Server 1**
    - Click **Actions**, sau đó click **Image and template** và chọn **Create image**
![AMI](/workshop01-AWS-FCJ-2024/images/7-1/01.png?width=50pc)

2. Ở giao diện tạo image:
    - **Image name** điền **`WebTierImage`**
    - **Image description** điền **`Web tier`**
    - Lướt xuống dưới cùng, click **Create image**
![AMI](/workshop01-AWS-FCJ-2024/images/7-1/02.png?width=50pc)
