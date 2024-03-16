---
title : "Clone Code from GitHub"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

## Clone Code from GitHub

1. Access the folder where you want to store the code.

2. Right-click and select **Open Git Bash Here**.
![Git Bash](/workshop01-AWS-FCJ-2024/images/2-CloneCode/01.png?width=40pc)

3. Type the command **`git clone https://github.com/NTDung93/library-app.git`** and press enter.
![Git Bash](/workshop01-AWS-FCJ-2024/images/2-CloneCode/02.png?width=40pc)

4. Complete the code clone from GitHub.
![Git Bash](/workshop01-AWS-FCJ-2024/images/2-CloneCode/03.png?width=40pc)

5. Checkout to the **deploy** branch using the command **`git checkout deploy`** (the branch has been adjusted the source code for easy deployment).
![Git Bash](/workshop01-AWS-FCJ-2024/images/2-CloneCode/04.png?width=40pc)

{{% notice note %}}
Nếu bạn có mở source code phần Front-end, nó sẽ báo lỗi đỏ khắp màn hình, đừng lo lắng vì source đó đã xóa folder Node_modules để phục vụ cho việc deploy trong các section tới, bạn chỉ cần chạy lệnh **`npm install`** để cài đặt lại các package cần thiết. Nhưng nếu bạn không có nhu cầu mở source code phần Front-end, bạn có thể bỏ qua bước này.
{{% /notice %}}