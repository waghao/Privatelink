---
title : "Create Subnets "
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 2.2.2 </b> "
---

1. Access [VPC service management interface](https://console.aws.amazon.com/vpc/home)
+ Click **Your VPC**.
+ Click **Subnet**.

![VPC](/images/3.connect/24-vpcsubnet-1.png)

2. On the **Create subnet** page.
+ Go to Subnets → Create subnet.
+ VPC: VPC-Consumer.
+ AZ 1: 
+ Name tag: Consumer-Subnet-1 
+ AZ: Asia Pacific (Sydney) / apse2-az1 (ap-southeast-2a) 
+ IPv4 CIDR: 10.1.1.0/24

![VPC](/images/3.connect/25-vpcsubnet-2.png) 


+ AZ 2: 
+ Name tag: Consumer-Subnet-2 
+ AZ: us-west-2b 
+ IPv4 CIDR: 10.1.2.0/24 
+ Click **Create subnet.**
![VPC](/images/3.connect/26-vpcsubnet-3.png)