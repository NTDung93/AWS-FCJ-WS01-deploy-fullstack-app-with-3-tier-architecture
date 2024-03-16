---
title : "Tạo Auto Scaling Group"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5.5 </b> "
---

#### Tạo Auto Scaling Group
1. Ở giao diện EC2, chọn **Auto scaling group** ở sidebar, sau đó click **Create auto scaling group.**
![](/workshop01-AWS-FCJ-2024/images/5-5/01.png?width=50pc)

2. Ở giao diện tạo ASG:
    - **Name** điền **`AppTierASG`**
    - **Launch template** chọn **AppTier-LaunchTemplate**
    - Kéo xuống dưới cùng và click **Next**
![](/workshop01-AWS-FCJ-2024/images/5-5/02.png?width=50pc)
3. Ở giao diện tạo ASG phần Network:
    - **VPC: my-vpc**
    - **AZs and subnets** chọn **Private Subnet 1** và **Private Subnet 2**
    - Click **Next**
![](/workshop01-AWS-FCJ-2024/images/5-5/03.png?width=50pc)

4. Ở giao diện config tiếp theo:
    - **Load balancing** chọn **Attach to an existing load balancer**
    - Chọn **Choose from your load balancer target group** sau đó chọn **AppTierTargetGroup**
    - Lướt xuống cuối và click **Next**
![](/workshop01-AWS-FCJ-2024/images/5-5/04.png?width=50pc)

5. Ở giao diện config tiếp theo:
    - **Desired capacity**: **2**
    - **Min desired capacity**: **2**
    - **Max desired capacity**: **2**
    - Lướt xuống cuối và click **Next**
    - **Next** tới bước cuối cùng thì click **Create auto scaling group**
![](/workshop01-AWS-FCJ-2024/images/5-5/05.png?width=50pc)

6. Hoàn thành tạo ASG:
![](/workshop01-AWS-FCJ-2024/images/5-5/06.png?width=50pc)

7. Sau khi tạo ASG thành công, 2 ec2 instance mới sẽ được tạo:
![](/workshop01-AWS-FCJ-2024/images/5-5/07.png?width=50pc)

{{% notice note %}}
→ Bây giờ chúng ta có 3 ec2 instances, giờ chúng ta có thể terminate con instance gốc My App Server 1 đi (nhưng recommend nên giữ lại để dễ dàng troubleshoot sau này)
{{% /notice %}}

{{% notice note %}}
→Nếu terminate bất kỳ con nào trong ASG, thì con mới sẽ được launched bởi ASG ngay tức thì
{{% /notice %}}

8. Thử terminate cả 2 con trong ASG đi, 2 con mới sẽ được launched ngay lập tức bởi ASG
![](/workshop01-AWS-FCJ-2024/images/5-5/08.png?width=50pc)

