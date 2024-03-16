---
title : "Create IAM EC2 Role"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---

## Create IAM EC2 Role

1. Find **IAM** service on the search bar and click on it
![IAM](/workshop01-AWS-FCJ-2024/images/2-3/01.png?width=50pc)
2. Choose **Roles** on the sidebar, then click **Create role**
![Create role](/workshop01-AWS-FCJ-2024/images/2-3/02.png?width=50pc)
3. In the role creation interface, at **Select trusted entity** step:
    - **Trusted entity type** choose **AWS Service**
    - **Use case** choose **EC2**
    - Click **Next**
![Select trusted entity](/workshop01-AWS-FCJ-2024/images/2-3/03.png?width=50pc)
4. In the role creation interface, at **Add permissions** step:
    - Find, choose role **AmazonSSMManagedInstanceCore** (allow safe connection to instance without SSH key) and **AmazonS3ReadOnlyAccess** (allow instance to download code from S3)
    - Click **Next**
![Add permissions](/workshop01-AWS-FCJ-2024/images/2-3/04.png?width=50pc)
5. In the role creation interface, at **Name, review, and create** step:
    - Fill in the role name as **`ec2role`**
    - Review the 3 steps just set up
    - Click **Create role**
![Name, review, and create](/workshop01-AWS-FCJ-2024/images/2-3/05.png?width=50pc)
![Name, review, and create](/workshop01-AWS-FCJ-2024/images/2-3/06.png?width=50pc)
![Name, review, and create](/workshop01-AWS-FCJ-2024/images/2-3/07.png?width=50pc)
6. Finish creating role
![Role created](/workshop01-AWS-FCJ-2024/images/2-3/08.png?width=50pc)