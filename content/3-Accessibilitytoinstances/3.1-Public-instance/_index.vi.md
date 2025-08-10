---
title : "Thiết lập Private DNS và Private Hosted Zone cho Consumer Endpoint"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 3.1. </b> "
---



**1. Lấy DNS name của Endpoint (Consumer)**
+ Vào VPC → Endpoints.
+ Chọn Interface Endpoint vừa tạo ở phần 2.2.
+ Chuyển sang tab DNS names.
+ Copy Private DNS name mặc định dạng: vpce-0123456789abcdef-xyz.us-west-2.vpce.amazonaws.com

 => Đây sẽ là đích CNAME cho domain riêng của bạn.
![S3](/images/4.s3/48-53-6.png)
**2. Tạo Private Hosted Zone (PHZ)**
![S3](/images/4.s3/43-53-1.png)
+ Vào Route 53 → Hosted zones → Create hosted zone.
+ Domain name: service.provider.local
+ Type: Private hosted zone
+ VPC association: Chọn VPC-Consumer
+ Click **Create hosted zone.**
![S3](/images/4.s3/44-53-2.png)
![S3](/images/4.s3/45-53-3.png)

**3. Tạo Record CNAME trỏ về Endpoint**
+ Trong Hosted zone vừa tạo, click Create record.
![S3](/images/4.s3/46-53-4.png)
+ Record name: web
 + → Domain đầy đủ sẽ là web.service.provider.local
+ Record type: CNAME
+ Value: Paste DNS name lấy ở bước B1 (ví dụ: vpce-0123456789abcdef-xyz.us-west-2.vpce.amazonaws.com)
+ TTL: 60
+ Click **Create records.**
![S3](/images/4.s3/47-53-5.png)

**4. Tìm NACL và sửa lại các Inbound và OutBound cho cả 2 máy chủ**
+ Vào EC2 console → chọn instance (Consumer hoặc Provider)
+ Trong tab Networking → mục Subnet ID (ví dụ: subnet-0fb949b4d8bc8b7eb)

**Tìm Network ACL của subnet**
+ Vào VPC console → menu Subnets
+ Chọn Subnet ID vừa tìm ở bước trên
+ Trong tab Network ACL sẽ hiện ra Network ACL ID (ví dụ: acl-0dda9d68019072da6)

**Xem và chỉnh rules của NACL**

+ Click vào Network ACL ID
+ Sẽ thấy Inbound rules và Outbound rules
+ Sau đó các bạn sẽ nhập theo bảng dưới đây:
 1. Security Group (SG) **
**SG của EC2 Provider (máy chủ dịch vụ)**
**Inbound Rules:**
+ Cho phép TCP port 80 (HTTP) từ IP của ENI của Endpoint Provider (10.1.2.190/32) và Endpoint Consumer (10.1.3.140/32).
+ Tác dụng: Chỉ cho phép các request HTTP từ các Endpoint (Provider và Consumer) truy cập vào EC2 Provider. Ngăn chặn các kết nối không hợp lệ từ nguồn khác.
**Outbound Rules:**
+ Cho phép TCP port từ 1024 đến 65535 tới IP của ENI Endpoint Provider và Consumer.
+ Tác dụng: Cho phép EC2 Provider trả lời các request từ Endpoint trên các port động (ephemeral ports), đảm bảo lưu lượng phản hồi được gửi đúng địa chỉ.

**SG của EC2 Consumer (máy khách sử dụng dịch vụ)**
Outbound Rules:

+ Cho phép TCP port 80 tới IP ENI của Endpoint Provider và Consumer.
+ Tác dụng: Cho phép EC2 Consumer gửi request HTTP tới Provider thông qua các Endpoint.

**Inbound Rules:**

+ Cho phép TCP port 1024-65535 từ IP của Endpoint Provider và Consumer.
+ Tác dụng: Cho phép EC2 Consumer nhận phản hồi trả về từ Provider qua các port động.

![EC2](/images/3.connect/41-inbounda.png)
![EC2](/images/3.connect/42-inboundb.png)

**2. Network ACL (NACL)**
**NACL của Subnet Provider**
**Inbound Rules:**

+ Cho phép TCP port 80 từ IP ENI Endpoint Provider và Consumer.
+ Tác dụng: Cho phép lưu lượng HTTP đến subnet của Provider từ các Endpoint.

**Outbound Rules:**

+ Cho phép TCP port 1024-65535 đến IP ENI Endpoint Provider và Consumer.
+ Tác dụng: Cho phép lưu lượng phản hồi trả về qua các port động được phép đi ra ngoài subnet Provider.

**NACL của Subnet Consumer**
**Outbound Rules:**

+ Cho phép TCP port 80 tới IP ENI Endpoint Provider và Consumer.
+ Tác dụng: Cho phép các request HTTP được gửi ra khỏi subnet Consumer tới Provider qua các Endpoint.

**Inbound Rules:**

+ Cho phép TCP port 1024-65535 từ IP ENI Endpoint Provider và Consumer.
+ Tác dụng: Cho phép subnet Consumer nhận các phản hồi qua port độn




**5. Kiểm tra DNS**
SSH vào EC2 trong VPC-Consumer.
Chạy:

+ **nslookup web.service.provider.local**
+ **curl web.service.provider.local**
+ Kết quả trả về: **Hello from Provider**

Xong Bạn đã DNS tới máy chủ Provider Thành công. 




