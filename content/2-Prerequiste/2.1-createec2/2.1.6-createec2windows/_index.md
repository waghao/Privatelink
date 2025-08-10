---
title : "Create Target Group"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 2.1.6 </b> "
---

1. Access [EC2 service management interface](https://console.aws.amazon.com/ec2/v2/home)
+ Click **Target Groups**.
+ Click **Create Target Group**.
![EC2](/images/2.prerequisite/14-targetgroup-1.png)
2. On the **Choose a target type** page.
+ Click **Instances**
+ Scroll down

3. At **Target group name**.
+ Enter **tgbackend**.
+ Click **Protocol: TCP | Port: 80**.

4. VPC **Select VPC-Provider**
+ At **Protocol version** select **HTTP1**.
+ Click **Next**

![EC2](/images/2.prerequisite/15-targetgroup-2.png)

5. On the **Register targets** page Select **Backend-EC2** 
+ Click **Include as pending below** 
+ Finally Click on **Create target group**

![EC2](/images/2.prerequisite/16-targetgroup-3.png)