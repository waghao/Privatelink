---
title : "Quy trình vận hành"
date :  "`r Sys.Date()`" 
weight : 5 
chapter : false
pre : " <b> 5. </b> "
---

{{% notice note %}}
Mục tiêu: Quản lý, giám sát và mở rộng PrivateLink một cách dễ dàng, đảm bảo dịch vụ hoạt động ổn định và bảo mật, phù hợp với người vận hành đơn lẻ.
{{% /notice %}}

**1. Ghi chép và lưu trữ cấu hình quan trọng**
+ Ghi lại thông tin VPC ID, CIDR, Subnet ID, Security Group ID, Endpoint ID, Service Name.

+ Lưu ở nơi dễ tìm (Google Docs, Notepad, hoặc file trên máy tính).

+ Ghi rõ ngày giờ thay đổi cấu hình để theo dõi.

**2. Kiểm tra định kỳ (ví dụ 1 tuần/lần)**
+ Kiểm tra DNS resolution bằng lệnh nslookup hoặc dig từ EC2 hoặc máy tính cá nhân.

+ Xem nhanh trạng thái Endpoint trong AWS Console: có “Available” không, có lỗi gì không.

+ Kiểm tra logs VPC Flow Logs (nếu bật) hoặc CloudWatch xem có truy cập lạ không.

+ Ghi chú lại nếu phát hiện bất thường.

**3. Khi cần mở rộng hoặc thay đổi**
+ Nếu dịch vụ bị tải cao, thêm subnet mới vào Endpoint và NLB qua Console.

+ Nếu muốn mở rộng ra vùng (region) mới, tạo thêm Endpoint ở vùng đó.

+ Luôn ghi lại thay đổi và kiểm tra lại kết nối sau khi thêm subnet hoặc region mới.

**4. Xử lý sự cố cơ bản**
+ DNS không hoạt động → kiểm tra lại Private DNS setting, Security Group.

+ Kết nối timeout → kiểm tra trạng thái Endpoint, NLB, Security Group, Route Table.

+ Ghi lại lỗi và cách khắc phục để lần sau nhanh xử lý.

**5. Bảo mật đơn giản**
+ Không chia sẻ quyền truy cập AWS cho người khác nếu không cần thiết.

+ Đảm bảo Security Group chỉ mở các port cần thiết.

+ Bật CloudTrail để theo dõi ai thay đổi cấu hình (nếu có).

**6. Sao lưu đơn giản**
+ Lưu lại file cấu hình hoặc snapshot cấu hình trên AWS (VD: Export CloudFormation nếu có).

+ Nếu cần, viết nhanh lại các bước tạo Endpoint, NLB để có thể làm lại nhanh.

**7. Tự học và nâng cao**
+ Tham khảo tài liệu AWS khi có tính năng mới.

+ Tự động hóa bằng script hoặc CloudFormation khi bạn có thời gian để giảm thao tác thủ công.

 Hãy nhớ thực hiện bước dọn dẹp tài nguyên để tránh sinh chi phí ngoài ý muốn nhé.