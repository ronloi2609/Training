# Giao thức IP

----
## Giao thức IP là gì ?
see [Wikipedia](https://vi.wikipedia.org/wiki/IP)

> Internet Protocol (tiếng Anh, viết tắt: IP, có nghĩa là Giao thức Internet) là một giao thức hướng dữ liệu được sử dụng bởi các máy chủ nguồn và đích để truyền dữ liệu trong một liên mạng chuyển mạch gói.

----
## Cấu trúc địa chỉ IP
- Mạng Internet  dùng hệ thống địa chỉ IP (32 bit) để "định vị" các máy tính liên kết với nó.

- Hệ thống địa chỉ này được thiết kế mềm dẻo qua một sự phân lớp. Có 5 lớp địa chỉ IP là : A, B, C, D, E. Sự khác nhau cơ bản giữa các lớp địa chỉ này là ở khả năng tổ chức các cấu trúc con của nó. 

- Trong hệ thống địa chỉ IP được chia ra 2 loại địa chỉ:
 - Địa chỉ IPv4.
 - Địa chỉ IPv6.

- Trên thực tế nguồn tài nguyên địa chỉ IPv4 đang dần cạn kiệt, địa chỉ IPv6 là một giải pháp nhằm dần thay thế cho địa chỉ IPv4.

- Tại Việt Nam chúng ta vẫn sử dụng loại địa chỉ IPv4 với lý do chúng ta con quá nhiều máy tính không hỗ trợ cho địa chỉ IPv6.

- Địa chỉ IPv4 được cấu tạo bởi 32 bit và chia làm 4 octet, mỗi octet chiếm 8 bit.

- **Địa chỉ IP được cấu tạo bởi 2 phần chính là**:

![Địa chỉ IP](https://i.imgur.com/C2OHIIS.png)  

 - **Phần Network**: 
    - Do các tổ chức kiểm soát cấp cao cung cấp ( thường là đơn vị quản lý toàn bộ mạng Wan hoặc INternet).
    - Dùng để phân biệt giữa các mạng khác nhau.

 - **Phần host**:
    - Được cấp bởi quản trị mạng.
    - Dùng để phân biệt giữa các thiết bị hoặc các host trong 1 mạng.  

 - **Network Bits**:
   - Xác định phần địa chỉ mạng.
   - Chỉ ra lớp mạng (A, B, C...)
   - Không cho phép tất cả các Bit đều bằng 0.

 - ** Host Bits**:
   - Xác định phần địa chỉ host.
   - Tất cả các bit đều bằng 0 dùng để chỉ địa chỉ mạng.
   - Tất cả các bit đều bằng 1 dùng để chỉ địa chỉ Broadcast.




----
## Các lớp địa chỉ IP
![Các lớp](https://image.slidesharecdn.com/network-1206754309287969-2-130903092039-/95/network-12067543092879692-37-638.jpg?cb=1378200219)

## Lớp A

![lớp a](http://www.adminvietnam.org/wp-content/uploads/2016/10/class-A.png)

- Bit đầu tiên của lớp A luôn mang giá trị là 0.
- 8 bit (octet) đầu tiên dùng địa chỉ phần địa chỉ mạng.
- Địa chỉ mạng lớp A bắt đầu từ 1.0.0.0 đến 127.0.0.0
- Ba octet cuối dùng để đánh địa chỉ Host.
- Mỗi mạng lớp A có (2 mũ 24) hoặc 16,777,214 địa chỉ IP.

----

## Lớp B

![lớp b](https://adminvietnam.org/wp-content/uploads/2016/10/classB-696x120.png)

- Hai bit đầu tiên của địa chỉ lớp B luôn có giá trị là **10**.
- Hai Octet đầu tiên dùng để chỉ địa chỉ mạng.
- Địa chỉ mạng lớp B bắt đầu từ 128.0.0.0 đến 191.255.0.0
- Hai Octet còn lại của địa chỉ lớp B dùng để chỉ phần host.
- Một mạng B có thể có ((2 mũ 16) -2) hoặc 65.534 địa chỉ IP.

----

## Lớp C

![lớp C](https://adminvietnam.org/wp-content/uploads/2016/10/classC-696x122.png)

- Ba bit đầu tiên của 1 địa chỉ lớp C luôn bắt đầu bằng **110**.
- Ba Octet đầu tiên dùng để chỉ phần địa chỉ mạng.
- Địa chỉ lớp C bắt đầu bằng từ 192.0.0.0 đến 233.255.255.0.
- Octet cuối cùng của lớp C dùng để chỉ phần host
- Một mạng lớp C có thể có ((2 mũ 8) - 2) hoặc 254 địa chỉ IP.

---

## Lớp D

- Gồm các địa chỉ thuộc dải: 244.0.0.0 -> 239.255.255.255.
- Được sử dụng để làm địa chỉ multicast.
- Ví dụ : 224.0.0.5 dùng cho OSPF; 224.0.0.9 dùng cho RIPv2.

---

## Lớp E:

- từ 240.0.0.0 trở đi
- Được sử dụng cho mục đích dự phòng.

---

## Địa chỉ Private và Public

Địa chỉ IP được phân thành hai loại : **Private** và **Public**.

- **Private**: Chỉ được sử dụng trong mạng nội bộ (mạng LAN), không được định tuyến trên môi trường Internet. Có thể được sử dụng lặp lại trong các mạng LAN khác nhau .

- **Public**: là địa chỉ IP sử dụng cho các gói tin đi trên môi trường Internet, được định tuyến trên môi trường Internet. Địa chỉ public phải là duy nhất cho mỗi host tham gia vào Internet.
- **Dải địa chỉ private** (được quy định trong RFC 1918):
Lớp A:         10.0.0.0 -> 10.255.255.255
Lớp B:          172.16.0.0 -> 172.31.255.255
Lớp C:          192.168.0.0 -> 192.168.255.255

- Kỹ thuật NAT (Network Address Translation) được sử dụng để chuyển đổi giữa IP private và IP public.
- Ý nghĩa của địa chỉ private: được sử dụng để bảo tồn địa chỉ IP public.

---

## Địa chỉ  Broadcast

- Direct broadcast. Ví dụ: 192.168.1.255.
- Local broadcast. 255.255.255.255.

Để phân biệt 2 địa chỉ broadcast này , xem xét ví dụ sau:

Xét host có địa chỉ IP là 192.168.2.1. Khi host này gửi broadcast đến 255.255.255.255, tất cả các host thuộc mạng 192.168.2.0 sẽ nhận được gói broadcast này, còn nếu nó gửi broadcast đến địa chỉ 192.168.1.255 thì tất cả các host thuộc mạng 192.168.1.0 sẽ nhận được gói broadcast này).

---

## Subnet mask và số Prefix length
- **Subnet mask**: Subnet mask là một dãy nhị phân dài 32 bit đi kèm với một địa chỉ IP để cho phép xác định được network mà IP này thuộc về. Điều này được thực hiện bằng AND địa chỉ IP với subnet-mask theo từng bit một.
  - Ví dụ : Xét địa chỉ IP 192.168.1.1 với subnet-mask là 255.255.255.0. Để xác định địa chỉ mạng của đia chỉ này , thực hiện AND 192.168.1.1 với 255.255.255.0.

- Các **Subnet- mask chuẩn** của các địa chỉ lớp A,B,C:
 - Lớp A:          255.0.0.0
 - Lớp B:          255.255.0
 - Lớp C:          255.255.255.0
- **Prefix – length**: Một cách khác để hiển thị địa chỉ IP là sử dụng số prefix-length. Số prefix-length là số bit mạng trong một địa chỉ IP . Giá trị này được viết ngay sau địa chỉ IP và ngăn cách bởi dấu “/”
  - Ví dụ: 192.168.1.1/24, 172.16.2.1/16, 10.0.0.1/8,…
