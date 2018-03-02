# DNS

## 1 Khái niệm
DNS là từ viết tắt trong tiếng Anh của **Domain Name System**, là Hệ thống phân giải tên được phát minh vào năm 1984 cho Internet, chỉ một hệ thống cho phép thiết lập tương ứng giữa địa chỉ IP và tên miền.
  
- Hệ thống tên miền (DNS) là một hệ thống đặt tên theo thứ tự cho máy vi tính, dịch vụ, hoặc bất kỳ nguồn lực tham gia vào Internet.  
- Nó liên kết nhiều thông tin đa dạng với tên miền được gán cho những người tham gia. Quan trọng nhất là, nó chuyển tên miền có ý nghĩa cho con người vào số định danh (nhị phân), liên kết với các trang thiết bị mạng cho các mục đích định vị và địa chỉ hóa các thiết bị khắp thế giới.

## 2 Chức năng 
Quá trình **dịch tên miền thành địa chỉ IP** để cho trình duyệt hiểu và truy cập được vào website là công việc của một DNS server. Các DNS trợ giúp qua lại với nhau để dịch địa chỉ "IP" thành "tên" và ngược lại. 

## 3 Cấu hình DNS server

### 3.1 Cài đặt 
Sau khi thiết lập địa chỉ IP tĩnh cho máy chủ đảm nhận vai trò DNS Server, bạn thực hiện các lệnh sau để cài đặt gói BIND9  

    # sudo -i  
    # apt-get update  
    # apt-get install bind9   

  Sau khi cài đặt thành công, bạn thu được thu mục chính là **/etc/bind**. Trong thư mục này, bạn sẽ cấu hình các file sau:  

  **/etc/bind/named.conf.local**  
  **/etc/bind/db.local**


### 3.2 Cấu hình

Trước tiên, bạn mở file /etc/bind/named.conf.local và bổ sung một zone mới, chẳng hạn tuananh.org:  

    zone "tuananh.org" {  
     type master;  
          file "/etc/bind/db.tuananh.org";  
    };

Tiếp theo, bạn tạo file cơ sở dữ liệu DNS 
**/etc/bind/db.tuananh.org** bằng cách sao chép nội dung từ file mẫu **/etc/bind/db.local**:

    # cp /etc/bind/db.local /etc/bind/db.hoanghac.org


Đến đây, bạn hiệu chỉnh file **/etc/bind/db.tuananh.org** bằng cách thay localhost. 
  
Bằng tên đầy đủ của máy chủ DNS (FQDN). Thay 127.0.0.1 bằng địa chỉ IP của DNS Server và root.localhost thành một địa chỉ email chính xác, nhưng sử dụng dấu chấm "." thay vì biểu tượng "@”.
  
Đồng thời, bạn cũng tạo ra một bản ghi (A) tương ứng với ns.hoanghac.org. Nội dung của file sẽ như sau:  

    ;
     ; BIND data file for local loopback interface
     ;
     $TTL 604800
    @    IN    SOA   ns.hoanghac.org.  root.hoanghac.org. (
                       2          ; Serial
                  604800          ; Refresh
                   86400          ; Retry
                 2419200          ; Expire
                  604800 )        ; Negative Cache 
    TTL
    ;
    @    IN    NS ns.hoanghac.org.
    @    IN    A 192.168.1.10
    @    IN    AAAA ::1
    ns   IN    A 192.168.1.10

Tiếp theo, bạn khởi động lại dịch vụ **BIND9** để những thao tác cấu hình vừa thực hiện có hiệu lực:

    # /etc/init.d/bind9 restart

### 3.3 Kiểm tra

Để kiểm tra hoạt động của DNS Server, bạn sử dụng lệnh ping như sau:

    # ping ns.tuananh.org