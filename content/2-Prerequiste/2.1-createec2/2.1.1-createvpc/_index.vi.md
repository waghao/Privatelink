---
title : "Tạo VPC "
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.1.1 </b> "
---



1. Truy cập [giao diện quản trị dịch vụ VPC](https://console.aws.amazon.com/vpc/home)
  + Click **Your VPC**.
  + Click **Create VPC**.

![VPC](/images/2.prerequisite/1-createvcpa-1.png)

2. Tại trang **Create VPC**.
  + Tại mục **Resources to create** Chọn **VCP Only**
  + Tại mục **Name tag** điền **VPC-Provider**.
  + Tại mục **IPv4 CIDR** điền : **10.10.0.0/16**.
  + Click **Create VPC**.

![VPC](/images/2.prerequisite/2-createvcpa-2.png)


3. Tại mục **DNS settings** Tick vào 
+ Enable DNS resolution
+ Enable DNS hostnames
