---
title : "Tạo Route Table"
date :  "`r Sys.Date()`" 
weight : 8
chapter : false
pre : " <b> 2.8 </b> "
---

#### Tạo Route Table

1. Tại giao diện của VPC, click chọn **Route tables** ở sidebar và click **Create route table**
![Create route table](/workshop01-AWS-FCJ-2024/images/2-8/01.png?width=50pc)

2. Tại giao diện Create route table:
    - **Name** nhập **`public-route-table`**
    - **VPC** chọn **my-vpc**
    - Click **Create route table**
![Create route table](/workshop01-AWS-FCJ-2024/images/2-8/02.png?width=50pc)

3. Sau khi tạo thành công route table, click **Edit routes**
![Edit routes](/workshop01-AWS-FCJ-2024/images/2-8/03.png?width=50pc)

4. Ở màn hình Edit routes, chọn **Add route**
![Add route](/workshop01-AWS-FCJ-2024/images/2-8/04.png?width=50pc)

5. Sau đó thêm route với **Destination** là **`0.0.0.0/0`** và **Target** là **workshop-01-igw** sau đó click **Save changes**
![Add route](/workshop01-AWS-FCJ-2024/images/2-8/05.png?width=50pc)

6. Sau khi tạo thành công, chuyển qua tab **Subnet associations** và click **Edit subnet associations**
![Edit subnet associations](/workshop01-AWS-FCJ-2024/images/2-8/06.png?width=50pc)

7. Chọn 2 public subnet ta đã tạo rồi click **Save associations**
![Edit subnet associations](/workshop01-AWS-FCJ-2024/images/2-8/07.png?width=50pc)

8. Thực hiện tương tự các bước trên để tạo ra **private-route-table-01** cho **private subnet 1**
![Create route table](/workshop01-AWS-FCJ-2024/images/2-8/08.png?width=50pc)

9. Thêm route với **Destination** là **`0.0.0.0/0`** và **Target** là **nat-gw-01** sau đó click **Save changes**
![Add route](/workshop01-AWS-FCJ-2024/images/2-8/09.png?width=50pc)

10. Chọn **private subnet 1** rồi click **Save associations**
![Edit subnet associations](/workshop01-AWS-FCJ-2024/images/2-8/10.png?width=50pc)

#### Tạo route table cho 2 private db subnet
11. Thực hiện tương tự các bước trên để tạo ra **private-db-route-table**:
    - **VPC** chọn **my-vpc**
    - Thêm route với **Destination** là **`0.0.0.0/0`** và **Target** là **igw** đã tạo (mục đích để có thể giao tiếp với db instance từ internet ngoài vpc)
    - Thực hiện gán route table này cho 2 subnet là **Private DB Subnet 1** và **Private DB Subnet 2**
![Create route table](/workshop01-AWS-FCJ-2024/images/2-8/11.png?width=50pc)