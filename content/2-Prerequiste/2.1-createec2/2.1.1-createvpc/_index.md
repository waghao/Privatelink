---
title : "Create VPC"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1.1 </b> "
---


1. Access [VPC service management interface](https://console.aws.amazon.com/vpc/home)
  + Click **Your VPC**.
  + Click **Create VPC**.

![VPC](/images/2.prerequisite/1-createvcpa-1.png)

2. At the **Create VPC**.
  + In the **Resources to create** choose **VCP Only**
  + In the **Name tag** fill **VPC-Provider**.
  + In the **IPv4 CIDR** fill : **10.10.0.0/16**.
  + Click **Create VPC**.

![VPC](/images/2.prerequisite/2-createvcpa-2.png)


3. At the **DNS settings** Click  
+ Enable DNS resolution
+ Enable DNS hostnames