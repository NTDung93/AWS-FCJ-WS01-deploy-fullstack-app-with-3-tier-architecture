---
title : "Create VPC for VPN"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 5.1.1 </b> "
---

## Create a VPN Environment

1. Access VPC Interface

- Select **Your VPC**
- Select **Create VPC**

![Create VPC](/images/9/0001.png?featherlight=false&width=90pc)

2. In the Create VPC Interface

- **Resource**: Select **VPC only**
- **Name**: Enter **`ASG VPN`**
- **IPv4 CIDR block**: Enter **`10.11.0.0/16`**

![Create VPC](/images/9/0002.png?featherlight=false&width=90pc)

3. Select Create VPC

![Create VPC](/images/9/0003.png?featherlight=false&width=90pc)

4. Successfully Create VPC

![Create VPC](/images/9/0004.png?featherlight=false&width=90pc)

5. Access VPC Interface

- Select **Subnets**
- Select **Create subnet**

![Create VPC](/images/9/0005.png?featherlight=false&width=90pc)

6. In the Create Subnet Interface

- Select **ASG VPN** VPC

![Create VPC](/images/9/0006.png?featherlight=false&width=90pc)

7. In the Subnet Settings Interface

- **Subnet name**: Enter **`VPN Public`**
- Select **Availability Zone**: **ap-southeast-1a**
- Select **IPv4 CIDR block** as **`10.11.1.0/24`** according to the architecture described

![Create VPC](/images/9/0007.png?featherlight=false&width=90pc)

8. Successfully Created VPN Public

![Create VPC](/images/9/0008.png?featherlight=false&width=90pc)

9. In the VPC Interface

- Select **Subnets**
- Select **VPN Public**
- Select **Actions**
- Select **Edit Subnet Settings**

![Create VPC](/images/9/0009.png?featherlight=false&width=90pc)

10. Execute Auto-assign IP Settings

- Select **Enable auto-assign public IPv4 address**
- Select **Save**

![Create VPC](/images/9/00010.png?featherlight=false&width=90pc)

11. Successful IP Allocation

![Create VPC](/images/9/00011.png?featherlight=false&width=90pc)

12. In the VPC Interface

- Select **Internet Gateway**
- Select **Create Internet Gateway**

![Create VPC](/images/9/00012.png?featherlight=false&width=90pc)

13. In the Create Internet Gateway Interface

- **Name tag**: Enter **`Internet Gateway VPN`**
- Select **Create Internet Gateway**

![Create VPC](/images/9/00013.png?featherlight=false&width=90pc)

14. After Creating Internet Gateway VPN Successfully and State is Detached

- Select **Actions**
- Select **Attach to VPC**

![Create VPC](/images/9/00014.png?featherlight=false&width=90pc)

15. Select VPC ASG VPN, VPC ID Will Be Automatically Filled In

- Select **Attach Internet Gateway**

![Create VPC](/images/9/00015.png?featherlight=false&width=90pc)

16. Attach Succeeds When State is Attached

![Create VPC](/images/9/00016.png?featherlight=false&width=90pc)

17. Create a Route Table to Route Out to the Internet Through the Internet Gateway

- In the VPC Interface
- Select **Route Tables**
- Select **Create Route Table**

![Create VPC](/images/9/00017.png?featherlight=false&width=90pc)

18. In the Create Route Table Interface

- **Name**: Enter **`Route table VPN - Public`**
- Select VPC named **ASG VPN**, VPC ID Will Be Automatically Filled In
- Select **Create Route Table**

![Create VPC](/images/9/00018.png?featherlight=false&width=90pc)
![Create VPC](/images/9/00019.png?featherlight=false&width=90pc)

19. Successfully Created Route Table

- In the Route Table VPN - Public Interface
- Select **Route**
- Select **Edit Route**

![Create VPC](/images/9/00020.png?featherlight=false&width=90pc)

20. In the Edit Routes Interface

- Select **Add Route**
- Fill in the **Destination CIDR**: **`0.0.0.0/0`** representing the Internet
- In the **Target** section, select **Internet Gateway**, then select the **Internet Gateway VPN** we created. Internet Gateway ID Will Be Automatically Filled In
- Select **Save Changes**

![Create VPC](/images/9/00021.png?featherlight=false&width=90pc)
![Create VPC](/images/9/00022.png?featherlight=false&width=90pc)

21. Complete and Test the Route

22. In the Route Table VPN - Public Interface

- Select **Subnet Associations**
- Select **Edit Subnet Associations**

![Create VPC](/images/9/00023.png?featherlight=false&width=90pc)

23. In the Edit Subnet Associations Interface

- Expand the Subnet ID column by dragging the pane to the right
- Select **Subnet VPN Public**
- Select **Save Associations**

![Create VPC](/images/9/00024.png?featherlight=false&width=90pc)

24. Complete and Recheck Routes

![Create VPC](/images/9/00025.png?featherlight=false&width=90pc)
