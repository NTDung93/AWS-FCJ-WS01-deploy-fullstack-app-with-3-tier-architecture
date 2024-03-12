---
title : "Test Connection"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---

## Checking Connection

> ℹ️ **Note:** There are several ways to connect to EC2 instances. You can follow the instructions to [connect to EC2 using PuTTY](https://000004.awsstudygroup.com/en/4-launchlinuxinstance/4.2-connectlinuxinstance/). In this lab, we will use [MobaXterm](https://mobaxterm.mobatek.net/) to establish the connection.

1. **Download MobaXterm**

   ![Download MobaXterm](https://mobaxterm.mobatek.net/download.html)

   ![Create VPC](/images/4-CreateEc2Server/4.2-ec2connect/00019-ec2connect.png?featherlight=false&width=90pc)

2. **Access the EC2 Page**

   - Go to the **EC2** page.
   - Select **Instances**.
   - Choose the **EC2 Public** instance.
   - Select **Details**.
   - Locate the **Public IPv4 address**.

   ![Create VPC](/images/7/0001.png?featherlight=false&width=90pc)

3. **Using MobaXterm**

   - After downloading MobaXterm, extract and open it.
   - Select **Session**.

   ![Create VPC](/images/7/0002.png?featherlight=false&width=90pc)

4. **Configuring Session Settings**

   - In the **Session settings** interface, choose **SSH**.

   ![Create VPC](/images/7/0002.png?featherlight=false&width=90pc)

5. **Session Settings Continued**

   - In the **Session settings** interface:
     - Enter the **Remote host** (Public IPv4 address).
     - Specify the **username** as `ec2-user`.
     - Choose the **Use private key** option and provide the path to the `aws-keypair.pem` file created and downloaded during EC2 instance creation.

   ![Create VPC](/images/7/0002.png?featherlight=false&width=90pc)

6. **Successful Connection**

   ![Create VPC](/images/7/0003.png?featherlight=false&width=90pc)

7. **Testing Internet Connection of EC2 Public**

   Execute the following command to test the internet connection of the EC2 Public instance


```
ping amazon.com -c5
```

![Create VPC](/images/7/0004.png?featherlight=false&width=90pc)

8. Make a ping to **EC2 private**

```
ping <IP Private EC2 Private>
```

![Create VPC](/images/7/0005.png?featherlight=false&width=90pc)



## Connect to the EC2 Private Server and Check Internet Connection

9. Access to **EC2**

   - Select **Instances**
   - Select **EC2 Private**
   - Select **Details**
   - Select **Private IPv4 addresses**
   - Then connect SSH to **EC2 Public**

![Create VPC](/images/7/0003.png?featherlight=false&width=90pc)

10. Perform a ping test to the EC2 Private's private IP address to test the connection from the EC2 Public server to the EC2 Private server. Use the following command:


```
ping 10.10.4.105 -c5
```
![Create VPC](/images/7/0005.png?featherlight=false&width=90pc)

11. **EC2 Private** will not have a **public IP address** because we are not assigning this server a public IP. To be able to ssh into **EC2 Private**, we will make an ssh connection from EC2 Public through EC2 Private **private IP address**

     - Download the **pscp** tool to the same folder containing the **aws-keypair.ppk** file to copy the **aws-keypair.pem** file from our computer to **EC2 Public** .

{{% notice info %}}
You download [an RSA and DSA key generation utility](https://the.earth.li/~sgtatham/putty/latest/w64/puttygen.exe) as **puttygen.exe**
{{% /notice %}}

{{% notice info %}}
You download [an SCP client, i.e. command-line secure file copy](https://the.earth.li/~sgtatham/putty/latest/w64/pscp.exe) is **pscp.exe**
{{% /notice %}}

12. We use **puttygen.exe** to generate key

     - Select **Load**

![Create VPC](/images/4-CreateEc2Server/4.2-ec2connect/0009-ec2connect.png?featherlight=false&width=90pc)

13. Select **aws-keypair.pem**

     - Select **OK**
     - Select **Save private key** with the name **aws-keypair.ppk**

![Create VPC](/images/4-CreateEc2Server/4.2-ec2connect/00010-ec2connect.png?featherlight=false&width=90pc)

14. Complete the generation key

![Create VPC](/images/4-CreateEc2Server/4.2-ec2connect/00011-ec2connect.png?featherlight=false&width=90pc)

15. Launch **Command Prompt**. Change the path to the folder you just downloaded **pscp**. Run the command below to upload the **aws-keypair.pem** file to the **/home/ec2-user/** directory of the EC2 Public server.

    - You will need to replace the **public IP address of EC2 Public** parameter before running the command.

```
pscp -i aws-keypair.ppk aws-keypair.pem ec2-user@<EC2 PUBLIC public IP address>:/home/ec2-user/
```

![Create VPC](/images/4-CreateEc2Server/4.2-ec2connect/00012-ec2connect.png?featherlight=false&width=90pc)

16. Access to **EC2**

     - Select **Instances**
     - Select **EC2 Public**
     - Select **Details**
     - View **Public IPv4 address**

![Create VPC](/images/7/0006.png?featherlight=false&width=90pc)

17. Return to the EC2 connection interface. Make sure you copy the **aws-keypair.pem** file to the **EC2 Public** server, we execute the command

```
ls
```

![Create VPC](/images/7/0007.png?featherlight=false&width=90pc)

18. Update the permissions for the **aws-keypair.pem** file by running the **chmod 400 aws-keypair.pem** command. AWS requires the key pair file to be restricted before it can be used to connect to the EC2 server.

```
chmod 400 aws-keypair.pem
```
![Create VPC](/images/7/0008.png?featherlight=false&width=90pc)

19. **SSH** to **EC2 Private** server

```
ssh -i aws-keypair.pem ec2-user@<EC2 Private server's private IP address>
```

![Create VPC](/images/7/0009.png?featherlight=false&width=90pc)

20. Perform **ping test to amazon.com**. As you can see, we cannot connect **internet from EC2 Private**. In the next step, we will create **NAT Gateway** to allow the **EC2 Private** server to connect to the internet in the outbound direction. Keep the connection to **EC2 Private** so that we can check the connection to **internet** after finishing creating and configuring **NAT Gateway**.

```
ping amazon.com
```

![Create VPC](/images/7/00010.png?featherlight=false&width=90pc)