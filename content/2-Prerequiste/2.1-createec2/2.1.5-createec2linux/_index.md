---
title : "Create EC2"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 2.1.5 </b> "
---

1. Access[VPC service management interface](https://console.aws.amazon.com/ec2/v2/home)
  + Click **Instances**.
  + Click **Launch instances**.
  
![EC2](/images/2.prerequisite/8-ec2-1.png)

2. At the **Step 1: Choose an Amazon Machine Image (AMI)**.
  + Click **Select** to choose AMI **Amazon Linux 2023 AMI**.
  
   At the **Step 2: Choose an Instance Type**.
 + Click choose Instance type **t2.micro**.
 
![EC2](/images/2.prerequisite/9-ec2-2.png)

3. In the **Key pair (login)**
  + Choose **Create new key pair**
  + In the **Key pair name** fill **Backend-EC2Key**.
  + In the **Key pair type** fill **RSA**
  + In the **Private key file format** Choose **.pem**
  + Click **Create key pair**.

![EC2](/images/2.prerequisite/10-keypema1.png)

4. At the **Network settings** 
  + Click **Edit** 
  + At the **VPC - required** Choose **VCP-Provider**
  + Continue **Subnet** chosse **Provider-Subnet-1**
  + Part **Firewall(security groups)** chosse **Select existing security group**
  + **Common security groups** Chọn **SG-Backend**.
  + Once created, SSH into EC2 and install web server

![EC2](/images/2.prerequisite/11-ec2-3.png)

5. Before SSH, you need to do the following.
+ Attach Internet Gateway (IGW) to VPC
Go to VPC → Internet Gateways.
+ Create internet gateway → name (eg: Provider-IGW).

Attach that IGW to VPC Provider-VPC.

+ Create/Edit Route Table for Subnet
+ Go to VPC → Route Tables.
+ Select the route table attached to Provider-Subnet-1 or create a new one.
+ Edit routes: Add route:
+ Destination: 0.0.0.0/0
+ Target: Internet Gateway (Provider-IGW)
+ **Save changes.**
Associate subnet: Attach Provider-Subnet-1 to this route table.

Give Public IPv4 to EC2
+ Go to EC2 → Instances → Select EC2.
+ Actions → Networking → Manage IP Addresses.
+ Assign new Elastic IP or enable Auto-assign public IPv4.
+ **Save.**
6. Continue to open **Gitbash** or **Press Windows + S → type PowerShell → Enter.**
Here I use Git Bash
+ Go to **Details** Copy **Public IPv4 address**
+ Continue to Git Bash and type the command **ssh -i ssh -i your-key.pem ec2-user@"Your Public IPv4 address"**
+ For example, this is the correct path **ssh -i "/d/AWS/Backend-EC2Key.pem" ec2-user@13.212.27.188**
+ Enter **Yes**
+ This is the interface you have successfully SSHed

![EC2](/images/2.prerequisite/12-gitbash.png)

7. Then install and launch the Nginx web server on EC2, and create an HTML page to test access.
+ Type sudo yum install -y nginx
+ **sudo systemctl enable nginx**
+ **sudo systemctl start nginx**
+ **echo "Hello from Provider" | sudo tee /usr/share/nginx/html/index.html**


![EC2](/images/2.prerequisite/13-gitbash-nghinx.png)