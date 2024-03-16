---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

#### Giới thiệu kiến trúc 3 tầng

**Kiến trúc ba tầng** là cách triển khai phổ biến nhất của kiến ​​trúc nhiều tầng, bao gồm một tầng giao diện, tầng logic và tầng dữ liệu. Hình minh họa sau đây cho thấy một ví dụ về một ứng dụng ba tầng chung đơn giản.

![Three tier example](/workshop01-AWS-FCJ-2024/images/1-Introduce/3TierExample.png?featherlight=false&width=50pc)

**Kiến trúc 3 tầng bao gồm**:
- Presentation tier / Web Tier: tầng giao diện để người dùng có thể tương tác trực tiếp (vd: trang web hay UI của ứng dụng mobile).
- Logic tier / App tier: tầng để xử lý logic và thực thi những câu lệnh của người dùng.
- Data tier: tầng lưu trữ dữ liệu của app.

**Lợi ích của việc sử dụng kiến trúc 3 tầng:**
- Tính mô-đun: kiến trúc này giúp ta module hóa app thành các phần độc lập nhau. Điều này giúp team dev có thể tập trung phát triển từng tầng của app, dẫn đến các thay đổi được áp dụng nhanh nhất có thể. Ngoài ra, nó còn giúp việc khôi phục app diễn ra nhanh chóng hơn sau khi server bị down do lỗi hay thảm họa nhờ vào việc có thể khoanh vùng và sửa chữa phần bị lỗi.
- Tính sẵn sàng cao: vì kiến trúc triển khai ứng dụng trên nhiều Availability Zones, các AZ được thiết kế để không xảy ra sự cố ảnh hưởng đồng thời 2 AZ một lúc (fault isolation).
- Tính dự phòng cao: AWS cho phép triển khai bản stand by hay replica của primary database trên AZ còn lại. Nếu database chính bị down, ứng dụng vẫn có thể truy xuất dữ liệu từ replica database.