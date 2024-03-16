---
title : "Tạo database instance"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 3.2 </b> "
---

#### Tạo database instance

1. Trong giao diện Amazon RDS, chọn **Databases** ở sidebar sau đó click **Create database**
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/01.png?width=50pc)

2. Ở giao diện Create database:
   - **Creation method** chọn **Standard create**
   - **Engine type** chọn **MySQL**
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/02.png?width=50pc)

3. **Templates** chọn **Dev/Test**, **Deployment options** chọn **Multi-AZ DB instance** (để tạo ra instance chính ở AZ hiện tại, và một clone instance ở AZ còn lại đã define trong db subnet group phòng failover)
→ Cách triển khai này sẽ best practice vì đáp ứng tiêu chí High availability và Data redundancy
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/03.png?width=50pc)
- Nhưng chúng ta có thể chọn option khác là **Free tier** để vừa phù hợp với scope của bài toán, vừa tiết kiệm chi phí
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/04.png?width=50pc)

4. Ở phần Settings:
   - **DB instance identifier** điền **`database-1`**
   - **Master username** điền **`admin`**
   - **Master password** điền **`12345678`**
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/05.png?width=50pc)

5. Ở phần Connectivity:
   - **Computer resource** chọn **Dont connect to EC2**
   - **VPC** chọn **my-vpc**
   - **DB subnet group** chọn **db-subnet-group** ta đã tạo
   - **Public access** chọn **No** (chọn **Yes** nếu muốn test connection từ public network)
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/06.png?width=50pc)
   - **VPC SG** chọn **Choose existing**
   - **Existing VPC SG** chọn **DataTier-SG**
   - **AZ** chọn **ap-southeast-1a**
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/07.png?width=50pc)
6. Ở phần **Additional configuration**, điền db name là **`demodb`** (**master name: admin, pass: 12345678**)
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/08.png?width=50pc)

7. Kéo xuống dưới cùng và chọn **Create database**:
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/09.png?width=50pc)

8. Hoàn thành tạo database instance
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/10.png?width=50pc)
#### Config lại để test connection từ public network
{{% notice note %}}
Để có thể test connection tới endpoint của db vừa tạo từ public network, ta phải config lại một số thứ như sau (sau khi test xong nhớ trả tất cả về trạng thái ban đầu)
   - Vào route table **private-db-route-table**, thêm một route mới với destination là **0.0.0.0/0** và target là **internet gateway** ta đã tạo
   - Vào security group **DataTier-SG**, thêm một inbound rule mới cho phép All traffic truy cập
   - Cập nhật lại trạng thái của **Public access** ở phần **Connectivity** trong db instance từ **No** thành **Yes**
{{% /notice %}}

#### Test connection tới endpoint của db instance vừa tạo
1. Vào phần mềm **MySQL Workbench**, tạo connect mới:
   - **Connection Name** điền **`db-ws-01`** 
   - **Hostname** copy và paste **endpoint** của db instance vừa tạo
   - **Port** điền **`3306`**
   - **Username** điền **`admin`**
   - **Password** click **Store in Vault** rồi nhập **`12345678`**
   - Sau cùng, nhấn **Test Connection**
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/11.png?width=50pc)

2. Test connection thành công
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/12.png?width=50pc)

3. Vào file **application.properties** và config lại **datasource url**, **username** và **password** như hình dưới
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/13.png?width=50pc)

4. Run app và check trong connection vừa tạo trong MySQL, ta thấy các table đã được auto generate nhờ vào cơ chế **code first** (chỉ để test vì trong workshop này chúng ta sẽ sử dụng **database first**)
![create db instance](/workshop01-AWS-FCJ-2024/images/3-2/14.png?width=40pc)