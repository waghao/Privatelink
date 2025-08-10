---
title : "DNS Resolution"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

**Meaning and purpose of DNS Resolution**
+ In the AWS PrivateLink solution, DNS Resolution plays a role in helping applications and services access internal resources through domain names instead of having to use fixed IP addresses. The goal of this part is to ensure that when a client in the VPC sends a request to the service domain name (for example: service.example.com), the DNS query will be correctly resolved to the IP address of the VPC Endpoint instead of going out to the Internet. This helps:

+ Increase security: all traffic only goes within the AWS network, not out to the Internet.

+ Simple management: clients do not need to change IP when the service infrastructure changes.

+ Support cross-account and cross-region: easily resolve domain names to the correct endpoint in each environment.

![Connect](/images/3.connect/amazon-route-53.png)

**Amazon Route 53** is an AWS domain name system (DNS) management service that provides fast, reliable, and highly scalable domain name resolution for applications and services running in the cloud. In the topic of building a private connection solution using AWS PrivateLink, Route 53 plays a key role in setting up and managing internal domain name resolution (Private DNS), helping services in different VPCs communicate with each other via domain names instead of hard IP addresses, ensuring flexibility and ease of management.

+ Specifically, when deploying PrivateLink, Route 53 allows the creation of Private Hosted Zones (PHZ) assigned to each VPC, thereby managing internal DNS records for the service. This allows Consumers to access the Provider service through a private domain name (e.g. web.service.provider.local) mapped to the default DNS name of the VPC Endpoint Interface, without having to use a static IP or public DNS. This not only increases security, avoids exposing the real IP address, but also makes the service expansion and maintenance process easier.

+ In addition, Route 53 also supports the ability to integrate with the organization's DNS system, synchronize internal domain names with services on AWS, creating a unified, stable and efficient domain name resolution system for the entire PrivateLink network architecture

### Contents
3.1. [Setting up Private DNS and Private Hosted Zone for Consumer Endpoint](3.1-public-instance/)