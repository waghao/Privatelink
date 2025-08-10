---
title : "Phân tích chi phí "
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 4.2 </b> "
---
{{%notice note%}}
Mục tiêu: Tính toán chi phí vận hành PrivateLink.
{{%/notice%}}


**Bước 1: Xem giá dịch vụ trên AWS Pricing Calculator**

+ Truy cập trang AWS Pricing Calculator (https://calculator.aws/#/)

+ Chọn Create estimate → Chọn Add service.

+ Tìm và chọn VPC Endpoint (hoặc "AWS PrivateLink").

+ Chọn thêm Elastic Load Balancing (ELB) (Network Load Balancer là một loại ELB).

+ Nhập các thông số dự kiến:
+ Số giờ vận hành (ví dụ: 720 giờ/tháng cho 1 tháng chạy liên tục).
+ Dung lượng dữ liệu dự kiến truyền tải (GB/ tháng).
+ Số lượng VPC Endpoint, số lượng subnets, số lượng AZ nếu có.
+ AWS Pricing Calculator sẽ hiện bảng tính ước tính chi phí hàng tháng cho bạn.
![S3](/images/4.s3/49-cost-1.png)
 ![S3](/images/4.s3/50-cost-2.png)


**Bước 2: Bật và sử dụng Cost Explorer**

+ Đăng nhập vào AWS Console.

+ Vào phần **Billing** → chọn **Cost Explorer.**

+ Nếu chưa bật, nhấn nút **Enable Cost Explorer** và đợi vài phút để kích hoạt.

Tạo báo cáo mới bằng cách:

+ Chọn Create report → Cost and Usage Report.

+ Lọc theo Service → chọn VPC Endpoint và Elastic Load Balancing.

+ Quan sát chi phí phát sinh theo thời gian, phân tích để tối ưu và dự báo ngân sách.
 

 ![S3](/images/4.s3/51-cost-3.png)
