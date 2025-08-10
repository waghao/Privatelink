---
title : "Setting up Consumer Environment (Account B)"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

1. On the EC2 Service Page, select **Load balancers** and continue to Click **Create Load bakancer**

![role](/images/2.prerequisite/038-iamrole.png)

2. On the **Compare and select load balancer type** page, Click **Network Load Balancer**

![role](/images/2.prerequisite/038-iamrole.png)

3. On the **Create Network Load Balancer.** page,
+ In the **Load balancer name** section, enter **NLB-Provider**
+ Continue **Scheme** Click **Internal**
+ **NetWork mapping** VPC select **VPC-Provider**
+ **Availability Zones and subnets** Click both areas **Provider-Subnet-1 and Provider-Subnet-2.**


![role1](/images/2.prerequisite/039-iamrole.png)

4. **Listeners and routing** section 
+ Protocol: **TCP** | Port: **80.** 
+ Forward to: **TG-Backend.** 

+ Finally Click **Create load balancer**
![role1](/images/2.prerequisite/040-iamrole.png)

5. Continue to Create VPC Endpoint Service

+ At VPC page Select **Endpoint services** Click **Create endpoint service**
+ Name: **Service-Provider**
+ **Load balancer type**: Click **Network**
+ Select NLB: **NLB-Provider.**

![createpolicy](/images/2.prerequisite/041-iamrole.png)


+ Turn on **Require acceptance**
+ Click **Create**

![createpolicy](/images/2.prerequisite/041-iamrole.png)


Next we will create a VPC Consumer (simulated Account B).