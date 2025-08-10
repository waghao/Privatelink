---
title : "Create NLB"
date : "`r Sys.Date()`"
weight : 7
chapter : false
pre : " <b> 2.1.6 </b> "
---


1. At the EC2 Service Page, select **Load balancers** and continue Click on **Create Load balancer**

![role](/images/2.prerequisite/18-loadbalancer-1.png)

2. On **Compare and select load balancer type** page Click **Network Load Balancer**

![role](/images/2.prerequisite/19-loadbalancer-2.png)

3. At page **Create Network Load Balancer.**
+ In **Load balancer name** section Enter **NLB-Provider**
+ Continue **Scheme** Click **Internal**
+ **NetWork mapping** VPC selects **VPC-Provider**
+ **Availability Zones and subnets** Click both zones **Provider-Subnet-1 and Provider-Subnet-2.**
![createpolicy](/images/2.prerequisite/20-loadbalancer-3.png)
4. **Listeners and routing** section 
+ Protocol: **TCP** | Port: **80.** 
+ Forward to: **TG-Backend.** 

+ Finally Click **Create load balancer**
![createpolicy](/images/2.prerequisite/21-loadbalancer-4.png)
5. Continue to Create VPC Endpoint Service
![createpolicy](/images/2.prerequisite/22-endpointservicea-1.png)
+ At VPC page Select **Endpoint services** Click **Create endpoint service**
+ Name: **Service-Provider**
+ **Load balancer type**: Click **Network**
+ Select NLB: **NLB-Provider.**

![createpolicy](/images/2.prerequisite/23-endpointservicea-2.png)


+ Turn on **Require acceptance**
+ Click **Create**
![createpolicy](/images/2.prerequisite/24-endpointservicea-3.png)



Next we will do it Now Create VPC Consumer (Account B simulated)