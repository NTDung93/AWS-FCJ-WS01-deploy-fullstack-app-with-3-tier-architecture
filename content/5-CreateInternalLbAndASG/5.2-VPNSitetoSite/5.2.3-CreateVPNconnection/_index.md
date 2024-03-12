---
title : "Create VPN Connection"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 5.2.3 </b> "
---

## Create a VPN Connection

1. Access **VPC**:
   - Select **Site-to-Site VPN Connections**
   - Select **Create VPN Connection**

   ![Create VPC](/images/12/0004.png?featherlight=false&width=90pc)

2. In the **Create VPN Connection** Interface:
   - **Name Tag**: Enter **`VPN Connection`**
   - **Target Gateway Type**: Select **Virtual Private Gateway**
   - **Virtual Private Gateway**: Select **VPN Gateway**
   - **Customer Gateway**: **Existing**
   - **Customer Gateway ID**: Select **Customer Gateway**

   ![Create VPC](/images/12/0005.png?featherlight=false&width=90pc)

3. Continue to Perform Configuration:
   - **Routing Options**: **Static**
   - **Static IP Prefixes**: **10.11.0.0/16**. This is the IP address resolution in a simulated On-premise environment.
   - Other configurations keep the default.

   ![Create VPC](/images/12/0007.png?featherlight=false&width=90pc)

4. Select **Create VPN Connection**

   ![Create VPC](/images/12/0006.png?featherlight=false&width=90pc)

5. Wait for about 5 minutes to finish creating the **VPN Connection**

   ![Create VPC](/images/12/0009.png?featherlight=false&width=90pc)

6. Configure **Propagation** for **Route Tables**:
   - In the **VPC** interface, select **Route Tables**
   - Select **Route table - Public**
   - Select **Route Propagation**
   - Select **Edit Route Propagation**

   ![Create VPC](/images/12/00010.png?featherlight=false&width=90pc)

7. In the **Edit Route Propagation** Interface:
   - Select **Enable**
   - Select **Save**

   ![Create VPC](/images/12/00011.png?featherlight=false&width=90pc)

8. Complete and Recheck: **Route Propagation** should have changed to **Yes**

   ![Create VPC](/images/12/00012.png?featherlight=false&width=90pc)

9. Similar Route Propagation for Private Subnet:

   ![Create VPC](/images/12/00013.png?featherlight=false&width=90pc)
   ![Create VPC](/images/12/00014.png?featherlight=false&width=90pc)
   ![Create VPC](/images/12/00015.png?featherlight=false&width=90pc)
