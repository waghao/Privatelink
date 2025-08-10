---
title : "Tạo VPC "
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2.2.1 </b> "
---

{{%notice note %}}
Ở phần này các bạn nhớ đổi qua region mới để tiếp tục làm nha cụ thể theo mình thì chọn vùng Sydney nhé
{{%/notice%}}

1. Truy cập [giao diện quản trị dịch vụ VPC](https://console.aws.amazon.com/vpc/home)
  + Click **Your VPC**.
  + Click **Create VPC**.

![VPC](/images/3.connect/23-vpcb-1.png)

2. Tại trang **Create VPC**.
  + Tại mục **Resources to create** Chọn **VCP Only**
  + Tại mục **Name tag** điền **VPC-Consumer**.
  + Tại mục **IPv4 CIDR** điền : **10.10.0.0/16**.
  + Click **Create VPC**.

![VPC](/images/3.connect/24-vpcb-2.png)


3. Tại mục **DNS settings** Tick vào 
+ Enable DNS resolution
+ Enable DNS hostnames
