---
title : "Tạo máy chủ EC2"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 4.1 </b> "
---

#### Tạo EC2 instance cho App Tier

1. Tìm và chọn dịch vụ **EC2**
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/01.png?width=50pc)
2. Chọn **Instances** ở sidebar, sau đó click **Launch instances**
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/02.png?width=50pc)
3. **Name and tags** điền **My App Server 1**
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/03.png?width=50pc)
4. Ở phần **AMI**:
   - chọn **Amazon Linux** 
   - **AMI** chọn **Amazon Linux 2 AMI (HVM)**
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/04.png?width=50pc)
5. Ở phần **Key pair**, ta chọn **Proceed without a key pair** vì ta sẽ connect EC2 instance thông qua **AWS Systems Manager Session Manager**.
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/05.png?width=50pc)
6. Ở phần **Network settings**:
   - **VPC** chọn **my-vpc**
   - **Subnet** chọn **Private Subnet 1**
   - **Auto-assign public IP** chọn **Enable**
   - **SG** chọn **Select existing security group**
   - **Common SG** chọn **AppTier-SG**
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/06.png?width=50pc)
7. Ở phần **Advanced details**, **IAM instance profile** chọn **ec2role** ta tạo ở trên
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/07.png?width=50pc)
8. Click **Launch instance**
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/08.png?width=40pc)
9. Hoàn thành tạo EC2 instance cho một server ở **AppTier** ở **private subnet 1**
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/09.png?width=50pc)