---
title : "Create Security Group "
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 2.2.3 </b> "
---

1. Access [VPC service management interface](https://console.aws.amazon.com/vpc/home)
+ Click **Security Groups**.
+ Click **Create Security Group**.
+ On the Create Security Group page
![VPC](/images/3.connect/27-securitygroup-1.png)

+ Enter **Name: SG-Endpoint.**
+ **VPC** Enter **VPC-Consumer.**
+ Continue **Inbound rules:** Select **Type: HTTP | Port: 80 | Source: 0.0.0.0/0**
+ Outbound: keep default.
+ Finally **Click** **Create security group.**
![VPC](/images/3.connect/28-securitygroup-2.png)