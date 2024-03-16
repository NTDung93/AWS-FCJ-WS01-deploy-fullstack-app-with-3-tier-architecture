---
title : "Clean Up Resources"
date : "`r Sys.Date()`"
weight : 9
chapter : false
pre : " <b> 9. </b> "
---
## Clean Up Resources

We will proceed to delete the resources in the following order:
1. Delete **NAT Gateway**
![NAT Gateway](../../../images/9/01.png?width=50pc)
![NAT Gateway](../../../images/9/02.png?width=50pc)

2. Delete **Elastic IPs**
![EIPs](../../../images/9/03.png?width=50pc)
![EIPs](../../../images/9/04.png?width=50pc)

3. Delete **Auto Scaling Group**
![Auto Scaling Group](../../../images/9/05.png?width=50pc)
![Auto Scaling Group](../../../images/9/06.png?width=50pc)

4. Delete **Load Balancer**
![Load Balancer](../../../images/9/07.png?width=50pc)
![Load Balancer](../../../images/9/08.png?width=50pc)

5. Delete **Target group**
![Target group](../../../images/9/09.png?width=50pc)
![Target group](../../../images/9/10.png?width=50pc)

6. Delete **Launch template**
![Launch template](../../../images/9/11.png?width=50pc)
![Launch template](../../../images/9/12.png?width=50pc)

7. Delete **AMIs**
![AMIs](../../../images/9/13.png?width=50pc)
![AMIs](../../../images/9/14.png?width=50pc)

8. Delete **EC2 instances**
![EC2 instances](../../../images/9/15.png?width=50pc)
![EC2 instances](../../../images/9/16.png?width=50pc)

9. Delete Database **RDS**
![RDS](../../../images/9/17.png?width=50pc)
![RDS](../../../images/9/18.png?width=50pc)

10. Delete **Route tables**
    - We have to delete the subnet associations of each route table first (go to subnet -> table associations -> edit subnet associations -> unchecked the assigned subnets -> save)
![Route tables](../../../images/9/19.png?width=50pc)
    - Delete route table
![Route tables](../../../images/9/20.png?width=50pc)
![Route tables](../../../images/9/21.png?width=50pc)

11. Delete **Internet Gateway**
    - detach IGW from VPC
![Internet Gateway](../../../images/9/22.png?width=50pc)
    - Delete IGW
![Internet Gateway](../../../images/9/23.png?width=50pc)

12. Delete **VPC**
![VPC](../../../images/9/24.png?width=50pc)
![VPC](../../../images/9/25.png?width=50pc)

13. Delete **S3 bucket**
     - Empty bucket
![S3 bucket](../../../images/9/26.png?width=50pc)
     - Delete bucket
![S3 bucket](../../../images/9/27.png?width=50pc) 