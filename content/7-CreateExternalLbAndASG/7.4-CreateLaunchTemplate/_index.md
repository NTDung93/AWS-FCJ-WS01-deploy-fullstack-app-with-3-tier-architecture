---
title : "Create Launch Template"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 7.4 </b> "
---
#### Create Launch Template
1. In the EC2 dashboard, select **Launch templates** in the sidebar, then click **Create launch template**
![](/workshop01-AWS-FCJ-2024/images/5-4/01.png?width=50pc)

2. In the launch template creation interface, under **Launch template name and description**, fill in **Launch template name** as **`WebTier-LaunchTemplate`**
![](/workshop01-AWS-FCJ-2024/images/7-4/02.png?width=50pc)

3. Under the AMI selection, choose **Owned by me** then select **WebTierImage**
![](/workshop01-AWS-FCJ-2024/images/7-4/03.png?width=50pc)

4. Choose **Instance type** as **t2.micro**
![](/workshop01-AWS-FCJ-2024/images/7-4/04.png?width=50pc)

5. **Keypair** to **Don’t include in launch template**
![](/workshop01-AWS-FCJ-2024/images/7-4/05.png?width=50pc)

6. **Network settings**:
    - **Subnet** to **Don’t include in launch template**
    - **SG** to existing sg, then select **WebTier-SG**
![](/workshop01-AWS-FCJ-2024/images/7-4/06.png?width=50pc)

7. **Advanced details, IAM instance profile** to **ec2role**
![](/workshop01-AWS-FCJ-2024/images/7-4/07.png?width=50pc)

8. Scroll down to the bottom, select **Create launch template**. Done!
![](/workshop01-AWS-FCJ-2024/images/7-4/08.png?width=50pc)