---
title : "Tối ưu cấu hình mạng bằng cách loại bỏ Internet Gateway cho Private Subnet "
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 4.1 </b> "
---

Trong quá trình triển khai Network Load Balancer nội bộ (Internal NLB), mình đã nhận thấy việc sử dụng subnet public (có route đến Internet Gateway) không phù hợp và có thể gây ra lộ IP, mất bảo mật, đồng thời AWS cũng không cho phép chọn subnet public cho Internal NLB.

Do đó, mình đã thực hiện các bước tối ưu quan trọng sau:

1. Loại bỏ Internet Gateway (IGW) hoặc sửa Route Table

+ Mình đã xóa các route trỏ đến IGW (0.0.0.0/0 → igw-xxxxxxx) trong bảng định tuyến (Route Table) của các subnet được chọn để làm subnet private.

+ Việc này đảm bảo rằng subnet không còn truy cập trực tiếp ra internet, phù hợp với yêu cầu bảo mật của Internal NLB.

+ Kiểm tra và đảm bảo subnet trở thành Private Subnet thực sự. Sau khi chỉnh sửa route table, mình kiểm tra lại các subnet để đảm bảo không còn đường đi ra Internet Gateway. Chỉ các subnet này mới được phép chọn làm subnet cho Internal NLB.
2. Chọn subnet private thuộc ít nhất 2 Availability Zones (AZs)

+ Mình chọn subnet private trong 2 AZ để đảm bảo tính sẵn sàng cao, load balancer có thể chịu lỗi và cân bằng tải hiệu quả.


+ Kết quả tối ưu
+ Hệ thống được bảo mật tốt hơn, tránh lộ IP ra ngoài.

+ Đáp ứng đúng yêu cầu kỹ thuật của AWS cho Internal NLB.

+ Tối ưu chi phí và tăng độ ổn định của hệ thống khi hoạt động trên nhiều AZ với private subnet.


 
Tiếp theo chúng ta sẽ tiến hành đến xem chi phí nhé.
