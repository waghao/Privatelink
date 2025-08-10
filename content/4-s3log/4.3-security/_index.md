---
title : "Security Authentication"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 4.3 </b> "
---
{{%notice note%}}
Goal: Authenticate PrivateLink connections that are completely private and controlled.
{{%/notice%}}
+ In **any** network architecture, especially when deploying cloud services like AWS, ensuring security is always a top priority. This chapter focuses on **authentication of the security and privacy of PrivateLink connections**, ensuring that all network traffic between components in the system is transmitted securely, **without being leaked to the public Internet environment.**

+ The main goal of this chapter is to **test and ensure that all connections between Consumers and Providers take place entirely in a private network environment,** without going through public connection points such as **Internet Gateways**. This not only helps protect sensitive data, avoid the risks of being attacked or eavesdropped, but also complies with the security and compliance requirements of the organization or legal regulations on information protection.

+ In addition, the chapter also focuses on access control through security policies such as security groups and network ACLs, ensuring that only valid traffic is allowed to pass through, preventing unauthorized access from the outside. Enabling VPC Flow Logs helps monitor and record detailed network traffic, providing important information for analysis, detecting abnormalities or security incidents in the system.

**Step 1: Make sure there is no Public Access**
+ Go to **EC2** → **Instances** → check the backend instance (Provider EC2) does not have a Public IP.

+ Go to **EC2** → **Load Balancers** → check the **Network Load Balancer** is configured as **Internal (no public IP).**

**Step 2: Check the packet flow (Packet Flow)**
+ **SSH into the Consumer EC2 instance.**

+ Run the following command to check the path to the service Provider via the internal domain (private DNS):

+ **traceroute web.service.provider.local**

+ **Observe the result:**

+ The path is not allowed to go through the Internet Gateway (IGW).

+ Hops must belong to private network, for example IP in CIDR of VPC/subnet, no public IP address.

**Step 3: Enable VPC Flow Logs to monitor network traffic**
Go to **VPC** → **Flow Logs** → select **Create flow log.**

+ Set up as follows:

+ **Resource type: VPC.**

+ Select Consumer VPC (VPC containing Consumer EC2).

+ **Filter**: select ACCEPT (only record allowed traffic).

+ **Destination**: select Send to CloudWatch Logs.

+ **Select or create a new Log Group in CloudWatch.**

+ Click **Create** to start collecting logs.

+ Then you can go to CloudWatch Logs to view network traffic logs, verify that the traffic going through PrivateLink is as desired.

![S3](/images/4.s3/52-logs-1.png) 
![S3](/images/4.s3/53-logs-2.png) 
![S3](/images/4.s3/54-logs-3.png)