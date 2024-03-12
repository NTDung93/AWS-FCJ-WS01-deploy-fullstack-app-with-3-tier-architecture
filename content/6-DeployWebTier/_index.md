---
title : "Deploy Web Tier"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---
## Deploy Web Tier"

We will proceed to delete the resources in the following order:

### Terminate EC2 Instances

1. Terminate EC2 instance:
    - Access the Amazon EC2 console at [EC2](https://console.aws.amazon.com/ec2/).
    - On the left navigation bar, select "Instances."
    - Select all EC2 instances related to the lab.
    - Select **Instance state**.
    - Select **Terminate instance**.

   ![Terminate EC2](/images/16/0001.png?featherlight=false&width=90pc)

2. Confirm termination.

   ![Confirm Termination](/images/16/0002.png?featherlight=false&width=90pc)

### Remove NAT Gateway and Elastic IP Address

- Remove NAT Gateway and Elastic IP Address. AWS charges for wasted EIPs, so you need to double-check to avoid unintended charges.
- Visit the Amazon VPC console page at [VPC](https://console.aws.amazon.com/vpc/).
- On the left navigation bar, click "NAT Gateway."
- Select NAT Gateway.
- Click **Action**.
- Click **Delete NAT Gateway**.

   ![Delete NAT Gateway](/images/16/0003.png?featherlight=false&width=90pc)

- Type "delete."
- Click **Delete** to confirm the deletion of NAT Gateway.

   ![Confirm Deletion](/images/16/0004.png?featherlight=false&width=90pc)
   ![Confirm Deletion](/images/16/0005.png?featherlight=false&width=90pc)

### Delete Elastic IP Address

- Continue to delete Elastic IP Address.
- Visit the Amazon VPC console page at [VPC](https://console.aws.amazon.com/vpc/).
- On the left navigation bar, click "Elastic IP."
- Select the Elastic IP Address we created.
- Click **Action**.
- Click **Release Elastic IP Address**.
- Click **Release**.

   ![Release Elastic IP](/images/16/0006.png?featherlight=false&width=90pc)
   ![Release Elastic IP](/images/16/0007.png?featherlight=false&width=90pc)

#### Delete the EC2 Instance connection endpoint
- Access to Endpoint transactions
- Select Action, select Delete VPC endpoints
- Enter delete
![Create VPC](/images/16/00020.png?featherlight=false&width=90pc)

### Delete in the following order:

- VPN Site to Site connection.

   ![VPN Site to Site](/images/16/0008.png?featherlight=false&width=90pc)
   ![VPN Site to Site](/images/16/0009.png?featherlight=false&width=90pc)

- Virtual Private Gateway.

   ![Virtual Private Gateway](/images/16/00010.png?featherlight=false&width=90pc)
   ![Virtual Private Gateway](/images/16/00011.png?featherlight=false&width=90pc)
   ![Virtual Private Gateway](/images/16/00012.png?featherlight=false&width=90pc)
   ![Virtual Private Gateway](/images/16/00013.png?featherlight=false&width=90pc)

- Customer Gateway.

   ![Customer Gateway](/images/16/00014.png?featherlight=false&width=90pc)
   ![Customer Gateway](/images/16/00015.png?featherlight=false&width=90pc)

- VPC ASG VPN.

   ![VPC ASG VPN](/images/16/00016.png?featherlight=false&width=90pc)
   ![VPC ASG VPN](/images/16/00017.png?featherlight=false&width=90pc)

- VPC ASG.

   ![VPC ASG](/images/16/00018.png?featherlight=false&width=90pc)
   ![VPC ASG](/images/16/00019.png?featherlight=false&width=90pc)
