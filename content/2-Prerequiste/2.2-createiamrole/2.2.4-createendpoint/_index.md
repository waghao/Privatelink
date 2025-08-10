---
title : " Creating Interface Endpoint"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 2.2.4 </b> "
---



1. Access [VPC service administration interface](https://console.aws.amazon.com/vpc/home)
+ Create Interface Endpoint
+ Go to VPC → Endpoints → Create endpoint.
![VPC](/images/3.connect/29-endpoint-1.png)

+ Service category: Other endpoint services.
+ Service name: paste Service Name from Provider then Clic **Verify Service**
+ VPC: VPC-Consumer.
+ Subnets: Consumer-Subnet-1, Consumer-Subnet-2.
+ Security Group: SG-Endpoint.
+ Turn on Enable private DNS.
![VPC](/images/3.connect/30-endpoint-2.png)

+ Click Create endpoint.






+ Go to Provider account
+ VPC -> EndPoint Service
+ Select Service-Provider -> Select Tags Endpoint Connections
+ Click **action** select **Modify supported Regions** select **sydney**

![VPC](/images/3.connect/33-endpoint-5.png)

+ Then fill in **accept**
![VPC](/images/3.connect/34-endponit-6.png)