---
title : "Cost Analysis "
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---
{{%notice note%}}
Objective: Calculate the cost of operating PrivateLink.

{{%/notice%}}

**Step 1: View service prices on AWS Pricing Calculator**

+ Go to AWS Pricing Calculator page (https://calculator.aws/#/)

+ Select Create estimate → Select Add service.

+ Find and select VPC Endpoint (or "AWS PrivateLink").

+ Select Elastic Load Balancing (ELB) (Network Load Balancer is a type of ELB).

+ Enter expected parameters:
+ Number of operating hours (for example: 720 hours/month for 1 month of continuous operation).

+ Expected data transfer capacity (GB/month).

+ Number of VPC Endpoints, number of subnets, number of AZs if available.

+ AWS Pricing Calculator will display a monthly cost estimate for you.

![S3](/images/4.s3/49-cost-1.png)

![S3](/images/4.s3/50-cost-2.png)

**Step 2: Enable and use Cost Explorer**

+ Log in to AWS Console.

+ Go to **Billing** → select **Cost Explorer.**

+ If not enabled, click the **Enable Cost Explorer** button and wait a few minutes to activate.

Create a new report by:

+ Select Create report → Cost and Usage Report.

+ Filter by Service → select VPC Endpoint and Elastic Load Balancing.

+ Observe costs incurred over time, analyze to optimize and forecast budget.

![S3](/images/4.s3/51-cost-3.png)