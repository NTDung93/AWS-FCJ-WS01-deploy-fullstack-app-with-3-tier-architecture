---
title : "Cấu hình Customer Gateway"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 5.2.4 </b> "
---

#### Cấu hình Customer Gateway

1. Truy cập vào **VPC**

   - Chọn **Site-to-Site VPN Connection**
   - Chọn **VPN Connection** đã tạo 
   - Chọn **Download Configuration**

![Create VPC](/images/13/0001.png?featherlight=false&width=90pc)

2. Trong hộp thoại **Download Configuration**, lựa chọn **appliance** phù hợp với bạn: Trong bài thực hành này, chúng ta sẽ sử dụng **OpenSwan**.

   - **Vendor**: Chọn **OpenSwan**
   - **Platform**: Chọn **OpenSwan**
   - **Software**: Chọn **OpenSwan 2.6.38+**
   - **IKE version**: Chọn **ikev1**
   - Chọn **Download**.

![Create VPC](/images/13/0002.png?featherlight=false&width=90pc)

3. Lưu thông tin file câu hình vào thư mục chúng ta sử dụng lưu trữ key pair và công cụ cho bài lab.

   - Sau đó dựa vào cấu hình được cung cấp, bạn thay đổi các thông tin phù hợp và cấu hình cho thiết bị của mình.

![Create VPC](/images/13/0003.png?featherlight=false&width=90pc)

   - Kết nối ssh vào **EC2 Customer Gateway**.
  
![Create VPC](/images/13/0004.png?featherlight=false&width=90pc)


4. Cài đặt **OpenSwan**

```
sudo su
yum install openswan -y
```
![Create VPC](/images/13/0005.png?featherlight=false&width=90pc)


5. Kiểm tra cấu hình file **/etc/ipsec.conf**

```
vi /etc/ipsec.conf
```
- Kiểm tra cấu hình đang như hình dưới.

![Create VPC](/images/13/0006.png?featherlight=false&width=90pc)

- Ấn phím **ESC** và tổ hợp **:q!** để thoát khỏi trình chỉnh sửa **vi**.

6. Cấu hình file **/etc/sysctl.conf**

```
vi /etc/sysctl.conf
```

![Create VPC](/images/13/0007.png?featherlight=false&width=90pc)

- Chuyển xuống vị trí cuối cùng trong file cấu hình. Ấn phím **i** để tiến hành chỉnh sửa file.
- Thêm cấu đoạn sau vào cuối tập tin cấu hình.

```
net.ipv4.ip_forward = 1
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.all.send_redirects = 0
```

- Ấn phím **ESC** và tổ hợp **:wq!** để lưu file cấu hình.

![Create VPC](/images/13/0008.png?featherlight=false&width=90pc)

7. Sau đó để áp dụng cấu hình này, chạy lệnh:

```
sysctl -p
```

![Create VPC](/images/13/0009.png?featherlight=false&width=90pc)

8. Tiếp theo chúng ta sẽ cấu hình file **/etc/ipsec.d/aws.conf**

   
```   
vi /etc/ipsec.d/aws.conf
```

   - Ấn phím **i** để tiến hành chỉnh sửa file.
   - Thêm cấu đoạn sau vào tập tin cấu hình. Chúng ta sẽ tạo **2 Tunnel** với thông tin được lấy từ file cấu hình **VPN Connection** bạn đã tải về và lưu chung vào thư mục chứa key pair trước đó.
   - Đảm bảo bạn chỉnh sửa địa chỉ IP và lớp mạng phù hợp trước khi copy đoạn cấu hình trên.
   - Đối với **Amazon Linux** thì chúng ta sẽ bỏ dòng **auth=esp** trong file cấu hình gốc.
   - Vì chúng ta chỉ có **1 public IP addres** cho **Customer Gateway** nên sẽ cần thêm cấu hình **overlapip=yes**.
   - **leftid**: **IP Public Address phía Onprem**. ( Ở đây chính là **IP public** của **EC2 Customer Gateway trong ASG VPN VPC**) .
   - **right**: **IP Public Address phía AWS VPN Tunnel**. 
   - **leftsubnet**: **CIDR của Mạng phía Local** (Nếu có nhiều lớp mạng, bạn có thể để là **0.0.0.0/0**).
   - **rightsubnet**: **CIDR của Mạng phía Private Subnet trên AWS**.
  
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

   - Ấn phím **ESC** và tổ hợp **:wq!** để lưu file cấu hình.

9. Kiểm tra bước tiếp theo trong file cấu hình chúng ta đã tải xuống.

![Create VPC](/images/13/00011.png?featherlight=false&width=90pc)

10. Tạo mới và cấu hình file **etc/ipsec.d/aws.secrets** Tạo tập tin mới với cấu hình sau để thiết lập chứng thực cho 2 Tunnel.

    - Chạy lệnh **touch /etc/ipsec.d/aws.secrets** để tạo tập tin.

```
touch /etc/ipsec.d/aws.secrets
```
![Create VPC](/images/13/00012.png?featherlight=false&width=90pc)

    - Chạy lệnh **vi /etc/ipsec.d/aws.secrets**

```
vi /etc/ipsec.d/aws.secrets
```

11.  Ấn phím **i** để tiến hành chỉnh sửa file.

    - Thêm cấu đoạn sau vào cuối tập tin cấu hình (đoạn cấu hình này ở bước 5 của **IPSEC Tunnel #1** và **IPSEC Tunnel #2**)

```
13.229.235.99 52.220.214.148: PSK "zkq_xvwpA5HNictmh6x6tVCKozVHxcpA"
13.229.235.99 54.179.66.207: PSK "c0WdOkBj4gtJ2jaGrmeA2bZ_4ZaN50o3"
```

![Create VPC](/images/13/00013.png?featherlight=false&width=90pc)

    - Ấn phím **ESC** và tổ hợp **:wq!** để lưu file cấu hình.
    - Chạy lệnh **cat /etc/ipsec.d/aws.secrets** để kiểm tra nội dung file cấu hình

![Create VPC](/images/13/00014.png?featherlight=false&width=90pc)

12.  Khởi động lại **Network service & IPSEC service**

```
service network restart 
chkconfig ipsec on
service ipsec start
service ipsec status
```

![Create VPC](/images/13/00015.png?featherlight=false&width=90pc)


- Nếu status tunnel vẫn chưa chạy đúng, sau khi kiểm tra và cập nhật cấu hình bạn sẽ cần chạy lệnh để **restart** lại **service network và IPsec** :

```
sudo service network restart
sudo service ipsec restart
```

![Create VPC](/images/13/00016.png?featherlight=false&width=90pc)


13. Sau khi hoàn tất cấu hình.Hãy thử thực hiện lệnh ping từ phía máy chủ **Customer Gateway** tới máy chủ **EC2 Private**. Nếu cấu hình VPN thành công bạn sẽ được kết quả như dưới đây.

```
ping <EC2 Private IP> -c5
```

![Create VPC](/images/13/00017.png?featherlight=false&width=90pc)

![Create VPC](/images/13/00018.png?featherlight=false&width=90pc)


14.  Sau khi hoàn tất cấu hình.Hãy thử thực hiện lệnh ping từ phía máy chủ **EC2 Private** tới máy chủ **Customer Gateway** . Nếu cấu hình VPN thành công bạn sẽ được kết quả như dưới đây.

```
ping <Customer gateway instance IP> -c5
```

![Create VPC](/images/13/00019.png?featherlight=false&width=90pc)

![Create VPC](/images/13/00020.png?featherlight=false&width=90pc)
