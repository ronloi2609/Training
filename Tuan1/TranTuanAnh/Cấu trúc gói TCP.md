# Giao thức TCP

----
## TCP là gì?
see [Wikipedia](https://vi.wikipedia.org/wiki/TCP)

> TCP (Transmission Control Protocol - "Giao thức điều khiển truyền vận") là một trong các giao thức cốt lõi của bộ giao thức TCP/IP. Sử dụng TCP, các ứng dụng trên các máy chủ được nối mạng có thể tạo các "kết nối" với nhau, mà qua đó chúng có thể trao đổi dữ liệu hoặc các gói tin..

----
## Khái quát TCP
1. TCP là một giao thức hướng kết nối (connection-oriented), hoạt động trên lớp giao vận(Transport) của chồng giao thức TCP/IP.
2. TCP cũng là một giao thức truyền thông tin cậy
3. Các giao thức sử dụng trên TCP: HTTP, FTP, SMTP, DNS, Telnet....


----
## Đặc điểm của giao thức
- Tạo cầu nối, một kết nối được thiết lập giữa các thiết bị đầu cuối trước khi truyền. 

- Tin cậy, điều khiển luồng (follow control) và có cơ chế báo nhận (acknowlegement).

- Tại nơi nhận nó lại tái tạo lại bản tin (message) từ các Segment .

- Truyền lại bất cứ segment bị lỗi.
- TCP hỗ trợ các kênh ảo (virtual circuit) giữa các ứng dụng đầu cuối.


----
## Quá trình thiết lập kết nối

![Thiết lập kết nối](https://i.imgur.com/NxAvUYy.png)

## Cơ chế bắt tay 3 bước:
- Để 2 máy trong 1 hệ thống mạng có thể truyền tin được cho nhau chúng phải tạo được 1 kế nối đến nhau. 
Quá trình đó được thực hiện như sau: 
 1. ULP B giả sử là một chương trình mail server ở Mỹ. Do là server nên lúc nào nó cũng chờ đợi sự kết nối.
 - ULP A là chương trình nhận thư điện tử của bạn. Để kết nối, bạn gửi yêu cầu kết nối xuống cho tầng TCP.
 - TCP chuẩn bị một gói dữ liệu TCP với cờ SYN=1 yêu cầu có sự đồng bộ hoá, SEQ có thể lấy bất kì giá trị nào, ở đây là =100 và gửi cho TCP B.
 - Sau khi nhận gói dữ liệu có SYN=1, TCP B gửi trả lại một thông báo có SYN=1, ACK=101, SEQ có thể lấy bất kì giá trị nào, ở đây là =177.
 - TCP A nhận được gói dữ liệu từ TCP B sẽ gửi tiếp một gói dữ liệu có ACK=178.
 - TCP A chuyển chấp nhận kết nối lên chương trình A.
 - Sau khi nhận nốt gói dữ liệu có ACK=178, TCP B chuyển chấp nhận kết nối lên chương trình B.