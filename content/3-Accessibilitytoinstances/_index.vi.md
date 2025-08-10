---
title : "Giải quyết DNS"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

**Ý nghĩa và mục tiêu của phần DNS Resolution**
+ Trong giải pháp AWS PrivateLink, DNS Resolution đóng vai trò giúp các ứng dụng và dịch vụ truy cập tài nguyên nội bộ thông qua tên miền thay vì phải sử dụng địa chỉ IP cố định. Mục tiêu của phần này là đảm bảo khi client trong VPC gửi yêu cầu đến tên miền dịch vụ (ví dụ: service.example.com), truy vấn DNS sẽ được phân giải chính xác về địa chỉ IP của VPC Endpoint thay vì ra Internet. Điều này giúp:

+ Tăng tính bảo mật: toàn bộ lưu lượng chỉ đi trong mạng AWS, không ra ngoài Internet.

+ Đơn giản quản lý: client không cần thay đổi IP khi hạ tầng dịch vụ thay đổi.

+ Hỗ trợ cross-account và cross-region: dễ dàng phân giải tên miền về đúng endpoint trong từng môi trường.

![Connect](/images/3.connect/amazon-route-53.png)

**Amazon Route 53** là dịch vụ quản lý hệ thống tên miền (DNS) của AWS, cung cấp khả năng phân giải tên miền nhanh, đáng tin cậy và mở rộng cao cho các ứng dụng và dịch vụ chạy trên môi trường đám mây. Trong đề tài xây dựng giải pháp kết nối riêng tư sử dụng AWS PrivateLink, Route 53 giữ vai trò then chốt trong việc thiết lập và quản lý phân giải tên miền nội bộ (Private DNS), giúp các dịch vụ trong các VPC khác nhau có thể giao tiếp với nhau thông qua tên miền thay vì địa chỉ IP cứng, đảm bảo tính linh hoạt và dễ quản lý.

+ Cụ thể, khi triển khai PrivateLink, Route 53 cho phép tạo các Private Hosted Zone (PHZ) gán riêng cho từng VPC, qua đó quản lý các bản ghi DNS nội bộ cho dịch vụ. Điều này giúp Consumer có thể truy cập dịch vụ Provider thông qua tên miền riêng (ví dụ web.service.provider.local) được ánh xạ tới DNS name mặc định của VPC Endpoint Interface, mà không phải dùng IP tĩnh hoặc public DNS. Việc này không chỉ tăng tính bảo mật, tránh lộ địa chỉ IP thực mà còn giúp quá trình mở rộng và bảo trì dịch vụ diễn ra dễ dàng hơn.

+ Ngoài ra, Route 53 còn hỗ trợ khả năng tích hợp với hệ thống DNS của tổ chức, đồng bộ hóa tên miền nội bộ với dịch vụ trên AWS, tạo nên một hệ thống phân giải tên miền đồng nhất, ổn định và hiệu quả cho toàn bộ kiến trúc mạng PrivateLink

### Nội dung
3.1. [Thiết lập Private DNS và Private Hosted Zone cho Consumer Endpoint](3.1-public-instance/)
