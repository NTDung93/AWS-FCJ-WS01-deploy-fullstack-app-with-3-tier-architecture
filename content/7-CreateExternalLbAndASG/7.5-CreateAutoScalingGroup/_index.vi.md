---
title : "Tạo Auto Scaling Group"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 7.5 </b> "
---

#### Tạo Auto Scaling Group
1. Ở giao diện EC2, chọn **Auto scaling group** ở sidebar, sau đó click **Create auto scaling group.**
![](/workshop01-AWS-FCJ-2024/images/5-5/01.png?width=50pc)

2. Ở giao diện tạo ASG:
    - **Name** điền **`WebTierASG`**
    - **Launch template** chọn **WebTier-LaunchTemplate**
    - Kéo xuống dưới cùng và click **Next**
![](/workshop01-AWS-FCJ-2024/images/7-5/02.png?width=50pc)
3. Ở giao diện tạo ASG phần Network:
    - **VPC: my-vpc**
    - **AZs and subnets** chọn **Public Subnet 1** và **Public Subnet 2**
    - Click **Next**
![](/workshop01-AWS-FCJ-2024/images/7-5/03.png?width=50pc)

4. Ở giao diện config tiếp theo:
    - **Load balancing** chọn **Attach to an existing load balancer**
    - Chọn **Choose from your load balancer target group** sau đó chọn **WebTierTargetGroup**
    - Lướt xuống cuối và click **Next**
![](/workshop01-AWS-FCJ-2024/images/7-5/04.png?width=50pc)

5. Ở giao diện config tiếp theo:
    - **Desired capacity**: **2**
    - **Min desired capacity**: **2**
    - **Max desired capacity**: **2**
    - Lướt xuống cuối và click **Next**
    - **Next** tới bước cuối cùng thì click **Create auto scaling group**
![](/workshop01-AWS-FCJ-2024/images/7-5/05.png?width=50pc)

6. Hoàn thành tạo ASG:
![](/workshop01-AWS-FCJ-2024/images/7-5/06.png?width=50pc)

7. Sau khi tạo ASG thành công, 2 ec2 instance mới sẽ được tạo:
![](/workshop01-AWS-FCJ-2024/images/7-5/09.png?width=50pc)

8. Giờ chúng ta có thể open web bằng **DNS name** của **web-tier-external-lb**
![](/workshop01-AWS-FCJ-2024/images/7-5/08.png?width=50pc)

