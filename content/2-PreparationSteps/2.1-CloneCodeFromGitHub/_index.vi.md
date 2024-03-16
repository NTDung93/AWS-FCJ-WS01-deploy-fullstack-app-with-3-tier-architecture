---
title : "Clone code từ GitHub"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---
#### Clone code từ GitHub
1. Truy cập vào folder mà bạn muốn lưu trữ code.

2. Chuột phải chọn **Open Git Bash Here**.
![Git Bash](/workshop01-AWS-FCJ-2024/images/2-CloneCode/01.png?width=40pc)

3. Gõ lệnh **`git clone https://github.com/NTDung93/library-app.git`** rồi enter.

![Git Bash](/workshop01-AWS-FCJ-2024/images/2-CloneCode/02.png?width=40pc)

4. Hoàn thành clone code từ GitHub
![Git Bash](/workshop01-AWS-FCJ-2024/images/2-CloneCode/03.png?width=40pc)

5. Checkout qua nhánh **deploy** bằng lệnh **`git checkout deploy`** (nhánh đã được tinh chỉnh source code để thuận tiện cho việc deploy)
![Git Bash](/workshop01-AWS-FCJ-2024/images/2-CloneCode/04.png?width=40pc)

{{% notice note %}}
Nếu bạn có mở source code phần Front-end, nó sẽ báo lỗi đỏ khắp màn hình, đừng lo lắng vì source đó đã xóa folder Node_modules để phục vụ cho việc deploy trong các section tới, bạn chỉ cần chạy lệnh **`npm install`** để cài đặt lại các package cần thiết. Nhưng nếu bạn không có nhu cầu mở source code phần Front-end, bạn có thể bỏ qua bước này.
{{% /notice %}}