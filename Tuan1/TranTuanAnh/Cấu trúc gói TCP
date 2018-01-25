----
## Cấu trúc của các gói tin
## TCP (Transmisson control protocol)
* **Một gói tin TCP bao gồm 2 phần**
 * **Header**
 * **Dữ liệu**
* Phần header có 11 trường trong đó 10 trường bắt buộc. Trường thứ 11 là tùy chọn (trong
bảng minh họa có màu nền đỏ) có tên là: options.

* **Header**
![Header](https://i.imgur.com/NQbHqd9.png)

 * **Source port**: Số hiệu của cổng tại máy tính gửi.
 * **Destination port**: Số hiệu của cổng tại máy tính nhận.
 * **Sequence number**: Trường này có 2 nhiệm vụ. Nếu cờ SYN bật thì nó là số thứ tự gói ban đầu và byte đầu tiên được gửi có số thứ tự này cộng thêm 1. Nếu
không có cờ SYN thì đây là số thứ tự của byte đầu tiên.
 * **Acknowledgement number**: Nếu cờ ACK bật thì giá trị của trường chính là số thứ tự gói tin tiếp theo mà bên nhận cần.
 * **Data offset**: Trường có độ dài 4 bít qui định độ dài của phần header (tính theo đơn vị từ 32 bít). Phần header có độ dài tối thiểu là 5 từ (160 bit) và tối đa là 15 từ (480 bít).
  * **Reserved** Dành cho tương lai và có giá trị là 0.

* Cấu trúc gói tin TCP.
  * **Flags** (hay Control bits).
 * Bao gồm 6 cờ:
 	* **URG** Cờ cho trường Urgent pointer.
 	* **ACK** Cờ cho trường Acknowledgement.
 	* **PSH** Hàm Push.
 	* **RST** Thiết lập lại đường truyền.
 	* **SYN** Đồng bộ lại số thứ tự.
 	* **FIN** Không gửi thêm số liệu.

 * **Window** Số byte có thể nhận bắt đầu từ giá trị của trường báo nhận (ACK)
 * **Checksum (16 bit)**:  kiểm tra cho cả phần header và dữ liệu.
 * **Urgent Poiter ( 16bits )** : con trỏ này trỏ tới số hiệu tuần tự của byte đi theo sau sữ liệu khẩn, cho phép bên nhận biết được độ dài của dữ liệu khẩn, chỉ có hiệu lực khi bit URG được thiết lập.
 * **Options ( độ dài thay đổi )** : khai báo các options của TCP.
 * **Padding ( độ dài thay đổi )** : Phần chèn thêm vào header để đảm bảo đủ kích thước.
 * **TCP data** : phần dữ liệu của TCP segment.

* **Dữ liệu**
   * Trường cuối cùng không thuộc về header. Giá trị của trường này là thông tin dành cho các tầng trên (trong mô hình 7 lớp OSI). Thông tin về giao thức của tầng trên không được chỉ rõ trong phần header mà phụ thuộc vào cổng được chọn.