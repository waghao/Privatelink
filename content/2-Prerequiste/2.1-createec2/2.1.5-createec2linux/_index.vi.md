---
title : "Tạo EC2 Backend"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 2.1.4 </b> "
---

1. Truy cập [giao diện quản trị dịch vụ EC2](https://console.aws.amazon.com/ec2/v2/home)
  + Click **Instances**.
  + Click **Launch instances**.
  
![EC2](/images/2.prerequisite/8-ec2-1.png)

2. Tại trang **Step 1: Choose an Amazon Machine Image (AMI)**.
  + Click **Select** để lựa chọn AMI **Amazon Linux 2023 AMI**.
  
   Tại trang **Step 2: Choose an Instance Type**.
 + Click chọn Instance type **t2.micro**.
 
![EC2](/images/2.prerequisite/9-ec2-2.png)

3. Tại mục **Key pair (login)**
  + Chọn **Create new key pair**
  + Tại mục **Key pair name** nhập **Backend-EC2Key**.
  + Tại mục **Key pair type** chọn **RSA**
  + Tại mục **Private key file format** Chọn **.pem**
  + Click **Create key pair**.

![EC2](/images/2.prerequisite/10-keypema1.png)

4. Tại mục **Network settings** 
  + Click **Edit** 
  + Tại mục **VPC - required** Chọn **VCP-Provider**
  + Tiếp tục **Subnet** Chọn **Provider-Subnet-1**
  + Phần **Firewall(security groups)** Chọn **Select existing security group**
  + **Common security groups** Chọn **SG-Backend**.
  + Sau khi tạo xong, SSH vào EC2 và cài web server

![EC2](/images/2.prerequisite/11-ec2-3.png)

5. Trước khi SSH cần làm 1 số thứ sau đây.
+ Gắn Internet Gateway (IGW) cho VPC
Vào VPC → Internet Gateways.
+ Create internet gateway → đặt tên (ví dụ: Provider-IGW).

Attach IGW đó vào VPC Provider-VPC.

+ Tạo/Chỉnh Route Table cho Subnet 
+ Vào VPC → Route Tables.
+ Chọn route table đang gắn với Provider-Subnet-1 hoặc tạo mới.
+ Edit routes:  Add route:
 + Destination: 0.0.0.0/0
 + Target: Internet Gateway (Provider-IGW)
+ **Save changes.**
Associate subnet: Gắn Provider-Subnet-1 vào route table này.

Cấp Public IPv4 cho EC2
+ Vào EC2 → Instances → Chọn EC2.
+ Actions → Networking → Manage IP Addresses.
+ Assign new Elastic IP hoặc bật Auto-assign public IPv4.
+ **Save.**
6. Tiếp tục mở **Gitbash** hoặc **Nhấn Windows + S → gõ PowerShell → Enter.** 
Ở đây mình dùng trên Git Bash nhé
  + Vào phần **Details** Copy **Public IPv4 address**
  + Tiếp tục vào Git Bash gõ lệnh **ssh -i ssh -i your-key.pem ec2-user@"Your Public IPv4 address"** 
  + Ví dụ đây là đường dẫn đúng **ssh -i "/d/AWS/Backend-EC2Key.pem" ec2-user@13.212.27.188**
  + Nhập **Yes**
  + Đây là giao diện bạn đã SSH thành công 

![EC2](/images/2.prerequisite/12-gitbash.png)

7. Sau đó cài đặt và khởi chạy web server Nginx trên EC2, đồng thời tạo trang HTML kiểm tra truy cập.
+ Nhập sudo yum install -y nginx
+ **sudo systemctl enable nginx**
+ **sudo systemctl start nginx**
+ **echo "Hello from Provider" | sudo tee /usr/share/nginx/html/index.html**


![EC2](/images/2.prerequisite/13-gitbash-nghinx.png)
