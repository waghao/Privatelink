---
title : " Tạo Interface Endpoint"
date :  "`r Sys.Date()`" 
weight : 5 
chapter : false
pre : " <b> 2.2.4 </b> "
---



1. Truy cập [giao diện quản trị dịch vụ VPC](https://console.aws.amazon.com/vpc/home)
+ Tạo Interface Endpoint
+ Vào VPC → Endpoints → Create endpoint.
![VPC](/images/3.connect/29-endpoint-1.png)

+ Service category: Other endpoint services.
+ Service name: dán Service Name từ Provider sau đó Clic **Verify Service**
+ VPC: VPC-Consumer.
+ Subnets: Consumer-Subnet-1, Consumer-Subnet-2.
+ Security Group: SG-Endpoint.
+ Bật Enable private DNS.
![VPC](/images/3.connect/30-endpoint-2.png)

+ Click Create endpoint.






+ Vào account Provider
+ VPC -> EndPoint Service 
+ Chọn Service-Provider -> Chọn Tags Endpoint Connections 
+ Click **action** chọn  **Modify supported Regions** chọn **sydney**

![VPC](/images/3.connect/33-endpoint-5.png)

+ Sau đó điền **accept**
![VPC](/images/3.connect/34-endponit-6.png)