---
title : "Xác thực bảo mật"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 4.3 </b> "
---
{{%notice note%}}
Mục tiêu: Xác thực kết nối PrivateLink hoàn toàn private và được kiểm soát.
{{%/notice%}}
+ Trong **bất kỳ** kiến trúc mạng nào, đặc biệt là khi triển khai các dịch vụ trên đám mây như AWS, việc đảm bảo bảo mật luôn là ưu tiên hàng đầu. Chương này tập trung vào việc **xác thực tính bảo mật và riêng tư của kết nối PrivateLink**, đảm bảo toàn bộ lưu lượng mạng giữa các thành phần trong hệ thống được truyền tải một cách an toàn, **không bị rò rỉ ra môi trường Internet công cộng.**

+ Mục tiêu chính của chương này là **kiểm tra và đảm bảo rằng toàn bộ kết nối giữa Consumer và Provider diễn ra hoàn toàn trong môi trường mạng riêng tư (private network),** không đi qua các điểm kết nối công cộng như **Internet Gateway**. Việc này không chỉ giúp bảo vệ dữ liệu nhạy cảm, tránh các rủi ro bị tấn công hoặc nghe lén, mà còn tuân thủ các yêu cầu về bảo mật và compliance của tổ chức hoặc các quy định pháp luật về bảo vệ thông tin.

+ Bên cạnh đó, chương cũng tập trung vào việc kiểm soát truy cập qua các chính sách bảo mật như security group và network ACL, đảm bảo chỉ những lưu lượng hợp lệ được phép đi qua, ngăn chặn các truy cập trái phép từ bên ngoài. Việc bật VPC Flow Logs giúp theo dõi và ghi nhận lưu lượng mạng chi tiết, cung cấp thông tin quan trọng để phân tích, phát hiện các bất thường hoặc sự cố bảo mật trong hệ thống.



**Bước 1: Đảm bảo không có Public Access**
+ Vào **EC2** → **Instances** → kiểm tra instance backend (Provider EC2) không có Public IP.

+ Vào **EC2** → **Load Balancers** → kiểm tra **Network Load Balancer** được cấu hình là **Internal (không có public IP).**

**Bước 2: Kiểm tra đường truyền gói tin (Packet Flow)**
+ **SSH vào Consumer EC2 instance.**

+ Chạy lệnh sau để kiểm tra đường đi đến service Provider qua domain nội bộ (private DNS):

+ **traceroute web.service.provider.local**

+ **Quan sát kết quả:**

+ Đường đi không được phép đi qua Internet Gateway (IGW).

+ Các hop phải thuộc private network, ví dụ IP trong CIDR của VPC/subnet, không thấy địa chỉ IP công khai.

**Bước 3: Bật VPC Flow Logs để theo dõi lưu lượng mạng**
Vào **VPC** → **Flow Logs** → chọn **Create flow log.**

+ Thiết lập như sau:

+ **Resource type: VPC.**

+ Chọn VPC của Consumer (VPC đang chứa Consumer EC2).

+ **Filter**: chọn ACCEPT (chỉ ghi nhận lưu lượng được phép).

+ **Destination**: chọn Send to CloudWatch Logs.

+ **Chọn hoặc tạo Log Group mới trong CloudWatch.**

+ Nhấn **Create** để bắt đầu thu thập log.

+ Sau đó bạn có thể vào CloudWatch Logs để xem các log lưu lượng mạng, xác thực lưu lượng đi qua PrivateLink đúng như mong muốn.


 
![S3](/images/4.s3/52-logs-1.png)
 ![S3](/images/4.s3/53-logs-2.png)
 ![S3](/images/4.s3/54-logs-3.png)
