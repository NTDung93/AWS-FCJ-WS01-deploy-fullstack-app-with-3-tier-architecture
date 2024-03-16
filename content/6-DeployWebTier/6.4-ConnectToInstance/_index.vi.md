---
title : "Kết nối tới EC2 instance"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 6.4 </b> "
---

#### Kết nối tới EC2 instance
1. Làm tương tự như khi kết nối vào instance của app server, ta connect thông qua **Session manager**.
![](/workshop01-AWS-FCJ-2024/images/6-4/01.png?width=50pc)

2. Switch qua ec2-user.
![](/workshop01-AWS-FCJ-2024/images/6-4/02.png?width=50pc)

3. Kiểm tra kết nối bằng việc ping tới ip của Google DNS server → kết nối được internet thông qua IGW.
![](/workshop01-AWS-FCJ-2024/images/6-4/03.png?width=50pc)


4. Tải **NPM** về instance:
    - **`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash`**
    - **`source ~/.bashrc`** để reload the bash shell configuration file thì mới apply được npm vừa tải
![](/workshop01-AWS-FCJ-2024/images/6-4/04.png?width=50pc)
    - Chạy **`nvm install 16`** sau đó chạy **`nvm use 16`** để tải và sử dụng **Node.js version 16**
![](/workshop01-AWS-FCJ-2024/images/6-4/05.png?width=50pc)

5. Để copy code từ folder **library-app-fe** từ **S3 bucket** ta chạy những lệnh sau:
    - **`cd`** để về **user’s home directory**
    - **`aws s3 cp s3://demowebapp-workshop-01/library-app-fe/ web-tier --recursive`** để copy tất cả các file từ folder library-app-fe và các sub-folder của nó về folder web-tier ở instance (nếu chưa tồn tại folder web-tier, instance sẽ tự động tạo mới folder)
![](/workshop01-AWS-FCJ-2024/images/6-4/06.png?width=50pc)

6. Tải các dependencies:
    - **`cd web-tier`** để truy cập vào folder
    - **`ls -ltr`** để list các file và sub-folder của web-tier
![](/workshop01-AWS-FCJ-2024/images/6-4/07.png?width=50pc)
    - **`npm install`** để tải các thư viện hay phụ thuộc cần thiết
![](/workshop01-AWS-FCJ-2024/images/6-4/08.png?width=50pc)
![](/workshop01-AWS-FCJ-2024/images/6-4/09.png?width=50pc)
    - **`npm run build`** để build source code
![](/workshop01-AWS-FCJ-2024/images/6-4/10.png?width=50pc)
    - **`sudo amazon-linux-extras install nginx1 -y`** để tải nginx (nginx đóng vai trò như 1 web server để giúp app chạy trên port 80, cũng như giúp direct API calls tới internal load balancer)
7. Config Nginx:
    - **`cd /etc/nginx`**
    - **`ls`**
    - Chúng ta sẽ thấy có file **nginx.conf** ở trong folder nginx. Chúng ta cần **xóa file** này đi và **replace** bằng file mà ta đã config và up trên s3 bucket.
![](/workshop01-AWS-FCJ-2024/images/6-4/11.png?width=50pc)
    - **`sudo rm nginx.conf`**
    - **`sudo aws s3 cp s3://demowebapp-workshop-01/nginx.conf .`** để copy file trên bucket về folder nginx
![](/workshop01-AWS-FCJ-2024/images/6-4/12.png?width=50pc)
    - **`sudo service nginx restart`** để restart Nginx
    - **`chmod -R 755 /home/ec2-user`** để cấp quyền cho Nginx access vào các tất cả các files
    - **`sudo chkconfig nginx on`** để chạy Nginx service tự động mỗi khi instance restart