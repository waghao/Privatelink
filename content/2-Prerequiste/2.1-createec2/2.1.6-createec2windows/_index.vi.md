---
title : "Tạo Target Group"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 2.1.5 </b> "
---

1. Truy cập [giao diện quản trị dịch vụ EC2](https://console.aws.amazon.com/ec2/v2/home)
  + Click **Target Groups**.
  + Click **Create Target Group**.
  ![EC2](/images/2.prerequisite/14-targetgroup-1.png)
2. Tại trang **Choose a target type**.
  + Click **Instances** 
  + Kéo chuột xuống tiếp 

3. Tại **Target group name**.
 + Nhập **tgbackend**.
 + Click **Protocol: TCP | Port: 80**.

4. VPC **Chọn VPC-Provider**
  + Tại mục **Protocol version** chọn **HTTP1**.
  + Click **Next** 

![EC2](/images/2.prerequisite/15-targetgroup-2.png)

5. Tại trang **Register targets** Chọn **Backend-EC2**
  + Click **Include as pending below** 
  + Cuối cùng Click vào **Create target group**

![EC2](/images/2.prerequisite/16-targetgroup-3.png)

