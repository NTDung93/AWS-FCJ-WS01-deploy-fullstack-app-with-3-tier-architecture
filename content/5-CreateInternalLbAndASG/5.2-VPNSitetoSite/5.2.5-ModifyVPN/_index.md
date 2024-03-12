---
title : "Modify AWS VPN Tunnel"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 5.2.5 </b> "
---

## Modify AWS VPN Tunnel

1. Access the **VPC** Interface:

   - Go to **Site-to-Site VPN connections**.
   - Choose the recently created **VPN**.
   - Click on **Actions**.
   - Select **Modify VPN tunnel options**.

   ![Step 1](/images/13/00023.png?featherlight=false&width=90pc)

2. Choose the **VPN Tunnel Outside IP Address**:

   ![Step 2](/images/13/00024.png?featherlight=false&width=90pc)

3. Confirm UP Tunnel Modification and Keep Other Parameters Default:

   ![Step 3](/images/13/00025.png?featherlight=false&width=90pc)

4. Enable Tunnel Activity Log:

   - Enable **Tunnel activity log**.
   - Choose an existing **Amazon CloudWatch log group** (or create one in CloudWatch if not already done).
   - Set **Output format** to **text**.
   - Click **Save changes**.

   ![Step 4](/images/13/00026.png?featherlight=false&width=90pc)

5. Access **CloudWatch**:

   - Navigate to **Log groups**.
   - Go to **Log streams**.
   - Choose a log stream.

   ![Step 5](/images/1300027.png?featherlight=false&width=90pc)

6. View **Log Events**:

   ![Step 6](/images/13/00028.png?featherlight=false&width=90pc)

7. Repeat the Process for the Remaining Tunnel(s):

   ![Step 7](/images/13/00029.png?featherlight=false&width=90pc)

8. Verify That Both Tunnels are UP:

   ![Step 8](/images/13/00030.png?featherlight=false&width=90pc)
