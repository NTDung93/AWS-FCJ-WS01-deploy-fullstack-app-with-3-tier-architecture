---
title : "Tạo Launch Template"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 5.4 </b> "
---
#### Sự khác nhau giữa Launch template và AMI?
**Launch template** và **AMI (Amazon Machine Images)** đều là cơ sở quan trọng để khởi chạy các phiên bản EC2 trên AWS, nhưng chúng phục vụ cho các mục đích khác nhau:
- **AMI (Amazon Machine Image)**: Một AMI là một template mô phỏng toàn bộ môi trường phần mềm của một phiên bản EC2 đang chạy. Nó bao gồm hệ điều hành, ứng dụng, cấu hình và khối lượng dữ liệu. AMI hoạt động như bản thiết kế cho việc tạo ra các phiên bản mới với cùng một setup. Bạn có thể coi chúng như các bản snapshots của một máy ảo.
- **Launch template**: Một Launch template xác định các chi tiết cấu hình cần thiết để khởi chạy một phiên bản EC2. Điều này bao gồm ID AMI (xác định môi trường phần mềm), security group, user data (scripts to run on instance startup), và các tham số khởi chạy khác. Nó về cơ bản xác định cách một phiên bản sẽ được cung cấp ngoài phần mềm cơ sở được cung cấp bởi AMI.

**Dưới đây là một ví dụ**: Hãy tưởng tượng AMI như một công thức làm bánh, xác định các thành phần (hệ điều hành, ứng dụng). Một Launch template sẽ giống như hướng dẫn nướng bánh, bao gồm nhiệt độ lò (loại phiên bản), thời gian nướng, và bất kỳ bước nào bổ sung (các script dữ liệu người dùng). Bạn có thể sử dụng cùng một công thức làm bánh (AMI) với các hướng dẫn nướng khác nhau (Launch template) để tạo ra các loại bánh có biến thể (cấu hình phiên bản khác nhau).

#### Tạo Launch Template
1. Tại giao diện EC2, chọn **Launch templates** ở sidebar, sau đó click **Create launch template**
![](/workshop01-AWS-FCJ-2024/images/5-4/01.png?width=50pc)

2. Tại giao diện tạo launch template, ở phần **Launch template name and description**, **Launch template name** điền **`AppTier-LaunchTemplate`**
![](/workshop01-AWS-FCJ-2024/images/5-4/02.png?width=50pc)

3. Ở phần chọn AMI, chọn **Owned by me** sau đó chọn **AppTierImage**
![](/workshop01-AWS-FCJ-2024/images/5-4/03.png?width=50pc)

4. Chọn **Instance type** là **t2.micro**
![](/workshop01-AWS-FCJ-2024/images/5-4/04.png?width=50pc)

5. **Keypair** để **Don’t include in launch template**
![](/workshop01-AWS-FCJ-2024/images/5-4/05.png?width=50pc)

6. **Network settings**:
    - **Subnet** chọn **Don’t include in launch template**
    - **SG** chọn existing sg, sau đó chọn **AppTier-SG**
![](/workshop01-AWS-FCJ-2024/images/5-4/06.png?width=50pc)

7. **Advanced details, IAM instance profile** chọn **ec2role**
![](/workshop01-AWS-FCJ-2024/images/5-4/07.png?width=50pc)

8. Kéo xuống dưới cùng, chọn **Create launch template**. Hoàn thành!
![](/workshop01-AWS-FCJ-2024/images/5-4/08.png?width=50pc)