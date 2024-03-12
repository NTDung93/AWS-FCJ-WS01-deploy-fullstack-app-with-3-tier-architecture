---
title : "Customer Gateway Configuration"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 5.2.4 </b> "
---

# Configure Customer Gateway

1. Access to VPC
- Select **Site-to-Site VPN Connection**
- Select **VPN Connection** created
- Select **Download Configuration**

![Create VPC](/images/13/0001.png?featherlight=false&width=90pc)

2. Download Configuration
In the **Download Configuration** dialog, choose the appropriate **appliance**, e.g., **OpenSwan**.

- **Vendor**: Select **OpenSwan**
- **Platform**: Select **OpenSwan**
- **Software**: Select **OpenSwan 2.6.38+**
- **IKE version**: Select **ikev1**
- Select **Download**.

![Create VPC](/images/13/0002.png?featherlight=false&width=90pc)

3. Save the image file information to the folder used for storing the key pair and lab tools. Modify the configuration based on your device.

![Create VPC](/images/13/0003.png?featherlight=false&width=90pc)

Connect SSH to **EC2 Customer Gateway**.

![Create VPC](/images/13/0004.png?featherlight=false&width=90pc)

4. Install **OpenSwan**

```
sudo su
yum install openswan -y
```
![Create VPC](/images/13/0005.png?featherlight=false&width=90pc)


5. Check the configuration file **/etc/ipsec.conf**

```
vi /etc/ipsec.conf
```
- Check the configuration is as shown below.

![Create VPC](/images/13/0006.png?featherlight=false&width=90pc)

- Press the **ESC** key and the combination **:q!** to exit the **vi** editor.

6. Configuration file **/etc/sysctl.conf**

```
vi /etc/sysctl.conf
```

![Create VPC](/images/13/0007.png?featherlight=false&width=90pc)

- Move down to the last position in the configuration file. Press the **i** key to proceed with editing the file.
- Add the following configuration at the end of the configuration file.

```
net.ipv4.ip_forward = 1
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.all.send_redirects = 0
```
- Press the **ESC** key and the combination **:wq!** to save the configuration file.

![Create VPC](/images/13/0008.png?featherlight=false&width=90pc)

7. Then to apply this configuration, run the command:

```
sysctl -p
```

![Create VPC](/images/13/0009.png?featherlight=false&width=90pc)

8. Next we will configure the file **/etc/ipsec.d/aws.conf**

   
```
vi /etc/ipsec.d/aws.conf
```

   - Press **i** to proceed to edit the file.
   - Add the following configuration to the configuration file. We will create **2 Tunnel** with information taken from the **VPN Connection** configuration file you downloaded and saved in the folder containing the key pair earlier.
   - Make sure you edit the IP address and network class accordingly before copying the above configuration.
   - For **Amazon Linux**, we will omit the **auth=esp** line in the original configuration file.
   - Since we only have **1 public IP addres** for **Customer Gateway**, we will need to configure **overlapip=yes**.
   - **leftid**: **IP Public Address on the Onprem side**. (Here is **public IP** of **EC2 Customer Gateway in ASG VPN VPC**) .
   - **right**: **IP Public Address on AWS VPN Tunnel** side.
   - **leftsubnet**: **CIDR of Local Side Network** (If there are multiple network layers, you can leave it as **0.0.0.0/0**).
   - **rightsubnet**: **CIDR of Private Subnet on AWS**.

  
```
conn Tunnel1
	authby=secret
	auto=start
	left=%defaultroute
	leftid=13.229.235.99
	right=52.220.214.148
	type=tunnel
	ikelifetime=8h
	keylife=1h
	phase2alg=aes128-sha1;modp1024
	ike=aes128-sha1;modp1024
	keyingtries=%forever
	keyexchange=ike
	leftsubnet=<LOCAL NETWORK>
	rightsubnet=<REMOTE NETWORK>
	dpddelay=10
	dpdtimeout=30
	dpdaction=restart_by_peer
 	overlapip=yes

conn Tunnel2
	authby=secret
	auto=start
	left=%defaultroute
	leftid=13.229.235.99
	right=54.179.66.207
	type=tunnel
	ikelifetime=8h
	keylife=1h
	phase2alg=aes128-sha1;modp1024
	ike=aes128-sha1;modp1024
	keyingtries=%forever
	keyexchange=ike
	leftsubnet=<LOCAL NETWORK>
	rightsubnet=<REMOTE NETWORK>
	dpddelay=10
	dpdtimeout=30
	dpdaction=restart_by_peer
 	overlapip=yes
```

![Create VPC](/images/13/00010.png?featherlight=false&width=90pc)

- Press the **ESC** key and the combination **:wq!** to save the configuration file.

9. Check the next step in the configuration file we downloaded.

![Create VPC](/images/13/00011.png?featherlight=false&width=90pc)

10. Create and configure the file **etc/ipsec.d/aws.secrets** Create a new file with the following configuration to set up authentication for the 2 Tunnels.

    - Run the command **touch /etc/ipsec.d/aws.secrets** to create the file.

```
touch /etc/ipsec.d/aws.secrets
```
![Create VPC](/images/13/00012.png?featherlight=false&width=90pc)

    - Run the command **vi /etc/ipsec.d/aws.secrets**

```
vi /etc/ipsec.d/aws.secrets
```

11. Press the **i** key to edit the file.

    - Add the following configuration to the end of the configuration file (this configuration is in step 5 of **IPSEC Tunnel #1** and **IPSEC Tunnel #2**)

```
13,229,235.99 52,220,214,148: PSK "zkq_xvwpA5HNictmh6x6tVCKozVHxcpA"
13,229,235.99 54,179,66,207: PSK "c0WdOkBj4gtJ2jaGrmeA2bZ_4ZaN50o3"
```

![Create VPC](/images/13/00013.png?featherlight=false&width=90pc)

    - Press the **ESC** key and the combination **:wq!** to save the configuration file.
    - Run the command **cat /etc/ipsec.d/aws.secrets** to check the content of the configuration file

![Create VPC](/images/13/00014.png?featherlight=false&width=90pc)

12. Restart **Network service & IPSEC service**

```
service network restart
chkconfig ipsec on
service ipsec start
service ipsec status
```

![Create VPC](/images/13/00015.png?featherlight=false&width=90pc)


- If the status tunnel is still not running correctly, after checking and updating the configuration you will need to run the command to **restart** **service network and IPsec** :

```
sudo service network restart
sudo service ipsec restart
```

![Create VPC](/images/13/00016.png?featherlight=false&width=90pc)


13. After completing the configuration.Try to ping from the **Customer Gateway** server side to the **EC2 Private** server. If the VPN configuration is successful you will get the result as below.

```
ping <EC2 Private IP> -c5
```

![Create VPC](/images/13/00017.png?featherlight=false&width=90pc)

![Create VPC](/images/13/00018.png?featherlight=false&width=90pc)


14. After completing the configuration.Try to ping from the **EC2 Private** server side to the **Customer Gateway** server. If the VPN configuration is successful you will get the result as below.

```
ping <Customer gateway instance IP> -c5
```

![Create VPC](/images/13/00019.png?featherlight=false&width=90pc)

![Create VPC](/images/13/00020.png?featherlight=false&width=90pc)