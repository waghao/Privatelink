---
title : "Tạo NLB"
date :  "`r Sys.Date()`" 
weight : 7 
chapter : false
pre : " <b> 2.1.6 </b> "
---


1. Tại Trang Dịch Vụ EC2 chọn **Load balancers** tiếp tục Click vào **Create Load balancer**

![role](/images/2.prerequisite/18-loadbalancer-1.png)

2. Tại trang **Compare and select load balancer type** Click **Network Load Balancer**

![role](/images/2.prerequisite/19-loadbalancer-2.png)

3. Tại trang **Create Network Load Balancer.**
+ Phần **Load balancer name** Nhập **NLB-Provider**
+ Tiếp tục **Scheme** Click **Internal**
+ **NetWork mapping** VPC chọn **VPC-Provider**
+ **Availability Zones and subnets** Click cả 2 vùng **Provider-Subnet-1 và Provider-Subnet-2.**
![createpolicy](/images/2.prerequisite/20-loadbalancer-3.png)
4. Phần **Listeners and routing** 
  + Protocol: **TCP** | Port: **80.**
  + Forward to: **TG-Backend.**
  
  + Cuối cùng Click **Create load balancer**
![createpolicy](/images/2.prerequisite/21-loadbalancer-4.png)
5. Tiếp tục Tạo VPC Endpoint Service
![createpolicy](/images/2.prerequisite/22-endpointservicea-1.png)
+ Tại trang VPC Chọn **Endpoint services** Click **Create endpoint service**
+ Name: **Service-Provider** 
+ **Load balancer type**: Click **Network**
+ Chọn NLB: **NLB-Provider.**

![createpolicy](/images/2.prerequisite/23-endpointservicea-2.png)


+ Bật **Require acceptance**
+ Click **Create**
![createpolicy](/images/2.prerequisite/24-endpointservicea-3.png)



Tiếp theo chúng ta sẽ thực hiện Tạo VPC Consumer (Account B giả lập)