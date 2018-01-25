# Bộ giao thức TCP/IP

----
## TCP/IP là gì?
see [Wikipedia](https://vi.wikipedia.org/wiki/TCP/IP)
>
Bộ giao thức TCP/IP(Internet protocol suite hoặc IP suite hoặc TCP/IP protocol suite - bộ giao thức liên mạng), là một bộ các giao thức truyền thông cài đặt chồng giao thức mà Internet và hầu hết các mạng máy tính thương mại đang chạy trên đó. Bộ giao thức này
được đặt tên theo hai giao thức chính của nó là TCP (Giao thức Điều khiển Giao vận) và IP (Giao thức
Liên mạng). Chúng cũng là hai giao thức đầu tiên được định nghĩa. 


## Tổng quan
* Cho phép các hệ thống mạng không đồng bộ
kết nối với nhau.
* Ngày nay TCP/IP được sử dụng rộng rãi trong
hầu hết các mạng máy tính, và là giao thức chủ
yếu trên mạng internet.
* **Kiến trúc giao thức TCP/IP**

![Kiến trúc](https://i.imgur.com/ZRDW4kr.png)

* **So sánh với mô hình OSI**
![So sánh với OSI](https://i.imgur.com/ClwPUoG.png)

- **Giống nhau**:
 - Cả 2 đều có kiến trúc phân lớp.
 - Đều có lớp Applocation, mặc dù các dịch vụ ở mỗi lớp khác nhau.
 - Đều có các lớp Transport và Network.
 - Sử dụng kĩ thuật chuyển packet (packet-switched).
 - Các nhà quản trị mạng chuyên nghiệp cần phải biết rõ 2 mô hình này.

- **Khác nhau**:
 - Mô hình TCP/IP kết hợp lớp Presentation và lớp Session vào trong lớp Application.
 - Mô hình TCP/IP kết hợp lớp Data Link và lớp Physical vào trong một lớp.
 - Mô hình TCP/IP đơn giản hơn bởi vì có ít lớp hơn.
 - Nghi thức TCP/IP được chuẩn hóa và được sử dụng phổ biến trên toàn thế giới.
----
## Nhiệm vụ từng tầng
### 1. Tầng ứng dụng (Application layer):
* **Cung cấp các ứng dụng** để giải quyết sự cố mạng, vận chuyển file, điều khiển từ xa, và các hoạt động Internet. Đồng thời **hỗ trợ Giao diện Lập trình Ứng dụng** (API) mạng, cho phép các chương trình được thiết kế cho một hệ điều hành nào đó có thể truy cập mạng. 
* **Các giao thức làm việc**:
 * **Flie Transfer:** TFTP, FTP, NFS.
 * **E-mail**: SMTP.
 * **Remote Login**: Telnet, Rlogin.
 * **Network Managenment**: SNMP
 * **Name Management**: DNS

----
### 2. Tầng vận chuyển (Transport Layer):
* Giúp **kiểm soát luồng dữ liệu, kiểm tra lỗi** và **xác nhận các dịch vụ** cho liên mạng. Đóng vai trò giao diện cho các ứng dụng mạng.
- **Các giao thức hoạt động**: TCP, UDP.

----
### 3. Tầng Internet( Internet Layer)
- **Cung cấp địa chỉ logic**, độc lập với phần cứng, để dữ liệu có giao thông và hỗ trợ việc vận chuyển liên mạng.
- Thuật ngữ liên mạng được dùng để đề cập đến các thể lướt qua các tiểu mạng có cấu trúc vật lý khác nhau. **Cung cấp chức năng định tuyến** để giao lưu lượng mạng rộng lớn hơn, kết nối từ nhiều LAN.
- **Tạo sự gắn kết** giữa địa chỉ vật lý và địa chỉ logic.
 - **Các giao thức mạng**: IP, ICMP, ARP, RARP.

----
### 4. Tầng truy cập mạng( Network Access Layer)
- **Cung cấp giao diện** tương tác với mạng vật lý.
- **Format dữ liệu** cho bộ phận truyền tải trung gian và tạo địa chỉ dữ liệu cho các tiểu mạng dựa trên địa chỉ phần cứng vật lý.
- **Cung cấp việc kiểm tra lỗi** trong quá trình truyền dữ liệu.

----
### Hình ảnh tổng quan các giao thức dùng ở các tầng
![Giao thức](https://i.imgur.com/u0ueePB.png) 

- **FTP (File transfer Protocol)**: Giao thức truyền tệp cho phép người dùng lấy hoặc gửi tệp tới một máy khác.
- **Telnet**: Chương trình mô phỏng thiết bị đầu cuối cho phép người dùng login vào một máy chủ từ một máy tính nào đó trên mạng.
- **DNS (Domain Name server)**: Dịch vụ tên miền cho phép nhận ra máy tính từ một tên miền thay cho chuỗi địa chỉ Internet khó nhớ.
- **SMTP (Simple Mail Transfer Protocol)**: Một giao thức thư tín điện tử.
- **SNMP (Simple Network Monitoring Protocol)**: Giao thức quản trị mạng cung cấp những công cụ quản trị mạng từ xa.
- **RIP (Routing Internet Protocol)**: Giao thức dẫn đường  động.
- **ICMP (Internet Control Message Protocol)**: Nghi thức thông báo lỗi. 
- **UDP (User Datagram Protocol)**: Giao thức truyền không kết nối cung cấp dịch vụ truyền không tin cậy nhưng tiết kiệm chi phí truyền.
- **TCP (Transmission Control Protocol)**: Giao thức hướng kết nối cung cấp dịch vụ truyền thông tin tưởng.
- **IP (Internet Protocol)**: Giao thức Internet chuyển giao các gói tin qua các máy tính đến đích.
- **ARP (Address Resolution Protocol)**: Cơ chế chuyển địa chỉ TCP/IP  thành địa chỉ vật lý của các thiết bị mạng.


----

