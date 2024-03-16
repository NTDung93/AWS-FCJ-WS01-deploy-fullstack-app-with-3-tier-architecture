---
title : "Create Launch Template"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 5.4 </b> "
---

#### Create Launch Template
**Launch templates** and **AMIs (Amazon Machine Images)** are both fundamental for launching EC2 instances on AWS, but they serve different purposes:
- **AMI (Amazon Machine Image)**: An AMI is a template that captures the entire software environment of a running EC2 instance. It includes the operating system, applications, configurations, and data volumes. AMIs act as blueprints for creating new instances with the same software setup. You can think of them as pre-configured snapshots of a virtual machine.
- **Launch Template**: A launch template defines the configuration details needed to launch an EC2 instance. This includes the AMI ID (which specifies the software environment), instance type (hardware capabilities), security groups (network access rules), user data (scripts to run on instance startup), and other launch parameters. It essentially defines how an instance will be provisioned beyond the base software provided by the AMI.

**Here's an analogy**: Imagine an AMI as a recipe for a cake, specifying the ingredients (operating system, applications). A launch template would be like the baking instructions, including the oven temperature (instance type), baking time, and any additional steps (user data scripts). You can use the same cake recipe (AMI) with different baking instructions (launch templates) to create cakes with variations (different instance configurations).

#### Create Launch Template
1. In the EC2 dashboard, select **Launch templates** in the sidebar, then click **Create launch template**
![](/workshop01-AWS-FCJ-2024/images/5-4/01.png?width=50pc)

2. In the launch template creation interface, under **Launch template name and description**, fill in **Launch template name** as **`AppTier-LaunchTemplate`**
![](/workshop01-AWS-FCJ-2024/images/5-4/02.png?width=50pc)

3. Under the AMI selection, choose **Owned by me** then select **AppTierImage**
![](/workshop01-AWS-FCJ-2024/images/5-4/03.png?width=50pc)

4. Choose **Instance type** as **t2.micro**
![](/workshop01-AWS-FCJ-2024/images/5-4/04.png?width=50pc)

5. **Keypair** to **Don’t include in launch template**
![](/workshop01-AWS-FCJ-2024/images/5-4/05.png?width=50pc)

6. **Network settings**:
    - **Subnet** to **Don’t include in launch template**
    - **SG** to existing sg, then select **AppTier-SG**
![](/workshop01-AWS-FCJ-2024/images/5-4/06.png?width=50pc)

7. **Advanced details, IAM instance profile** to **ec2role**
![](/workshop01-AWS-FCJ-2024/images/5-4/07.png?width=50pc)

8. Scroll down to the bottom, select **Create launch template**. Done!
![](/workshop01-AWS-FCJ-2024/images/5-4/08.png?width=50pc)