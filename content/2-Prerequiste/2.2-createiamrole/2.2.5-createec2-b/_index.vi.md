---
title : " Tạo EC2 của Account B"
date :  "`r Sys.Date()`" 
weight : 6 
chapter : false
pre : " <b> 2.2.5 </b> "
---

NEWW

1. Truy cập giao diện quản trị dịch vụ EC2
  + Click **Instance**.
  + Click **Launch Instances**.
  ![EC2](/images/3.connect/35-ec2-1.png)
  + Tại trang Tạo Instance
  + Nhập **Name: Consumer-B.**

2. Tại trang **Step 1: Choose an Amazon Machine Image (AMI)**.
  + Click **Select** để lựa chọn AMI **Amazon Linux 2023 AMI**.
  
   Tại trang **Step 2: Choose an Instance Type**.
 + Click chọn Instance type **t2.micro**.
 

3. Tại mục **Key pair (login)**
  + Chọn **Create new key pair**
  + Tại mục **Key pair name** nhập **Consumer-bkey**.
  + Tại mục **Key pair type** chọn **RSA**
  + Tại mục **Private key file format** Chọn **.pem**
  + Click **Create key pair**.

![EC2](/images/3.connect/36-ec2-2.png)

4. Tại mục **Network settings** 
  + Click **Edit** 
  + Tại mục **VPC - required** Chọn **VCP-Consumer**
  + Tiếp tục **Subnet** Chọn **Provider-Subnet-1**
  + Phần **Firewall(security groups)** Chọn **Select existing security group**
  + **Common security groups** Chọn **SG-Endpoint**.
  + Sau khi tạo xong, SSH vào EC2 và cài web server
  
![EC2](/images/3.connect/37-ec2-3.png)

6. Muốn nhanh hơn không cần rườm rà thì các bạn chỉ cần Click vào **Intansce** vừa tạo sau đó Click vào **connect**


  
![EC2](/images/3.connect/40-connect-ec2b.png)

+ Test kết nối
+ Sau khi SSH vào EC2 Consumer.
+ Các bạn **curl http://<Private-DNS-hoặc-IP-endpoint>** 
+ khi mà nó xuất hiện như trong hình là xong nhé
![EC2](/images/3.connect/41-curl.png)


