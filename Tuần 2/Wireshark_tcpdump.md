# Wireshark 
**Wireshark** là một công cụ kiểm tra, theo dõi và phân tích thông tin mạng được phát triển bởi Gerald Combs.

Phiên bản đầu tiên của Wireshark mang tên Ethereal được phát hành năm 1988. Đến nay, WireShark vượt trội về khả năng hỗ trợ các giao thức (khoảng 850 loại), từ những loại phổ biến như TCP, IP đến những loại đặc biệt như là AppleTalk và Bit Torrent. 

### 1. Bắt gói tin
Giao diện chương trình:
![](https://i.imgur.com/cbiZhsk.png)

Interface List:

* WireLess Network Connection (Mạng WiFi)
* Local Area Connection (Mạng LAN)

Click icon trong hình để chọn Interface cần bắt gói tin
![](https://i.imgur.com/nZdnMAf.png)
Click **Start** để bắt đầu bắt gói tin.

Ngay sau đó, chúng ta sẽ thấy các gói dữ liệu bất đầu xuất hiện, Wireshark sẽ “bắt” từng gói – package ra và vào hệ thống mạng.

Click icon để dừng quá trình bắt gói tin.
![](https://i.imgur.com/BT9GQZK.png)

Chọn File => Save để lưu lại thành file. Sau này có thể mở ra để xem lại.

Click icon để bắt đầu một quá trình khác.
![](https://i.imgur.com/I3oaVex.png)

Chọn **Save** để lưu lại. Chọn **Continue without Saving** nếu không muốn lưu.
![](https://i.imgur.com/zMwxuv5.png)

Giao diện chương trình khi bắt gói tin:
![](https://i.imgur.com/SUohcoL.png)

Chúng ta sẽ thấy có nhiều màu sắc khác nhau. Wireshark dựa vào cơ chế này để giúp người dùng phân biệt được các loại traffic khác nhau.

Các cột: 

* Time: thời gian
* Source: địa chỉ nguồn
* Destination địa chỉ đích
* Protocol: giao thức
* Length: độ dài gói tin
* Info: thông tin

Danh sách gói tin:
![](https://i.imgur.com/IW7lqpf.png)

### 2. Lọc gói tin
Nhập từ khóa vào ô Filter rồi nhấn Enter, Wireshark sẽ tìm những gói tin với thông tin trên.

VD. Nhập "tcp", Wireshark sẽ chỉ ra những gói sử dụng giao thức TCP để truyền và nhận.

![](https://i.imgur.com/mMIlNo8.png)

VD. Tìm những gói tin có địa chỉ nguồn là *192.168.1.3* và địa chỉ đích là *2.17.150.138*.

![](https://i.imgur.com/Y8qlgth.png)

Nhấp chuột phải vào một packet, chúng ta sẽ thấy toàn bộ quãng thời gian giao tiếp giữa server và client.
![](https://i.imgur.com/XaCLNe3.png)

![](https://i.imgur.com/ObjYIDQ.png)

### 3. Kiểm tra gói tin
Thông tin của một gói tin cụ thể:
![](https://i.imgur.com/lTK9vlT.png)


# tcpdump
**tcpdump** là công cụ được phát triển nhằm mục đích phân tích các gói dữ liệu mạng theo dòng lệnh. Nó cho phép người dùng chặn và hiển thị các gói tin được truyền đi hoặc được nhận trên một mạng mà máy tính có tham gia.

### 1. Cài đặt
Ở Ubuntu, dùng lệnh: `sudo apt-get install tcpdump -y`

### 2. Vài lệnh cơ bản
* Xem các interface đang hoạt động: `tcpdump -D`

![](https://i.imgur.com/KqWgQoe.png)

* Bắt gói tin trên 1 interface: `tcpdump -i <INTERFACE>`

VD. Bắt gói tin trên interface enp0s3.

![](https://i.imgur.com/ZGyFelr.png)

Bấm tổ hợp phím Ctrl + C để dừng.

Sau khi dừng, một vài thông số sau sẽ hiện ra:

* **Packet capture**: số lượng gói tin bắt được và xử lý.
* **Packet received by filter**: số lượng gói tin được nhận bởi bộ lọc.
* **Packet dropped by kernel**: số lượng packet đã bị dropped bởi cơ chế bắt gói tin của hệ điều hành.

Định dạng chung của một dòng giao thức tcpdump:

`time-stamp src > dst:  flags  data-seqno  ack  window urgent options`


|Tên trường|Mô tả|
|---|---|
|Time-swamp|hiển thị thời gian gói tin được bắt.|
|Src và dst|hiển thị địa IP của người gửi và người nhận.|
|Cờ Flag|S(SYN): Được sử dụng trong quá trình bắt tay của giao thức TCP.<br>.(ACK): Được sử dụng để thông báo cho bên gửi biết là gói tin đã nhận được dữ liệu thành công.<br>F(FIN): Được sử dụng để đóng kết nối TCP.<br>P(PUSH): Thường được đặt ở cuối để đánh dấu việc truyền dữ liệu.<br>R(RST): Được sử dụng khi muốn thiết lập lại đường truyền.|
|Data-sqeno|Số sequence number của gói dữ liệu hiện tại.|
|ACK|Mô tả số sequence number tiếp theo của gói tin do bên gửi truyền (số sequence number mong muốn nhận được).|
|Window|Vùng nhớ đệm có sẵn theo hướng khác trên kết nối này.|
|Urgent|Cho biết có dữ liệu khẩn cấp trong gói tin.|

* Bắt n gói tin với tùy chọn -c

`tcpdump -c n -i enp0s3`

Mặc định, tcpdump sẽ bắt liên tiếp các gói tin. Để dừng quá trình này, chúng ta phải thao tác tổ hợp phím Ctrl + C. Nhưng với tùy chọn -c, chúng ta có thể chỉ cho tcpdump biết là "Tôi chỉ muốn bắt n gói."

VD. Bắt 3 gói tin.

![](https://i.imgur.com/rgazd0u.png)

* Lưu file .pcap

`tcpdump -i enp0s3 -w <FILENAME>`

* Đọc file .pcap

`tcpdump -r <FILENAME>`

* Bắt các gói tin theo giao thức

`tcpdump -i enp0s3 <PROTOCOL> -c n`

(n: số gói tin cần bắt)

VD. Bắt các gói TCP

![](https://i.imgur.com/3pq95od.png)

* Bắt theo địa chỉ nguồn hoặc đích

`tcpdump -i emp0s3 src <IP_SOURCE>`

`tcpdump -i emp0s3 src <IP_DESTINATION>`
