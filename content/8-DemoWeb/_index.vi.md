---
title : "Demo deploy thành công"
date :  "`r Sys.Date()`" 
weight : 8
chapter : false
pre : " <b> 8. </b> "
---
#### Demo deploy thành công

1. Truy cập vào trang web bằng **DNS name** của **web-tier-external-lb**
![](/workshop01-AWS-FCJ-2024/images/8/01.png?width=60pc)

#### Demo giao diện home và api load sách sử dụng pagination
2. Để test việc call api thành công, trước khi truy cập vào web, ta sẽ inspect trên browser và mở tab **Network** và tick vào **Fetch/XHRđ** để xem request gửi đi và response nhận lại từ server.
    - chọn tab **Headers** để xem request gửi đi
![](/workshop01-AWS-FCJ-2024/images/8/02.png?width=60pc)

    - Chọn tab **Response** để xem response từ server
![](/workshop01-AWS-FCJ-2024/images/8/03.png?width=60pc)

#### Demo giao diện search sách và api search sách
3. Truy cập vào giao diện search sách bằng cách click vào **Search Books** trên header
![](/workshop01-AWS-FCJ-2024/images/8/04.png?width=60pc)

4. Sau đó nhập tên sách muốn tìm kiếm vào ô search và click vào nút **Search** (ngoài ra bạn có thể filter theo category của sách)
![](/workshop01-AWS-FCJ-2024/images/8/05.png?width=60pc)
![](/workshop01-AWS-FCJ-2024/images/8/06.png?width=60pc)

#### Demo chuyển trang sử dụng pagination
5. Trong giao diện **Search Books**, kéo xuống dưới cùng và click chọn **page number** để chuyển trang (hoặc sử dụng nút **First Page** và **Last Page**)
![](/workshop01-AWS-FCJ-2024/images/8/07.png?width=60pc)

{{% notice note %}}
Vì EC2 instance ta đang sử dụng chưa đủ mạnh nên khi upload code của front-end S3, tôi đã cắt giảm source code của front end khá nhiều dẫn tới việc app chỉ hoạt động trên một số tính năng cơ bản. Nếu bạn muốn app có thể chạy hoàn chỉnh, bạn có thể clone source code từ nhánh **Main** và sử dụng instance có cấu hình mạnh hơn.
{{% /notice %}}