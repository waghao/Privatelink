---
title : "Create VPC "
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.2.1 </b> "
---

{{%notice note %}}
In this section, remember to change to the new region to continue working. Specifically, I choose the Sydney region
{{%/notice%}}

1. Access [VPC service management interface](https://console.aws.amazon.com/vpc/home)
+ Click **Your VPC**.
+ Click **Create VPC**.

![VPC](/images/3.connect/23-vpcb-1.png)

2. On the **Create VPC** page.
+ In the **Resources to create** section, select **VCP Only**
+ In the **Name tag** section, enter **VPC-Consumer**.
+ In the **IPv4 CIDR** section, fill in: **10.10.0.0/16**. 
+ Click **Create VPC**.

![VPC](/images/3.connect/24-vpcb-2.png)


3. In the **DNS settings** section, tick it
+ Enable DNS resolution
+ Enable DNS hostnames