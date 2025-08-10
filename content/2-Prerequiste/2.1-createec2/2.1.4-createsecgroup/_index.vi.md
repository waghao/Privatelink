---
title : "Tạo security group"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 2.1.3 </b> "
---

#### Tạo các security group

1. Truy cập [giao diện quản trị dịch vụ VPC](https://console.aws.amazon.com/vpc)
  + Click **Security Group**.  
  + Click **Create security group**.

![SG](/images/2.prerequisite/6-createvpca-security1.png)

3. Tại mục **Security group name**, điền **SG-Backend**. 
  + Tại mục **Description**, điền **Allows SSH access to developers**.
  + Tại mục **VPC**, click dấu **X** để chọn lại **VPC-Provider** bạn đã tạo cho bài lab này.

![SG](/images/2.prerequisite/7-createvpca-security2.png)
4. Tại mục **Inbound rules**, chọn **Add Rules**
  + Tại mục **Type** Chọn **HTTP**, **Port: 80**
  + Tại mục **Type** Chọn **SSH**, **Port: 22**
5. Giữ nguyên **Outbound rule**, kéo chuột xuống phía dưới.
  + Click **Create security group**.

