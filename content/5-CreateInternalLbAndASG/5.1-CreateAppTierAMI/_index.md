---
title : "Create AMI for App Tier"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 5.1 </b> "
---

#### Why do we need AMIs?
-  **Reproduce configurations easily** - Once you have an instance configured the way you want, with all necessary software, settings etc., you can create an AMI from it. Then launching new instances from that AMI ensures all instances have the same baseline configuration automatically.
- **Standardize environments** - AMIs help maintain consistency across your environments. For example, you may have an AMI configured for a web server role that contains the necessary web server software and configurations. All new web server instances would use this standardized AMI.
- **Backup and recovery** - AMIs act as machine snapshots that can be used for backup, disaster recovery or to reproduce instances that may have failed. If an existing instance fails or needs to be replaced, launching a new one from the AMI is quicker than reconfiguring from scratch.
- **Auto scaling** - When using auto scaling groups to dynamically scale your fleet size based on demand, AMIs ensure all new instances added by auto scaling have the required configuration already in place.

#### Create AMI from EC2 Instance
1. Access EC2 service:
    - Choose **Instances** from the sidebar
    - Select instance **My App Server 1**
    - Click **Actions**, then click **Image and template** and choose **Create image**
![AMI](/workshop01-AWS-FCJ-2024/images/5-1/01.png?width=50pc)

2. In the create image interface:
    - Fill in **Image name** with **`AppTierImage`**
    - Fill in **Image description** with **`App tier`**
    - Scroll down to the bottom and click **Create image**
![AMI](/workshop01-AWS-FCJ-2024/images/5-1/02.png?width=50pc)

