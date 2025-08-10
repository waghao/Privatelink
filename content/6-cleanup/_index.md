---
title : "Clean up resources"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---
Objective:
Delete all created resources to avoid unnecessary costs and prepare a clean environment for the next deployments or labs.

**Step 1: Delete Endpoint Interface in VPC Consumer**
+ Go to VPC → Endpoints in region us-west-2 (Consumer).

+ Select the Endpoint corresponding to the created PrivateLink (based on Service Name).

+ Click Actions → Delete Endpoint to delete the Endpoint Interface.

**Step 2: Delete Security Group of Endpoint (Consumer)**
+ Go to EC2 → Security Groups in region us-west-2.

+ Find and select SG-Endpoint (or SG related to Endpoint).

+ Delete this Security Group (Delete).

**Step 3: Delete EC2 Consumer (if any)**
+ Go to EC2 → Instances region us-west-2.

+ Shut down and terminate the EC2 instances created in VPC Consumer, for example the instance used to test the connection.

**Step 4: Delete Subnet and VPC Consumer**
+ Go to VPC → Subnets in region us-west-2.

+ Select the subnets belonging to VPC-Consumer (Consumer-Subnet-1, Consumer-Subnet-2).

+ Delete each subnet.

+ Go back to VPC → Your VPCs, select VPC-Consumer and delete the VPC.

**Step 5: From the Provider region (us-east-1), delete Endpoint Service and NLB**
+ Go to VPC → Endpoint Services region us-east-1.

+ Select the Service-Provider Endpoint Service created.

+ Delete Endpoint Service (Delete).

+ Go to EC2 → Load Balancers region us-east-1.

+ Select NLB-Provider (Network Load Balancer).

+ Delete Load Balancer (Delete).

**Step 6: Delete Target Group Backend**
+ Go to EC2 → Target Groups region us-east-1.

+ Select Target Group tgbackend.

+ Delete Target Group.

**Step 7: Delete EC2 Backend (Provider)**
+ Go to EC2 → Instances region us-east-1.

+ Turn off and terminate the Backend-EC2 instance.

**Step 8: Delete Provider Security Groups**
+ Go to EC2 → Security Groups region us-east-1.

+ Delete the Security Groups: SG-Backend, SG-NLB.

**Step 9: Delete Subnets and VPC Provider**
+ Go to VPC → Subnets region us-east-1.

+ Delete subnets belonging to VPC-Provider (Provider-Subnet-1, Provider-Subnet-2).

+ Go to VPC → Your VPCs region us-east-1.

+ Delete VPC-Provider.

**Step 10: Delete Private Hosted Zone**
+ Go to Route 53 → Hosted zones (default region).

+ Find and delete Private Hosted Zone named service.provider.local if created for DNS resolution.

{{%notice note%}}
Note:
Delete resources in order from smallest to largest (instances first, then security groups, subnets, then VPC) to avoid dependency errors.

Check the remaining resources by going to each AWS Console service.
Ensure that no resources incur costs after deletion.
{{%/notice%}}