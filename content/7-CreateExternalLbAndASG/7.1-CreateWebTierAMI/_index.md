---
title : "Create AMI for Web Tier"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 7.1 </b> "
---

#### Create AMI from EC2 Instance
1. Access EC2 service:
    - Choose **Instances** from the sidebar
    - Select instance **My Web Server 1**
    - Click **Actions**, then click **Image and template** and choose **Create image**
![AMI](/workshop01-AWS-FCJ-2024/images/7-1/01.png?width=50pc)

2. In the create image interface:
    - Fill in **Image name** with **`WebTierImage`**
    - Fill in **Image description** with **`Web tier`**
    - Scroll down to the bottom and click **Create image**
![AMI](/workshop01-AWS-FCJ-2024/images/7-1/02.png?width=50pc)

