---
title : "Tạo Launch Template"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 7.4 </b> "
---
#### Tạo Launch Template
1. Tại giao diện EC2, chọn **Launch templates** ở sidebar, sau đó click **Create launch template**
![](/workshop01-AWS-FCJ-2024/images/5-4/01.png?width=50pc)

2. Tại giao diện tạo launch template, ở phần **Launch template name and description**, **Launch template name** điền **`WebTier-LaunchTemplate`**
![](/workshop01-AWS-FCJ-2024/images/7-4/02.png?width=50pc)

3. Ở phần chọn AMI, chọn **Owned by me** sau đó chọn **WebTierImage**
![](/workshop01-AWS-FCJ-2024/images/7-4/03.png?width=50pc)

4. Chọn **Instance type** là **t2.micro**
![](/workshop01-AWS-FCJ-2024/images/7-4/04.png?width=50pc)

5. **Keypair** để **Don’t include in launch template**
![](/workshop01-AWS-FCJ-2024/images/7-4/05.png?width=50pc)

6. **Network settings**:
    - **Subnet** chọn **Don’t include in launch template**
    - **SG** chọn existing sg, sau đó chọn **WebTier-SG**
![](/workshop01-AWS-FCJ-2024/images/7-4/06.png?width=50pc)

7. **Advanced details, IAM instance profile** chọn **ec2role**
![](/workshop01-AWS-FCJ-2024/images/7-4/07.png?width=50pc)

8. Kéo xuống dưới cùng, chọn **Create launch template**. Hoàn thành!
![](/workshop01-AWS-FCJ-2024/images/7-4/08.png?width=50pc)