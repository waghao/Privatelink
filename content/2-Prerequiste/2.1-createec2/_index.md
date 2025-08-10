---
title : "Setting up Provider Environment (Account A) "
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

In this step, we will need to create a VPC with 2 public / private subnets. Then create 1 EC2 Instance Linux in the public subnet, 1 EC2 Instance Windows in the private subnet.

The architecture overview after you complete this step will be as follows:

![VPC](/images/Picture1.png)

To learn how to create EC2 instances and VPCs with public/private subnets, you can refer to the lab:

- [Introduction to Amazon EC2](https://000004.awsstudygroup.com/vi/)

- [Working with Amazon VPC](https://000003.awsstudygroup.com/vi/)

### Content
- [Create VPC](2.1.1-createvpc/)
- [Create subnet](2.1.2-createpublicsubnet/)
- [Create security group](2.1.4-createsecgroup/)
- [Create public Linux server](2.1.5-createec2linux/)

- [Create Target Group](2.1.6-createec2windows/)
- [Create NBL](2.1.7-createloadbalancer/)