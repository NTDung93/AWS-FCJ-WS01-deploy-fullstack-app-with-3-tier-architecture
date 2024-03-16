---
title : "Chạy ứng dụng trên EC2 instance"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4.4 </b> "
---

#### Chạy ứng dụng trên EC2 instance

{{% notice info %}}
Ý tưởng: Ta sẽ build ra file jar của app, sau đó upload file jar đó lên s3 bucket. Tiếp đó tải file jar lên ec2 instance và chạy file jar trên instance.
{{% /notice %}}

1. Tải java 17 trên instance bằng lệnh **`sudo yum install java-17-amazon-corretto-headless`**. Sau đó check tải thành công bằng lệnh **`java -version`**
!![run app](/workshop01-AWS-FCJ-2024/images/4-4/01.png?width=50pc)

2. Để generate ra file jar của app, ta vào IDE, mở project back end, truy cập vào **Maven**, chuột phải vào **install** trong **Lifecycle** và chọn **Run Maven Build**.
!![run app](/workshop01-AWS-FCJ-2024/images/4-4/02.png?width=50pc)

3. Hoàn thành tạo file jar của app, file jar vừa tạo sẽ nằm trong folder target
!![run app](/workshop01-AWS-FCJ-2024/images/4-4/03.png?width=50pc)

4. Truy cập vào S3, vào bucket đã tạo, tạo folder mới tên **`library-app-be`**. Sau khi tạo xong folder, ta upload file jar vừa tạo bằng cách kéo thả vào folder
!![run app](/workshop01-AWS-FCJ-2024/images/4-4/04.png?width=50pc)

5. Trước khi download s3 lên instance, ta cần **make s3 public** bằng cách thêm policy cho nó:
   - Chọn s3 bucket đã tạo, vào **tab permission**
   - Ở **Bucket policy** chọn edit và paste đoạn mã sau vào, sau đó nhấn **Save changes**
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::demowebapp-workshop-01/*"
        }
    ]
}
```
![run app](/workshop01-AWS-FCJ-2024/images/4-4/05.png?width=50pc)

6. Truy cập vào file jar trên bucket và copy **Object URL** của nó
![run app](/workshop01-AWS-FCJ-2024/images/4-4/06.png?width=50pc)

7. Ở session manager, chạy lệnh **sudo wget <Object URL>** (**`sudo wget https://demowebapp-workshop-01.s3.ap-southeast-1.amazonaws.com/library-app-be/library-app-be-0.0.1-SNAPSHOT.jar`**) để tải file jar lên instance
![run app](/workshop01-AWS-FCJ-2024/images/4-4/07.png?width=50pc)

8. Chạy lệnh **`java -jar library-app-be-0.0.1-SNAPSHOT.jar`** để chạy app trên instance
![run app](/workshop01-AWS-FCJ-2024/images/4-4/08.png?width=50pc)

9. Để có thể tạm test bằng **Postman**, ta có thể tạm thời gán **public-route-table** (mục đích để có thể sử dụng IGW) cho **private-subnet-1** (subnet chứa ec2 instance)
![run app](/workshop01-AWS-FCJ-2024/images/4-4/09.png?width=50pc)

10. Truy cập postman, ta có thể sử dụng **Public IPv4 address** hoặc **Public IPv4 DNS** để gọi tới các API
![run app](/workshop01-AWS-FCJ-2024/images/4-4/10.png?width=50pc)
   - sử dụng **Public IPv4 address**
![run app](/workshop01-AWS-FCJ-2024/images/4-4/11.png?width=50pc)
   - sử dụng **Public IPv4 DNS**
![run app](/workshop01-AWS-FCJ-2024/images/4-4/12.png?width=50pc)

11. Để có thể giữ cho app chạy sau khi terminate session, chúng ta sẽ sử dụng nohup bằng lệnh sau **nohup java -jar <jar file name>** (ex: **`nohup java -jar library-app-be-0.0.1-SNAPSHOT.jar`**)
![run app](/workshop01-AWS-FCJ-2024/images/4-4/13.png?width=50pc)

12. Để dừng app sau khi chạy bằng nohup, ta chạy lệnh sau **`pkill -f 'java -jar library-app-be-0.0.1-SNAPSHOT.jar'`**
![run app](/workshop01-AWS-FCJ-2024/images/4-4/14.png?width=50pc)

{{% notice note %}}
Nhưng ta cần phải tìm cách để app chạy tự động sau khi instance reboot, vì vậy ta sẽ sử dụng **systemd** để tạo service cho app (run java app as a service)
{{% /notice %}}

13. Ta sẽ chạy lần lượt các lệnh sau:
   - **`sudo chmod +x /home/ec2-user/library-app-be-0.0.1-SNAPSHOT.jar`**
   - **`sudo vim /etc/systemd/system/library.service`**	

**Insert the code below into your-application.service:**

```
[Unit]
Description=Java Application as a Service
After=syslog.target

[Service]
User=ec2-user
ExecStart=ExecStart=/usr/bin/java -jar /home/ec2-user/library-app-be-0.0.1-SNAPSHOT.jar
SuccessExitStatus=143

[Install]
WantedBy=multi-user.target
```
   - **`cd /etc/systemd/system/`**
   - **`sudo chmod 777 library.service`**
   - **`sudo nano library.service`**
   - **`sudo systemctl daemon-reload`**
   - **`sudo systemctl enable library.service`**
   - **`sudo systemctl start library.service`**
   - **`sudo systemctl status library.service -l`**
   - **`sudo systemctl stop library.service`**