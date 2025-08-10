---
title : "Operating Procedure"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

{{% notice note %}}
Objective: Manage, monitor and expand PrivateLink easily, ensure stable and secure service operation, suitable for single operators.

{{% /notice %}}

**1. Record and store important configurations**
+ Record information about VPC ID, CIDR, Subnet ID, Security Group ID, Endpoint ID, Service Name.

+ Save in an easy-to-find place (Google Docs, Notepad, or a file on your computer).

+ Clearly record the date and time of configuration changes for tracking.

**2. Check periodically (eg once a week)**
+ Check DNS resolution using the nslookup or dig command from EC2 or your personal computer.

+ Quickly view Endpoint status in AWS Console: is it “Available”, is there any error.

+ Check VPC Flow Logs (if enabled) or CloudWatch logs for unusual access.

+ Take notes if any abnormalities are detected.

**3. When to expand or change**

+ If the service is highly loaded, add a new subnet to the Endpoint and NLB via Console.

+ If you want to expand to a new region, create an additional Endpoint in that region.

+ Always record changes and recheck the connection after adding a new subnet or region.

**4. Basic troubleshooting**
+ DNS is not working → recheck Private DNS setting, Security Group.

+ Connection timeout → check Endpoint status, NLB, Security Group, Route Table.

+ Record errors and solutions for quick handling next time.

**5. Simple Security**
+ Do not share AWS access with others if not necessary.

+ Make sure Security Group only opens necessary ports.

+ Enable CloudTrail to track who changes the configuration (if any).

**6. Simple Backup**
+ Save the configuration file or configuration snapshot on AWS (eg: Export CloudFormation if available).

+ If necessary, quickly write down the steps to create Endpoint, NLB so you can do it again quickly.

**7. Self-study and improve**
+ Refer to AWS documentation when there is a new feature.

+ Automate with scripts or CloudFormation when you have time to reduce manual operations.

Remember to perform the resource cleanup step to avoid unexpected costs.