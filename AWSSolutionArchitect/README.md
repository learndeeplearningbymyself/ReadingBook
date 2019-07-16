## AWS Solution Architect

### 6-4. S3

S3 (viết tắt của **Simple Storage Service**) là service lưu trữ object không hạn chế dung lượng cũng như có tính bền cao.

S3 khác với hệ thống lưu trữ file thông thường ở chỗ, S3 lưu trữ dưới cấu trúc flat chứ không phải cấu trúc thư mục (directory), ngoài ra người dùng cũng có thể gán các thông tin (**meta data**) cho dữ liệu.

Có thể sử dụng **REST** hoặc **SOAP (Simple Object Access Protocol)** để kết nối tới các object của S3.

Người dùng không chỉ sử dụng S3 như 1 công cụ để lưu trữ dữ liệu mà còn sử dụng dưới hình thức nơi lưu trữ **EBS Snapshot**, **AWS Backend Service**

Do tính mềm dẻo mà ta có thể sử dụng **S3** cho nhiều mục đích khác nhau. Tuy nhiên dưới đây là 1 vài **use cases** chủ yếu
- Data Backup
- Data leak để giải quyết Big Data
- Lưu trữ file trung gian ETL (Extract/ Transform/ Load)
- Địa chỉ gửi log của **EC2 instance**, **container**
- Static host
- Database cho kiểu dữ liệu đơn giản Key-Value

> Point: S3 là dịch vụ có tính chịu tải cao, lưu trữ object không hạn chế dung lượng, cũng như có thể sử dụng vào nhiều mục đích khác nữa


