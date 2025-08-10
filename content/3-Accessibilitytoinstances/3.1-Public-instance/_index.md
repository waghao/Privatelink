---
title : "Setting up Private DNS and Private Hosted Zone for Consumer Endpoint"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 3.1. </b> "
---

**1. Get the DNS name of the Endpoint (Consumer)**
+ Go to VPC → Endpoints.
+ Select the Interface Endpoint just created in section 2.2.
+ Switch to the DNS names tab.
+ Copy the default Private DNS name in the format: vpce-0123456789abcdef-xyz.us-west-2.vpce.amazonaws.com

=> This will be the CNAME destination for your private domain.
![S3](/images/4.s3/48-53-6.png)
**2. Create Private Hosted Zone (PHZ)**
![S3](/images/4.s3/43-53-1.png)
+ Go to Route 53 → Hosted zones → Create hosted zone.
+ Domain name: service.provider.local
+ Type: Private hosted zone
+ VPC association: Select VPC-Consumer
+ Click **Create hosted zone.**
![S3](/images/4.s3/44-53-2.png)
![S3](/images/4.s3/45-53-3.png)

**3. Create CNAME Record pointing to Endpoint**
+ In the newly created Hosted zone, click Create record.
![S3](/images/4.s3/46-53-4.png)
+ Record name: web
+ → Full domain will be web.service.provider.local
+ Record type: CNAME
+ Value: Paste DNS name taken in step B1 (for example: vpce-0123456789abcdef-xyz.us-west-2.vpce.amazonaws.com)
+ TTL: 60
+ Click **Create records.**
![S3](/images/4.s3/47-53-5.png)

**4. Find NACL and edit Inbound and OutBound for both servers**
+ Go to EC2 console → select instance (Consumer or Provider)
+ In Networking tab → Subnet ID (eg: subnet-0fb949b4d8bc8b7eb)

**Find Network ACL of subnet**
+ Go to VPC console → Subnets menu
+ Select Subnet ID found in the step above
+ In Network ACL tab, Network ACL ID will appear (eg: acl-0dda9d68019072da6)

**View and edit NACL rules**

+ Click on Network ACL ID
+ You will see Inbound rules and Outbound rules
+ Then you will enter according to the table below:
1. Security Group (SG) **
**SG of EC2 Provider (service server)**
**Inbound Rules:**
+ Allow TCP port 80 (HTTP) from IP of ENI of Endpoint Provider (10.1.2.190/32) and Endpoint Consumer (10.1.3.140/32).

+ Effect: Only allows HTTP requests from Endpoints (Provider and Consumer) to access EC2 Provider. Prevent invalid connections from other sources.

**Outbound Rules:**
+ Allow TCP port from 1024 to 65535 to IP of ENI Endpoint Provider and Consumer.

+ Effect: Allow EC2 Provider to respond to requests from Endpoint on dynamic ports (ephemeral ports), ensuring response traffic is sent to the correct address.

**SG of EC2 Consumer (client using the service)**
Outbound Rules:

+ Allow TCP port 80 to IP ENI of Endpoint Provider and Consumer.

+ Effect: Allow EC2 Consumer to send HTTP requests to Provider through Endpoints.

**Inbound Rules:**

+ Allow TCP port 1024-65535 from the IP of Endpoint Provider and Consumer.

+ Effect: Allow EC2 Consumer to receive response back from Provider via dynamic ports.

![EC2](/images/3.connect/41-inbounda.png)
![EC2](/images/3.connect/42-inboundb.png)

**2. Network ACL (NACL)**
**NACL of Subnet Provider**
**Inbound Rules:**

+ Allow TCP port 80 from IP ENI Endpoint Provider and Consumer.

+ Effect: Allow HTTP traffic to the Provider subnet from Endpoints.

**Outbound Rules:**

+ Allow TCP port 1024-65535 to IP ENI Endpoint Provider and Consumer.

+ Effect: Allow response back traffic via dynamic ports to go out of the Provider subnet.

**NACL of Subnet Consumer**
**Outbound Rules:**

+ Allow TCP port 80 to IP ENI Endpoint Provider and Consumer.

+ Effect: Allow HTTP requests to be sent out of the Consumer subnet to Provider via Endpoints.

**Inbound Rules:**

+ Allow TCP port 1024-65535 from IP ENI Endpoint Provider and Consumer.

+ Effect: Allow subnet Consumer to receive responses via buffer port

**5. Check DNS**
SSH to EC2 in VPC-Consumer.

Run:

+ **nslookup web.service.provider.local**
+ **curl web.service.provider.local**
+ Return result: **Hello from Provider**

Done You have DNS to the Provider server Successfully.