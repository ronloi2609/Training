
#  Giao thức UDP

----
## Giao thức UDP là gì?
see [Wikipedia](https://vi.wikipedia.org/wiki/UDP)

> Giao thức UDP(User Datagram Protocol) là giao thức phi kết nối (connectionless) hoạt động trên tầng giao vận(Transport) của chồng giao thức TCP/IP.  
UDP cũng là một giao thức truyền thông không tin cậy.  
Các giao thúc sử dụng trên UDP: TFTP, SNMP, DHCP, DNS.

----
## Các đặc điểm của giao thức
1. UDP đơn giản và hiệu quả, nhưng không tin cậy.
2. UDP là giao thức phi kết nối(connectionless).
3. Không có cơ chế báo nhận(acknowledgement) để đảm bảo dữ liệu đi đến đích.
4. Không cung cấp cơ chế điều khiển luồng(follow control).
5. Tính tin cậy của dữ liệu sẽ được kiểm tra nhờ các giao thức ở lớp trên.

-----
## Các cổng dịch vụ
----
![Cổng dịch vụ](https://i.imgur.com/zLf5kl6.png)

- Cả TCP và UDP đều sử dụng các chỉ số port để chuyển thông tin lên các lớp trên.
- Các chỉ số port dùng để theo dõi các cuộc đàm thoại khác nhau xuyên qua mạng cùng một lúc.
- Quy định phát triển phần mềm ứng dụng thống nhất dùng các chỉ số port đặc biệt được kiểm soát bởi IANA.

# Các dải chỉ số port quy định:
- Các chỉ số **Port < 255** cho các ứng dụng **công cộng**.
- Các chỉ số **Port từ 255-1023** được gán cho các công ty trong các **ứng dụng thương mai**.
- Các chỉ số **Port > 1023 không được quy định** sắp xếp rõ ràng.

----

