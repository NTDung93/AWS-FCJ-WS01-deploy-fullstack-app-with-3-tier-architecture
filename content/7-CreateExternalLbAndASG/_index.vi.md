---
title : "Tạo External Load Balancer và Auto Scaling Group"
date :  "`r Sys.Date()`" 
weight : 7
chapter : false
pre : " <b> 7. </b> "
---
#### Giới thiệu
Ở section này, chúng ta sẽ tạo **External Load Balancer** để cân bằng tải các traffic từ người dùng (internet) tới Web Tier và **Auto Scaling Group** cho Web Tier.

#### Nội dung:

1. [Tạo AMI cho Web Tier](7.1-CreateWebTierAMI)
2. [Tạo Tartget Group cho Web Tier](7.2-CreateTargetGroup)
3. [Tạo External Load Balancer](7.3-CreateExternalLoadBalancer)
4. [Tạo Launch Template cho Web Tier](7.4-CreateLaunchTemplate)
5. [Tạo Auto Scaling Group](7.5-CreateAutoScalingGroup)