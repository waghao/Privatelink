---
title : "Tạo Security Group  "
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 2.2.3 </b> "
---



1. Truy cập [giao diện quản trị dịch vụ VPC](https://console.aws.amazon.com/vpc/home)
  + Click **Security Groups**.
  + Click **Create Security Group**.
  + Tại trang Tạo Security Group 
![VPC](/images/3.connect/27-securitygroup-1.png)

  + Nhập **Name: SG-Endpoint.**
  + **VPC** Nhập **VPC-Consumer.**
  + Tiếp tục **Inbound rules:** Chọn **Type: HTTP | Port: 80 | Source: 0.0.0.0/0**
  + Outbound: giữ mặc định.
  + Cuối cùng **Click** **Create security group.**
![VPC](/images/3.connect/28-securitygroup-2.png)