---
title : "Thiết lập môi trường Consumer (Account B) "
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2.2 </b> "
---

Trong bước này, chúng ta sẽ cần tạo một VPC có 2 subnet public / private. Sau đó tạo 1 EC2 Instance Linux nằm trong public subnet,  1 EC2 Instance Windows nằm trong private subnet.

Tổng quan kiến trúc sau khi các bạn hoàn tất bước này sẽ như sau:

![VPC](/images/Picture1.png)

Để tìm hiểu cách tạo các EC2 instance và VPC với public/private subnet các bạn có thể tham khảo bài lab :
  - [Giới thiệu về Amazon EC2](https://000004.awsstudygroup.com/vi/)
  - [Làm việc với Amazon VPC](https://000003.awsstudygroup.com/vi/) 


### Nội dung
  - [Tạo VPC](2.2.1-createvpcb/)
  - [Tạo subnet](2.2.2-createsubnetb/)
  - [Tạo security group](2.2.3-createsecuritygroup/)
  - [Tạo Interface Endpoint](2.2.4-createendpoint/)
  - [Tạo EC2 ](2.1.6-createec2-b/)
  