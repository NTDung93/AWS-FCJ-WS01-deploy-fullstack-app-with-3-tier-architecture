---
title : "Create EC2 Server"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---

## Create EC2 Instances for App Tier

1. Find and select the **EC2** service.
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/01.png?width=50pc)

2. Select **Instances** in the sidebar, then click **Launch instances**.
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/02.png?width=50pc)

3. **Name and tags** fill in **My App Server 1**
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/03.png?width=50pc)

4. In the **AMI** section:
   - select **Amazon Linux**
   - **AMI** select **Amazon Linux 2 AMI (HVM)**
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/04.png?width=50pc)

5. In the **Key pair** section, we choose **Proceed without a key pair** because we will connect the EC2 instance through **AWS Systems Manager Session Manager**.
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/05.png?width=50pc)

6. In the **Network settings** section:
   - **VPC** select **my-vpc**
   - **Subnet** select **Private Subnet 1**
   - **Auto-assign public IP** select **Enable**
   - **SG** select **Select existing security group**
   - **Common SG** select **AppTier-SG**
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/06.png?width=50pc)

7. In the **Advanced details** section, **IAM instance profile** select **ec2role** we created above
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/07.png?width=50pc)

8. Click **Launch instance**
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/08.png?width=40pc)

9. Complete creating EC2 instance for a server in **AppTier** in **private subnet 1**
![Git Bash](/workshop01-AWS-FCJ-2024/images/4-1/09.png?width=50pc)