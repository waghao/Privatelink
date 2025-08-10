---
title : "System Optimization and Control"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

The goal of the performance optimization part of the system is to **ensure that PrivateLink connections and services operate with the lowest possible latency**, while **optimizing operating costs** and **increasing the ability to handle traffic (throughput) efficiently.**

Specifically, **minimizing latency** improves the end-user experience and **ensures that services are accessed quickly**, without network congestion or delays in data transmission. At the same time, cost optimization is an important factor in maintaining stable operations while still controlling the budget, avoiding unnecessary costs due to wasted resources or unreasonable configuration.

In addition, **increasing throughput** enables the system to handle a large volume of concurrent requests, suitable for applications that require high bandwidth and high access frequency, thereby ensuring the stability and scalability of the system in high load situations.



+ **AWS Pricing Calculator** is an online tool provided by Amazon Web Services, helping you estimate the cost of using AWS services accurately and easily before actual deployment.
+ https://aws.amazon.com/aws-cost-management/aws-pricing-calculator/

Some highlights of AWS Pricing Calculator:

+ Custom cost estimates: You can select different AWS services (EC2, S3, VPC Endpoint, Load Balancer, Lambda, etc.) and enter expected usage parameters such as running hours, storage capacity, transmission bandwidth, etc. to get detailed quotes.

+ Suitable for budget planning: Helps you forecast monthly or periodic costs, avoiding spending over budget.

+ Custom configuration: Allows you to set up details for each component, such as number of instances, instance types, regions, storage types, etc.

+ Intuitive, easy-to-use interface: Friendly web interface, you can save estimates and share with your team or customers.

+ Updated to current price: Always get the latest price from AWS, helping to estimate costs closer to reality.


### Content:

- [Optimize network configuration by removing Internet Gateway for Private Subnet](./4.1-updateiamrole/)
- [Cost analysis](./4.2-cost/)
- [Security authentication](./4.3-security)