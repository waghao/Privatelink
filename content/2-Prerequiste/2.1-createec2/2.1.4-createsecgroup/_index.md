---
title : "Create security groups"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 2.1.4 </b> "
---

#### Create security groups

1. Truy cập [VPC service management interface](https://console.aws.amazon.com/vpc)
  + Click **Security Group**.  
  + Click **Create security group**.

![SG](/images/2.prerequisite/6-createvpca-security1.png)

3. At the **Security group name**, fill **SG-Backend**. 
  + At the **Description**, fill **Allows SSH access to developers**.
  + At the **VPC**, click  **X** to choose **VPC-Provider** you created for this lab.

![SG](/images/2.prerequisite/7-createvpca-security2.png)
4. At the **Inbound rules**, Choose **Add Rules**
  + At the **Type** Choose **HTTP**, **Port: 80**
  + At the **Type** Choose **SSH**, **Port: 22**
5. Keep it the same **Outbound rule**, drag mouse down.
  + Click **Create security group**.

