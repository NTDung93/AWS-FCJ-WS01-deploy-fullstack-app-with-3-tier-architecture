---
title : "Tạo Security Group"
date :  "`r Sys.Date()`" 
weight : 9
chapter : false
pre : " <b> 2.9 </b> "
---

#### Tạo Security Group cho External (Internet Facing) Load Balancer

1. Ở giao diện VPC, chọn **Security groups** ở sidebar, sau đó click **Create security group** để tạo SG cho **ELB (Elastic load balancer)** chuẩn bị tạo
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/01.png?width=50pc)

2. Ở giao diện tạo security group:
    - **Name** điền **`InternetFacing-LB-SG`**
    - **Description** điền **`External load balancer security group`**
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/02.png?width=50pc)

3. Thiết lập **Inbound rules**, bằng cách thêm các rule sau:
    - **Rule đầu tiên** cho phép truy cập **HTTP**, và **Source: Anywhere-IPv4**
    - **Rule thứ hai** cho phép **SSH** từ **My IP** tức IP cá nhân, sẽ thay đổi khi bạn thay đổi mạng
    - **Rule cuối Type: All ICMP - IPv4** và **Source: Anywhere-IPv4** cho phép ping từ bất kì địa chỉ IP nào
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/03.png?width=50pc)

4. Kéo xuống cuối và click **Create security group**
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/04.png?width=50pc)

5. Hoàn thành tạo SG cho ELB
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/05.png?width=50pc)

#### Tạo SG cho Web tier
6. Lặp lại các bước trên để tạo SG cho **Web tier** (tầng present với user, có thể hiểu như front-end)
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/06.png?width=50pc)

7. Thiết lập **Inbound rules**, bằng cách thêm các rule sau:
    - **Rule đầu tiên** cho phép truy cập bằng **HTTP** nhưng chỉ với source từ **InternetFacing-LB-SG** ta vừa tạo ở trên (theo cấu trúc đã thiết kế)
    - Các rule sau tương tự như tạo SG cho ELB
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/07.png?width=50pc)

8. Kéo xuống dưới cùng và click **Create security group**
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/08.png?width=50pc)

#### Tạo SG cho Internal load balancer
9. Tạo SG thứ 3 dành cho **Internal load balancer**
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/09.png?width=50pc)

10. Cài đặt **Inbound rules**:
    - **Type: HTTP** chọn **Source: WebTier-SG** cho phép truy cập HTTP từ SG của web tier
    - Sau đó click **Create security group**
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/10.png?width=50pc)

#### Tạo SG thứ 4 cho App tier (các private instances)
11. Tạo SG thứ 4 cho **App tier** (các private instances)
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/11.png?width=50pc)

12. Cài đặt **Inbound rules**:
    - **Type: Custom TCP, Port: 8080** và **Source: Internal-LB-SG** cho phép traffic từ internal load balancer đi vào 
    - Và 2 rule tương tự nhưng **Source: Anywhere-IPv4** và **My IP**
    - Sau đó click **Create security group**
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/12.png?width=50pc)

#### Tạo SG thứ 5 cho Data tier (các private instances chứa MySql)
13. Tạo SG thứ 5 cho **Data tier** (các private instances chứa MySql)
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/13.png?width=50pc)

14. Cài đặt **Inbound rules**:
    - **Type: MYSQL/Aurora** và **Source: AppTier-SG** cho phép traffic từ App tier đi vào 
    - Sau đó click **Create security group**
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/14.png?width=50pc)
    - Có thể thêm 2 rule nữa như hình để có thể **connect db instance** từ ngoài vpc (với mục đích test)
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/15.png?width=50pc)

15. Hoàn thành tạo 5 SG cho cấu trúc đã thiết kế
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/16.png?width=50pc)