---
title : "Create NAT Gateway"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---

## Create NAT Gateway

1. Access **EC2**:
   - Select **Elastic IPs**
   - Select **Allocate Elastic IP address**

![Create VPC](/images/8/0001.png?featherlight=false&width=90pc)

2. In the **Allocate Elastic IP address** interface:
   - **Public IPv4 address pool**: Select **Amazon's pool of IPv4 addresses**
   - Select **Allocate**

![Create VPC](/images/8/0002.png?featherlight=false&width=90pc)

3. Successfully created a **Public IP Address**

![Create VPC](/images/8/0003.png?featherlight=false&width=90pc)

4. Access **VPC**:
   - Select **NAT Gateways**
   - **Create NAT gateway**

![Create VPC](/images/8/0004.png?featherlight=false&width=90pc)

5. In **NAT gateway** interface:
   - **Name**: Enter **`NAT gateway`**
   - **Subnet**: Select **Public subnet 2**
   - **Connectivity type**: Select **Public**
   - **Elastic IP allocation ID**: Select recently created **Elastic IP**

![Create VPC](/images/8/0005.png?featherlight=false&width=90pc)

6. Select **Create NAT gateway**

![Create VPC](/images/8/0006.png?featherlight=false&width=90pc)

7. Successfully created **NAT gateway**

![Create VPC](/images/8/0007.png?featherlight=false&width=90pc)

## Create Route table - Private and assign to private subnets

8. In the **VPC** interface:
   - Select **Route Tables**
   - Select **Create route table**

![Create VPC](/images/8/0008.png?featherlight=false&width=90pc)

9. In the **Route table** interface:
   - **Name**: Enter **`Route table - Private`**
   - **VPC**: Select **ASG** VPC
   - Select **Create route table**

![Create VPC](/images/8/0009.png?featherlight=false&width=90pc)
![Create VPC](/images/8/00010.png?featherlight=false&width=90pc)

10. Finish creating **Route table - Private**

![Create VPC](/images/8/00011.png?featherlight=false&width=90pc)

11. In the **Route table - Private** interface:
    - Select **Subnet Associations**
    - Select **Edit subnet associations**

![Create VPC](/images/8/00012.png?featherlight=false&width=90pc)

12. In the **Edit subnet associations** interface:
    - Choose 2 private subnets
    - Select **Save associations**

![Create VPC](/images/8/00013.png?featherlight=false&width=90pc)

13. In the **Route table - Private** interface:
    - Select **Routes**
    - Select **Edit routes**

![Create VPC](/images/8/00014.png?featherlight=false&width=90pc)

14. In the **Edit routes** interface:
    - Select **Add route**
    - **Destination**: **0.0.0.0/0**
    - **Target**: **NAT Gateway**
    - Select **Save changes**

![Create VPC](/images/8/00015.png?featherlight=false&width=90pc)
![Create VPC](/images/8/00016.png?featherlight=false&width=90pc)

15. Double check **Routes**

![Create VPC](/images/8/00017.png?featherlight=false&width=90pc)

16. Test ping `amazon.com` successfully from EC2 Private:

```
ping amazon.com -c5
```

![Create VPC](/images/8/00018.png?featherlight=false&width=90pc)