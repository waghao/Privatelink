---
title : "Dọn dẹp tài nguyên"
date :  "`r Sys.Date()`" 
weight : 6 
chapter : false
pre : " <b> 6. </b> "
---
Mục tiêu:
Xóa toàn bộ tài nguyên đã tạo để tránh phát sinh chi phí không cần thiết và chuẩn bị môi trường sạch cho các lần triển khai hoặc lab tiếp theo.

**Bước 1: Xóa Endpoint Interface ở VPC Consumer**
+ Vào VPC → Endpoints trong region us-west-2 (Consumer).

+ Chọn Endpoint tương ứng với PrivateLink đã tạo (dựa vào Service Name).

+ Click Actions → Delete Endpoint để xóa Endpoint Interface.

**Bước 2: Xóa Security Group của Endpoint (Consumer)**
+ Vào EC2 → Security Groups trong region us-west-2.

+ Tìm và chọn SG-Endpoint (hoặc SG liên quan đến Endpoint).

+ Xóa Security Group này (Delete).

**Bước 3: Xóa EC2 Consumer (nếu có)**
+ Vào EC2 → Instances region us-west-2.

+ Tắt và terminate các instance EC2 đã tạo trong VPC Consumer, ví dụ instance dùng để test kết nối.

**Bước 4: Xóa Subnet và VPC Consumer**
+ Vào VPC → Subnets trong region us-west-2.

+ Chọn các subnet thuộc VPC-Consumer (Consumer-Subnet-1, Consumer-Subnet-2).

+ Xóa từng subnet.

+ Quay lại VPC → Your VPCs, chọn VPC-Consumer và xóa VPC.

**Bước 5: Từ region Provider (us-east-1), xóa Endpoint Service và NLB**
+ Vào VPC → Endpoint Services region us-east-1.

+ Chọn Service-Provider Endpoint Service đã tạo.

+ Xóa Endpoint Service (Delete).

+ Vào EC2 → Load Balancers region us-east-1.

+ Chọn NLB-Provider (Network Load Balancer).

+ Xóa Load Balancer (Delete). 

**Bước 6: Xóa Target Group Backend**
+ Vào EC2 → Target Groups region us-east-1.

+ Chọn Target Group tgbackend.

+ Xóa Target Group.

**Bước 7: Xóa EC2 Backend (Provider)**
+ Vào EC2 → Instances region us-east-1.

+ Tắt và terminate instance Backend-EC2.

**Bước 8: Xóa Security Groups của Provider**
+ Vào EC2 → Security Groups region us-east-1.

+ Xóa các Security Group: SG-Backend, SG-NLB.

**Bước 9: Xóa Subnets và VPC Provider**
+ Vào VPC → Subnets region us-east-1.

+ Xóa các subnet thuộc VPC-Provider (Provider-Subnet-1, Provider-Subnet-2).

+ Vào VPC → Your VPCs region us-east-1.

+ Xóa VPC-Provider.

**Bước 10: Xóa Private Hosted Zone**
+ Vào Route 53 → Hosted zones (region mặc định).

+ Tìm và xóa Private Hosted Zone tên service.provider.local nếu đã tạo cho phần DNS resolution.
{{%notice note%}}
Lưu ý:
Hãy xóa các tài nguyên theo thứ tự từ nhỏ đến lớn (instance trước, rồi security groups, subnets, rồi VPC) để tránh lỗi phụ thuộc.
Kiểm tra lại các tài nguyên còn tồn đọng bằng cách vào từng dịch vụ AWS Console.
Đảm bảo không còn tài nguyên phát sinh chi phí sau khi xóa.
{{%/notice%}}