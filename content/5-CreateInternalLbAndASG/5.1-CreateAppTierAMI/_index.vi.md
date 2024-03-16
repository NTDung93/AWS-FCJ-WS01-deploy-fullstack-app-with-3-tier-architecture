---
title : "Tạo AMI cho App Tier"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 5.1 </b> "
---

#### Vì sao chúng ta cần tạo Amazon Machine Image (AMI)?

- AMI bao gồm operating system, applications, configurations, và data volumes.
- **Reproduce config** hoặc **launch instance mới dễ dàng** - một khi đã tạo một instance với những config mong muốn, ta tạo AMI từ instance đó. Khi ta tạo ra những instance mới từ AMI đó, sẽ đảm bảo được tính consistency, các instance đều có những config tương đồng nhau.
- **Backup và recovery** - AMI như snapshot dùng để backup, recovery khi có thiên tai, để reproduce những instance bị fail → Nếu có instance nào fail hoặc cần thay thế, sẽ dễ dàng và nhanh chóng hơn nếu tạo từ AMI thay vì từ đầu.
- **Auto scaling** - Khi chúng ta sử dụng ASG (Auto Scaling Group) để scale up app, AMI sẽ đảm bảo những instance mới sẽ có những config cần thiết.

#### Tạo AMI từ instance
1. Truy cập vào dịch vụ EC2:
    - Chọn **Instances** ở sidebar
    - Chọn instance **My App Server 1**
    - Click **Actions**, sau đó click **Image and template** và chọn **Create image**
![AMI](/workshop01-AWS-FCJ-2024/images/5-1/01.png?width=50pc)

2. Ở giao diện tạo image:
    - **Image name** điền **`AppTierImage`**
    - **Image description** điền **`App tier`**
    - Lướt xuống dưới cùng, click **Create image**
![AMI](/workshop01-AWS-FCJ-2024/images/5-1/02.png?width=50pc)