---
title : "Tạo EC2 Instance Connect Endpoint (Optional)"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 4.5 </b> "
---

#### EC2 Instance Connect Endpoint

Trong bước 4.2 Kiểm tra kết nối, các bạn thấy rằng: để truy cập vào **EC2 Private** bạn cần phải:
1. Dùng công cụ **pscp** để copy key pair từ máy của chúng ta vào **EC2 Public**
2. Truy cập vào **EC2 Public**
3. Cấp quyền cho **key pair**
4. SSH tới máy chủ **EC2 Private**

-> Như bạn thấy, lúc này **EC2 Public** đóng vai trò như **Bastion Host** và chúng ta cần trả chi phí cho instance này. Vậy liệu có cách nào giúp tiết kiệm chi phí, giảm các bước cấu hình mà vẫn truy cập vào **EC2 Private** và đảm bảo tính bảo mật hay không?

Vào 13/06/2023, AWS ra mắt chức năng **EC2 Instance Connect Endpoint (EIC Endpoint)** đế giúp cho khách hàng truy cập vào EC2 instance mà không cần đến **public IP addresses**, thông qua giao thức **SSH** và **RDP**.

**EIC Endpoint** thay thế **Bastion Host**, đồng nghĩa loại bỏ khối lượng công việc: patching, managing, auditting và chi phí **Bastion Host** instance trước đây. Không có chi phí bổ sung dối với **EIC Endpoint**, tuy nhiên [chi phí data transfer](https://000034.awsstudygroup.com/vi/8-data-transfer-overview/) sẽ được áp dụng 

#### Kiến trúc mô tả **EIC Endpoint**

![Create VPC](/images/4-CreateEc2Server/4.5-eic/0001.png?featherlight=false&width=90pc)

1. Tạo Security Group cho **EIC Endpoint**

   - Tại khung search, nhập: **security groups**, trong mục features chọn **Security groups**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0002.png?featherlight=false&width=90pc)  

   - Chọn **Create security group**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0003.png?featherlight=false&width=90pc)  

  - Tại mục **Security group name**, nhập ``EIC Endpoint``
  - Tại mục **Description**, nhập ``Allow SSH for MyIP``
  - Tại mục VPC, chọn **ASG VPC**
  - Chọn **Add rule**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0004.png?featherlight=false&width=90pc)  

  - Tại mục **Type**, chọn protocol **SSH**
  - Tại mục **Source**, chọn **My IP** với ý nghĩa: chỉ cho phép địa chỉ IP của bạn với giao thức SSH được đi qua Security group này
  - Các giá trị còn lại vẫn giữ nguyên.
  - Chọn  **Create security group** 
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0005.png?featherlight=false&width=90pc)  

2. Tạo **EC2 Instance Connect Endpoint**

   - Tại khung search, nhập: ``endpoint services`` , trong mục features chọn **endpoint services**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0006.png?featherlight=false&width=90pc)  

   - Chọn **Create endpoint**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0007.png?featherlight=false&width=90pc)  

   - Tại mục **Name tag**, nhập: ``EC2 private endpoint``
   - Tại mục **Service category**, chọn: **EC2 Instance Connect Endpoint**
   - Tại mục **VPC**, chọn **ASG-VPC**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0008.png?featherlight=false&width=90pc)

   - Tại mục **Security groups**, chọn: **EIC Endpoint** đã tạo ở bước 1
   - Tại mục **Subnet**, chọn: **subnet-0da7e5096deb895e1 (Private subnet 2)** là subnet của EC2 Private
   - Chọn **Create endpoint**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/0009.png?featherlight=false&width=90pc)

   - Đợi Status chuyển thành **Available** và qua bước tiếp theo
![Create VPC](/images/4-CreateEc2Server/4.5-eic/00010.png?featherlight=false&width=90pc)

3. Truy cập EC2 Private thông qua **EC2 Instance Connect Endpoint**

- Tại giao diện EC2, tích vào **ô vuông** của EC2 Private
- Tại mục **Public IPv4 address**, kiểm tra và nhận thấy: không có giá trị Public IP - có nghĩa chúng ta không thể truy cập vào EC2 này thông qua Public IP
- Chọn **Connect**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/00011.png?featherlight=false&width=90pc)

- Tại mục **Connection Type** chọn **Connect using EC2 Instance Connect Endpoint**
- Tại mục **EC2 Instance Connect Endpoint** chọn EIC vừa tạo ở bước 2
- Chọn **Connect**
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/00012.png?featherlight=false&width=90pc)

- Chúc mừng bạn đã truy cập thành công EC2 Private thông qua **EC2 Instance Connect Endpoint** chỉ duy nhất từ địa chỉ IP của bạn
 ![Create VPC](/images/4-CreateEc2Server/4.5-eic/00013.png?featherlight=false&width=90pc)

Lưu ý:
- Thông thường, bạn sẽ làm lab bằng user có quyền Admin, trong trường hợp ngược lại, bạn cần tham khảo thêm tài liệu để cấp quyền cho User được phép thao tác các bước như trên. [IAM permissions to use EC2 Instance Connect Endpoint](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/permissions-for-ec2-instance-connect-endpoint.html)