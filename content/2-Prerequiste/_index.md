---
title : "Preparation "
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

![VPC](/images/2.prerequisite/aws-privatelink.png)

To learn how to create EC2 instance and VPC with public/private subnet you can refer to the lab
  - [Introduction to Amazon EC2](https://000004.awsstudygroup.com/vi/)
  - [Working with Amazon VPC](https://000003.awsstudygroup.com/vi/)

To use AWS PrivateLink to privately connect services within the same account or between different accounts and regions, we need to prepare some resources and grant appropriate permissions so that components can communicate securely and effectively.

In this preparation section, we will create IAM Role and configure permission policies for components such as:

+ Service Provider (EC2, Load Balancer, Service behind NLB): may only need normal EC2 role, but must be placed in VPC with appropriate configuration.

+ Service Consumer (EC2 or application accessing the service via Endpoint): needs to be granted permission to create, use VPC Endpoint and access PrivateLink resources.
In addition, we also need to create basic components such as VPC, subnet, route table, security group suitable for deployment:

+ VPC Endpoint Service (provider side) to publish the service.

+ VPC Endpoint (consumer side) to access the service via PrivateLink.
Preparing IAM Role and configuring network resources correctly is an important step to ensure PrivateLink deployment operates securely, architecturally correctly, and is easy to manage, especially in cross-account or cross-region environments.

Why choose 1 Account and 2 VPCs to simulate 2 domains in this PrivateLink lab?

**1. Simplify resource management**

+ Using 1 account helps you easily manage IAM Role, Policy, Service Catalog, Billing,... without dealing with complicated cross-account.

+ Helps centralize access control and logs within 1 account.

**2. Simulate Cross-Region but still within 1 Account**

+ PrivateLink can do cross-region (connect between 2 different AWS regions).

+ Using 2 VPCs (for example VPC A in region 1, VPC B in region 2) helps simulate cross-region architecture without needing multiple accounts.

 => Easier to test, debug and save cost.

**3. Create a near-real environment for practice and demo**

+ Having 2 VPCs in 2 different regions simulates correctly the real operation of cross-region PrivateLink.

+ You can test data flow, endpoint configuration, route, DNS resolution,... accurately.

**4. Limit risks and cost**

+ Using 2 real accounts, granting cross-account permission is more complex, easy to misconfigure.

+ Creating 2 separate accounts may cost more, and requires more setup time.

+ => 1 account + 2 VPCs is simpler, suitable for learning, demo or experimentation.

**5. Easily simulate security policies**

+ You can still simulate policies, IAM roles like cross-account by assigning separate role or policy for each VPC.

+ SG, NACL, route table configuration can also be done realistically.
### Content
- [Provider Environment Setup (Account A)](2.1-createec2/)
- [Consumer Environment Setup (Account B)](2.2-createiamrole/)

