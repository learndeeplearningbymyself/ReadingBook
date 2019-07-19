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

#### Các yếu tố cấu thành nên S3

- **Bucket**: là nơi lưu trữ các object của S3. Tên của bucket không hề liên quan đến tên của **region** hay **account**. Với quy ước tên này là duy nhất trong AWS

- **Object**: là đơn vị lưu trữ dữ liệu trong S3. Được gán **key** (tương tự như tên của object). **Bucket_Name + Object_key + Version_ID** sẽ tạo nên URL cho object (chắc chắn là duy nhất). Có thể sử dụng URL này thông qua Web API để thao tác với Object. Không hạn chế số lượng object lưu trong Bucket nhưng kích cỡ tối đa của object là 5TB.

- **Meta Data**: là thông tin dùng để quản lí object. Bao gồm metadata của hệ thống (thời gian tạo + size), cũng như metadata do user định nghĩa ở ứng dụng.

#### Tính bền và toàn vẹn của S3

Dữ liệu được lưu trữ trong S3, ngoài việc được lưu tại nhiều AZ, chúng còn được **duplicate** tại nhiều bộ nhớ vật lí trong AZ. Sau khi được lưu trữ, trong khoảng thời gian sau đó cho tới lúc quá trình duplicate nếu tham chiếu đến dữ liệu thì tuỳ vào địa chỉ tham chiếu, có thể sẽ hiển thị trạng thái trước khi lưu trữ.

#### Storage Class

S3 có 5 cấp độ (storage class)
- **STANDARD**
- **STANDARD-IA**
- **ONEZONE-IA**
- **INTELLIGENT-TIERING**
- **GLACIER**

#### Quản lí life cycle

Có thể định nghĩa vòng đời (life cycle) tương ứng với tần suất sử dụng các object được lưu trong S3. Việc thiết lập life cycle có thể lựa chọn một trong những cách sau:

- **Migration Action**: là hành động thay đổi storage class tương ứng với tần suất sử dụng của dữ liệu. VD: khi mới tạo thì object có tần suất truy xuất cao, sau một thời gian nhất định, thì tần xuất truy suất cũng như độ quan trọng sẽ giảm dần, từ đó có thể di chuyển đến storage class thích hợp

- **Expiration Date Action**: là hành động xoá đi các object vượt quá thời hạn sử dụng. Ta có thể quản lí việc xoá các objects với thời gian sử dụng nhất định hoặc các objects tạm thời. Do S3 là kiểu storage trả tiền tuỳ theo lượng lưu trữ, ta nên xoá 1 cách định kì các dữ liệu không cần thiết để giảm chi phí

#### Tính năng versioning

Là tính năng cho phép quản lí nhiều phiên bản của object.
Có thể chỉ định cho phép hoặc không cho phép tính năng này trong 1 bucket.
Versioning là lưu cả bản cũ, mới của object, kèm theo đó là version ID để phân biệt.

#### Tính năng Web hosting

S3 có thể tạo môi trường hosting cho static web.
Việc release nội dung tĩnh cũng tương tự như việc sử dụng S3 - lưu tại **S3 bucket**
Với web động thì không dùng S3 đươc, mà phải dùng EC2

**Những điểm cần chú ý khi sử dụng uniquely domain cho S3 web hosting**

Khi sử dụng S3 web hosting thì sẽ tự động tạo domain (FQDN). Trong trường hợp muốn domain này là duy nhất (unique) thì cần thiết lập thông tin **CNAME** cho **DNS** của **Route 53**
Trong trường hợp này cần match giữa **bucket name** và **domain name**
VD: nếu muốn domain là **www.example.com** thì cũng cần thiết lập tên cho bucket là **www.example.com**

Tuy nhiên trong trường hợp phía trước của S3 là **CloudFront** thì không cần match giữa **domain name** và **bucket name**

<img src="https://user-images.githubusercontent.com/43769314/61519551-20ba7000-aa47-11e9-865e-1dd1005d178c.png">

**Quản lí truy nhập S3**

Có 3 chế độ quản lí đó là **Bucket policy**, **ACL**, **IAM**
- **Bucket policy**: quản lí dựa theo đơn vị là **bucket**
- **ACL** (Access control list): quản lí dựa theo cơ chế **public**/ **private** đơn vị **object**.
- **IAM**: dùng trong TH điều khiển truy nhập S3 resource theo đơn vị **user**.

> Point: Có thể sử dụng Bucket policy, ACL, IAM để quản lí truy nhập S3. Có thể sử dụng Bucket policy với IAM user nhưng nên sử dụng IAM policy

#### URL có gắn chữ kí

Là tính năng đưa ra URL có chỉ định kì hạn đối với object mà ta muốn cho phép truy nhập
