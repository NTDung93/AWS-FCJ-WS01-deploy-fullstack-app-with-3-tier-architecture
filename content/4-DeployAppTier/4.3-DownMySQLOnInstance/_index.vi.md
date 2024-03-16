---
title : "Tải MySQL lên EC2 instance"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 4.3 </b> "
---

#### Tải MySQL lên EC2 instance

1. Chạy các command sau một cách lần lượt để tải MySQL lên instance:
   - **`sudo yum install -y https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm`**
   - **`sudo rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022`**
   - **`sudo yum install -y mysql-community-client`**
![download mysql](/workshop01-AWS-FCJ-2024/images/4-3/01.png?width=50pc)

2. Connect tới RDS database:
   - Chạy command **mysql -h <RDS-ENDPOINT> -u <USERNAME> -p** (**`mysql -h database-1.cbk6is6oozuw.ap-southeast-1.rds.amazonaws.com -u admin -p`**)
   - Sau đó điền password **`12345678`**
![connect to rds](/workshop01-AWS-FCJ-2024/images/4-3/02.png?width=50pc)

3. Chạy **`create database librarydb;`** để tạo mới 1 db
![create db](/workshop01-AWS-FCJ-2024/images/4-3/03.png?width=50pc)

4. Chạy **`show database;`** để show các db hiện có
![show db](/workshop01-AWS-FCJ-2024/images/4-3/04.png?width=50pc)

5. Chạy **`use librarydb;`** để sử dụng db vừa tạo
![use db](/workshop01-AWS-FCJ-2024/images/4-3/05.png?width=50pc)

6. Chạy **`show tables;`** để show những bảng trong db, lúc này db chưa có bảng nào
![show tables](/workshop01-AWS-FCJ-2024/images/4-3/06.png?width=50pc)

7. Để tạo bảng cho db, ta vào file **application.properties** của back-end và config lại các thông tin như hình dưới
![application properties](/workshop01-AWS-FCJ-2024/images/4-3/07.png?width=50pc)

8. Sau đó ta sẽ chạy app. Sau khi app chạy thành công, chạy lệnh **`show tables;`** lần nữa để kiểm tra
![show tables](/workshop01-AWS-FCJ-2024/images/4-3/08.png?width=50pc)

9. Chạy lệnh **insert into librarydb.book (author, category, copies, copies_available, description, img, title) values ('John', 'Programming', 10, 8, 'Tutorial about Java', '', 'Java Advanced');** để thêm 1 dòng data vào bảng book
![insert data](/workshop01-AWS-FCJ-2024/images/4-3/09.png?width=50pc)

10. Chạy **`select * from librarydb.book;`** để show những dòng data trong bảng book
![show data](/workshop01-AWS-FCJ-2024/images/4-3/10.png?width=50pc)

{{% notice note %}}
Những bước trên chỉ để test db đã hoạt động tốt theo những query mà ta đã viết. Nhưng trong workshop này chúng ta sẽ sử dụng database first approach, tức là ta sẽ tạo db trước và sau đó tạo entity và repository trong app để map với db.
{{% /notice %}}

11. Mở MySQL, truy cập vào connection đã tạo và import file **`React-Springboot-Add-Tables-Script-1.sql`** ở trong folder **`starter-files`**, sau đó chạy scripts có sẵn để tạo db tên **librarydb** và các bảng trong db
![import sql](/workshop01-AWS-FCJ-2024/images/4-3/11.png?width=50pc)