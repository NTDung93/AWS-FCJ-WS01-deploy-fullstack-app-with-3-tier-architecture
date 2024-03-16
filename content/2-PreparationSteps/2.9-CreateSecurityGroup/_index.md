---
title : "Create Security Group"
date :  "`r Sys.Date()`" 
weight : 9
chapter : false
pre : " <b> 2.9 </b> "
---

#### Create Security Group for External (Internet Facing) Load Balancer

1. In the VPC interface, choose **Security groups** on the sidebar, then click **Create security group** to create a security group for the **ELB (Elastic load balancer)** to be created
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/01.png?width=50pc)

2. In the create security group interface:
    - **Name** enter **`InternetFacing-LB-SG`**
    - **Description** enter **`External load balancer security group`**
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/02.png?width=50pc)

3. Set up **Inbound rules**, by adding the following rules:
    - **First rule** allows access to **HTTP**, and **Source: Anywhere-IPv4**
    - **Second rule** allows **SSH** from **My IP** which means personal IP, will change when you change the network
    - **Last rule Type: All ICMP - IPv4** and **Source: Anywhere-IPv4** allows ping from any IP address
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/03.png?width=50pc)

4. Scroll down to the bottom and click **Create security group**
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/04.png?width=50pc)

5. Finish creating SG for ELB
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/05.png?width=50pc)

#### Create SG for Web tier
6. Repeat the above steps to create SG for **Web tier** (present layer with user, can be understood as front-end)
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/06.png?width=50pc)

7. Set up **Inbound rules**, by adding the following rules:
    - **First rule** allows access via **HTTP** but only with source from **InternetFacing-LB-SG** we just created above (according to the designed structure)
    - The following rules are similar to creating SG for ELB
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/07.png?width=50pc)

8. Scroll down to the bottom and click **Create security group**
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/08.png?width=50pc)

#### Create SG for Internal load balancer
9. Create the 3rd SG for **Internal load balancer**
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/09.png?width=50pc)

10. Set up **Inbound rules**:
    - **Type: HTTP** choose **Source: WebTier-SG** allows access to HTTP from the web tier SG
    - Then click **Create security group**
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/10.png?width=50pc)

#### Create the 4th SG for App tier (private instances)
11. Create the 4th SG for **App tier** (private instances)
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/11.png?width=50pc)

12. Set up **Inbound rules**:
    - **Type: Custom TCP, Port: 8080** and **Source: Internal-LB-SG** allows traffic from internal load balancer to enter
    - And 2 similar rules but **Source: Anywhere-IPv4** and **My IP**
    - Then click **Create security group**
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/12.png?width=50pc)

#### Create the 5th SG for DB tier 
13. Create the 5th SG for **DB tier** (private instances containing MySql)
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/13.png?width=50pc)

14. Set up **Inbound rules**:
    - **Type: Custom TCP, Port: 3306** and **Source: AppTier-SG** allows traffic from app tier to enter
    - Then click **Create security group**
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/14.png?width=50pc)
    - You can add more rules to allow traffic from other sources for testing purposes
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/15.png?width=50pc)

15. Finish creating 5 SG for the designed structure
![Create security group](/workshop01-AWS-FCJ-2024/images/2-9/16.png?width=50pc)
