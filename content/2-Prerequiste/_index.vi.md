---
title : "Các bước chuẩn bị"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

![VPC](/images/2.prerequisite/aws-privatelink.png)

Để tìm hiểu cách tạo các EC2 instance và VPC với public/private subnet các bạn có thể tham khảo bài lab :
  - [Giới thiệu về Amazon EC2](https://000004.awsstudygroup.com/vi/)
  - [Làm việc với Amazon VPC](https://000003.awsstudygroup.com/vi/)

Để sử dụng AWS PrivateLink nhằm kết nối riêng tư giữa các dịch vụ trong cùng tài khoản hoặc giữa các tài khoản và vùng (region) khác nhau, chúng ta cần chuẩn bị trước một số tài nguyên và cấp quyền phù hợp để các thành phần có thể giao tiếp với nhau một cách bảo mật và hiệu quả.

Trong phần chuẩn bị này, chúng ta sẽ tiến hành tạo IAM Role và cấu hình chính sách quyền truy cập (permissions policy) cho các thành phần như:
- Service Provider (EC2, Load Balancer, Service behind NLB): có thể chỉ cần role EC2 thông thường, nhưng cần được đặt trong VPC có cấu hình phù hợp.
- Service Consumer (EC2 hoặc ứng dụng truy cập dịch vụ qua Endpoint): cần được cấp quyền để tạo, sử dụng VPC Endpoint và truy cập tài nguyên PrivateLink.
Ngoài ra, chúng ta cũng cần tạo các thành phần cơ bản như VPC, subnet, route table, security group phù hợp để triển khai:
- VPC Endpoint Service (phía provider) để xuất bản dịch vụ.
- VPC Endpoint (phía consumer) để truy cập dịch vụ thông qua PrivateLink.
Việc chuẩn bị IAM Role và cấu hình các tài nguyên mạng đúng cách là bước quan trọng để đảm bảo việc triển khai PrivateLink hoạt động bảo mật, đúng kiến trúc, và dễ quản lý, đặc biệt trong môi trường cross-account hoặc cross-region.


Vì sao chọn 1 Account và 2 VPC giả lập 2 miền trong bài lab PrivateLink này?

**1. Giản đơn hóa quản lý tài nguyên**
+ Dùng 1 tài khoản giúp bạn dễ dàng quản lý IAM Role, Policy, Service Catalog, Billing,... mà không phải xử lý phức tạp cross-account.
+ Giúp tập trung kiểm soát quyền truy cập và log trong 1 tài khoản.

**2. Giả lập Cross-Region nhưng vẫn trong 1 Account**
+ PrivateLink có thể làm cross-region (kết nối giữa 2 vùng AWS khác nhau).
+ Việc dùng 2 VPC (ví dụ VPC A ở region 1, VPC B ở region 2) giúp mô phỏng kiến trúc cross-region mà không cần phải tạo nhiều tài khoản.

**=> Dễ test, debug và tiết kiệm chi phí hơn.**

**3. Tạo môi trường gần thật cho thực hành và demo**
+ Việc có 2 VPC trong 2 region khác nhau mô phỏng đúng cách hoạt động thực tế của PrivateLink cross-region.
+ Bạn có thể test luồng dữ liệu, cấu hình endpoint, route, DNS resolution,... chuẩn xác.

**4. Hạn chế rủi ro và chi phí**
+ Nếu dùng 2 tài khoản thật, việc cấp quyền cross-account phức tạp hơn, dễ bị lỗi cấu hình.
+ Tạo 2 account riêng biệt có thể tốn thêm chi phí, cũng cần nhiều thời gian setup hơn.

 **=> 1 account + 2 VPC đơn giản hơn, phù hợp cho mục đích học tập, demo hoặc thử nghiệm.**

**5. Dễ dàng mô phỏng các chính sách bảo mật**
+ Bạn có thể vẫn mô phỏng các policy, IAM role như cross-account bằng cách gán role hoặc policy riêng biệt cho từng VPC.
+ Cấu hình SG, NACL, route table cũng có thể thực hiện như thật.

### Nội dung
  - [Thiết lập môi trường Provider (Account A)](2.1-createec2/)
  - [Thiết lập môi trường Consumer (Account B)](2.2-createiamrole/)

  
