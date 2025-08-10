---
title : " Create EC2 of Account B"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 2.2.5 </b> "
---

NEWW

1. Access the EC2 service management interface
+ Click **Instance**.
+ Click **Launch Instances**.
![EC2](/images/3.connect/35-ec2-1.png)
+ On the Create Instance page
+ Enter **Name: Consumer-B.**

2. On the **Step 1: Choose an Amazon Machine Image (AMI)** page.
+ Click **Select** to select the AMI **Amazon Linux 2023 AMI**.

On the **Step 2: Choose an Instance Type** page.
+ Click to select Instance type **t2.micro**.

3. In **Key pair (login)**
+ Select **Create new key pair**
+ In **Key pair name** enter **Consumer-bkey**.
+ In **Key pair type** select **RSA**
+ In **Private key file format** Select **.pem**
+ Click **Create key pair**.

![EC2](/images/3.connect/36-ec2-2.png)

4. In **Network settings**
+ Click **Edit**
+ In **VPC - required** Select **VCP-Consumer**
+ Continue **Subnet** Select **Provider-Subnet-1**
+ In **Firewall(security groups)** Select **Select existing security group**
+ **Common security groups** Select **SG-Endpoint**.
+ After creating, SSH into EC2 and install the web server

![EC2](/images/3.connect/37-ec2-3.png)

6. If you want it to be faster and not complicated, just click on the **Intansce** you just created and then click on **connect**

![EC2](/images/3.connect/40-connect-ec2b.png)

+ Test the connection
+ After SSHing into EC2 Consumer.
+ You **curl http://<Private-DNS-or-IP-endpoint>**
+ when it appears as in the picture, it's done
![EC2](/images/3.connect/41-curl.png)