---
title : "Dọn dẹp tài nguyên"
date :  "`r Sys.Date()`" 
weight : 9
chapter : false
pre : " <b> 9. </b> "
---
#### Dọn dẹp tài nguyên

Chúng ta sẽ tiến hành xóa các tài nguyên theo thứ tự sau:
1. Xóa **NAT Gateway**
![NAT Gateway](/workshop01-AWS-FCJ-2024/images/9/01.png?width=50pc)
![NAT Gateway](/workshop01-AWS-FCJ-2024/images/9/02.png?width=50pc)

2. Xóa **Elastic IPs**
![EIPs](/workshop01-AWS-FCJ-2024/images/9/03.png?width=50pc)
![EIPs](/workshop01-AWS-FCJ-2024/images/9/04.png?width=50pc)

3. Xóa **Auto Scaling Group**
![Auto Scaling Group](/workshop01-AWS-FCJ-2024/images/9/05.png?width=50pc)
![Auto Scaling Group](/workshop01-AWS-FCJ-2024/images/9/06.png?width=50pc)

4. Xóa **Load Balancer**
![Load Balancer](/workshop01-AWS-FCJ-2024/images/9/07.png?width=50pc)
![Load Balancer](/workshop01-AWS-FCJ-2024/images/9/08.png?width=50pc)

5. Xóa **Target group**
![Target group](/workshop01-AWS-FCJ-2024/images/9/09.png?width=50pc)
![Target group](/workshop01-AWS-FCJ-2024/images/9/10.png?width=50pc)

6. Xóa **Launch template**
![Launch template](/workshop01-AWS-FCJ-2024/images/9/11.png?width=50pc)
![Launch template](/workshop01-AWS-FCJ-2024/images/9/12.png?width=50pc)

7. Xóa **AMIs**
![AMIs](/workshop01-AWS-FCJ-2024/images/9/13.png?width=50pc)
![AMIs](/workshop01-AWS-FCJ-2024/images/9/14.png?width=50pc)

8. Xóa **EC2 instances**
![EC2 instances](/workshop01-AWS-FCJ-2024/images/9/15.png?width=50pc)
![EC2 instances](/workshop01-AWS-FCJ-2024/images/9/16.png?width=50pc)

9. Xóa Database **RDS**
![RDS](/workshop01-AWS-FCJ-2024/images/9/17.png?width=50pc)
![RDS](/workshop01-AWS-FCJ-2024/images/9/18.png?width=50pc)

10. Xóa **Route tables**
    - Ta phải xóa các subnet associations của từng route table trước (vào subnet -> table associations -> edit subnet associations -> unchecked các subnet đã gán -> save)
![Route tables](/workshop01-AWS-FCJ-2024/images/9/19.png?width=50pc)
    - Xóa route table
![Route tables](/workshop01-AWS-FCJ-2024/images/9/20.png?width=50pc)
![Route tables](/workshop01-AWS-FCJ-2024/images/9/21.png?width=50pc)

11. Xóa **Internet Gateway**
    - detach IGW ra khỏi VPC
![Internet Gateway](/workshop01-AWS-FCJ-2024/images/9/22.png?width=50pc)
    - Xóa IGW
![Internet Gateway](/workshop01-AWS-FCJ-2024/images/9/23.png?width=50pc)

12. Xóa **VPC**
![VPC](/workshop01-AWS-FCJ-2024/images/9/24.png?width=50pc)
![VPC](/workshop01-AWS-FCJ-2024/images/9/25.png?width=50pc)

13.  Xóa **S3 bucket**
     - Xóa các file trong bucket
![S3 bucket](/workshop01-AWS-FCJ-2024/images/9/26.png?width=50pc)
     - Xóa bucket
![S3 bucket](/workshop01-AWS-FCJ-2024/images/9/27.png?width=50pc) 