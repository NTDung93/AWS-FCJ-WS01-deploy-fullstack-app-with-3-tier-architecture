---
title : "Triển khai Web Tier"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---
#### Triển khai Web Tier"

Chúng ta sẽ tiến hành xóa các tài nguyên theo thứ tự sau

### Terminate các EC2 Instance.
1. Terminate EC2 instance.
    - Truy cập Amazon EC2 console tại địa chỉ [EC2](https://console.aws.amazon.com/ec2/).
    - Trên thanh điều hướng bên trái, chọn Intances
    - Chọn tất cả EC2 Instance liên quan tới bài lab.
    - Chọn **Instance state**
    - Chọn **Terminate instance**

![Create VPC](/images/16/0001.png?featherlight=false&width=90pc)

2. Xác nhận terminate.

![Create VPC](/images/16/0002.png?featherlight=false&width=90pc)

#### Xóa NAT Gateway, Elastic IP Address 

- Xóa NAT Gateway và Elastic IP Address. AWS sẽ thu tiền cho các EIP lãng phí nên bạn cần kiểm tra kỹ để tránh bị trừ chi phí ngoài ý muốn.
- Truy cập trang Amazon VPC console tại địa chỉ [VPC](https://console.aws.amazon.com/vpc/)
- Trên thanh điều hướng bên trái , click NAT Gateway.
- Chọn NAT Gateway.
- Click Action.
- Click Delete NAT Gateway.

![Create VPC](/images/16/0003.png?featherlight=false&width=90pc)

- Gõ delete.
- Click Delete để xác nhận xóa NAT Gateway

![Create VPC](/images/16/0004.png?featherlight=false&width=90pc)

![Create VPC](/images/16/0005.png?featherlight=false&width=90pc)

#### Xóa xóa Elastic IP Address.
- Tiếp tục xóa Elastic IP Address.
- Truy cập trang Amazon VPC console tại địa chỉ https://console.aws.amazon.com/vpc/
- Trên thanh điều hướng bên trái , click Elastic IP.
- Chọn Elastic IP Address chúng ta đã tạo.
- Click Action.
- Click Release Elastic IP Address
- Click Release.

![Create VPC](/images/16/0006.png?featherlight=false&width=90pc)

![Create VPC](/images/16/0007.png?featherlight=false&width=90pc)

#### Xóa EC2 Instance concect endpoint
- Truy cập vào giao dịch Endpoint
- Chọn Action, chọn Delete VPC endpoints
- Nhập delete
![Create VPC](/images/16/00020.png?featherlight=false&width=90pc)

#### Tiếp tục làm tương tự và xóa theo thứ tự sau nhé:
- VPN Site to Site connection.

![Create VPC](/images/16/0008.png?featherlight=false&width=90pc)

![Create VPC](/images/16/0009.png?featherlight=false&width=90pc)

- Virtual Private Gateway.
  
![Create VPC](/images/16/00010.png?featherlight=false&width=90pc)

![Create VPC](/images/16/00011.png?featherlight=false&width=90pc)

![Create VPC](/images/16/00012.png?featherlight=false&width=90pc)

![Create VPC](/images/16/00013.png?featherlight=false&width=90pc)

- Customer Gateway.

![Create VPC](/images/16/00014.png?featherlight=false&width=90pc)


![Create VPC](/images/16/00015.png?featherlight=false&width=90pc)

- VPC ASG VPN

![Create VPC](/images/16/00016.png?featherlight=false&width=90pc)

![Create VPC](/images/16/00017.png?featherlight=false&width=90pc)

- VPC ASG.

![Create VPC](/images/16/00018.png?featherlight=false&width=90pc)

![Create VPC](/images/16/00019.png?featherlight=false&width=90pc)