---
title : "Triển khai Web Tier"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---
#### Giới thiệu
Trong phần này, chúng ta sẽ tiến hành triển khai Web Tier bằng cách upload mã nguồn của ứng dụng lên **Amazon S3** và triển khai ứng dụng trên **Amazon EC2**. Ngoài ra chúng ta sẽ sử dụng **Nginx** trong workshop này. Nginx sẽ đóng vai trò là 1 **web server** mà chúng ta sẽ config để chạy úng dụng trên **port 80**, cũng như giúp **chuyển hướng API** request từ Web Tier đến App Tier thông qua **Internal Load Balancer**.

#### Nội dung:
1. [Sửa lại file cấu hình Nginx](6.1-UpdateConfigFile/)
2. [Upload mã nguồn ứng dụng lên Amazon S3](6.2-UploadCodeToS3/)
3. [Tạo EC2 Instance](6.3-CreateEc2Instance/)
4. [Kết nối tới EC2 Instance](6.4-ConnectToInstance/)
