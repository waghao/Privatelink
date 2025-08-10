---
title : "Optimize network configuration by removing Internet Gateway for Private Subnet "
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---

During the process of deploying the internal Network Load Balancer (Internal NLB), I realized that using a public subnet (with a route to the Internet Gateway) is not suitable and can cause IP exposure, loss of security, and AWS also does not allow choosing a public subnet for Internal NLB.

Therefore, I have performed the following important optimization steps:

1. Remove the Internet Gateway (IGW) or edit the Route Table

+ I have deleted the routes pointing to IGW (0.0.0.0/0 → igw-xxxxxxx) in the Route Table of the subnets selected to be private subnets.

+ This ensures that the subnet no longer has direct access to the internet, in accordance with the security requirements of Internal NLB.

+ Check and ensure that the subnet becomes a real Private Subnet. After editing the route table, I recheck the subnets to ensure that there is no longer a path to the Internet Gateway. Only these subnets are allowed to be selected as subnets for Internal NLB.

2. Choose a private subnet belonging to at least 2 Availability Zones (AZs)

+ I choose a private subnet in 2 AZs to ensure high availability, the load balancer can withstand errors and balance the load effectively.

+ Optimal results
+ The system is better secured, avoiding exposing the IP to the outside.

+ Meets AWS's technical requirements for Internal NLB.

+ Optimizes costs and increases system stability when operating on multiple AZs with private subnets.

Next, we will proceed to see the costs.