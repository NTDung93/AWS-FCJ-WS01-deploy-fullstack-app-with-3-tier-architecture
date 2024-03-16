---
title : "Giải thích luồng chạy"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1.1 </b> "
---
## Giải thích luồng chạy của kiến trúc ba tầng

Trong hình dưới đây, chúng ta sẽ thấy mô hình kiến trúc của ứng dụng fullstack với **kiến trúc ba tầng**. Đầu tiên, thao tác của người dùng sẽ đi qua **Internet gateway** và sau đó đến **External (Internet facing) Application Load Balancer**. Load Balancer sẽ chuyển tiếp các traffic đến các **máy chủ ở Web tier**. Sau đó các máy chủ ở Web tier sẽ gọi các API đến **Interal Load Balancer**. Load Balancer sau đó sẽ chuyển tiếp các traffic đến các **máy chủ ở App tier**. Cuối cùng, các máy chủ ở App tier sẽ xử lý yêu cầu, truy xuất dữ liệu ở **Data tier** (nếu cần) và trả kết quả về cho người dùng ở Web tier. Đây là mô hình kiến trúc ba lớp cơ bản mà chúng ta sẽ triển khai trong workshop này.

![Architecture diagram](/workshop01-AWS-FCJ-2024/images/1-Introduce/workshop01-white.png?width=60pc)
