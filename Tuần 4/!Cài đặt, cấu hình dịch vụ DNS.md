# DNS

## Khái niệm, cấu hình DNS sever vs Bind

## 1 Khái niệm
DNS là từ viết tắt trong tiếng Anh của **Domain Name System**, là Hệ thống phân giải tên được phát minh vào năm 1984 cho Internet, chỉ một hệ thống cho phép thiết lập tương ứng giữa địa chỉ IP và tên miền.
  
- Hệ thống tên miền (DNS) là một hệ thống đặt tên theo thứ tự cho máy vi tính, dịch vụ, hoặc bất kỳ nguồn lực tham gia vào Internet.  
- Nó liên kết nhiều thông tin đa dạng với tên miền được gán cho những người tham gia. Quan trọng nhất là, nó chuyển tên miền có ý nghĩa cho con người vào số định danh (nhị phân), liên kết với các trang thiết bị mạng cho các mục đích định vị và địa chỉ hóa các thiết bị khắp thế giới.

**Hiện nay hệ thống tên miền được phân thành nhiêu cấp**:

 - ** Gốc (Domain root)** : Nó là đỉnh của nhánh cây của tên miền. Nó có thể biểu diễn đơn giản chỉ là dấu chấm “.”  
 - **Tên miền cấp một (Top-level-domain) :** gồm vài kí tự xác định một nước, khu vưc hoặc tổ chức. Nó được thể hiện là “.com” , “.edu”,...  
 - **Tên miền cấp hai (Second-level-domain)**: Nó rất đa dạng rất đa dạng có thể là tên một công ty, một tổ chức hay một cá nhân.
 - **Tên miền cấp nhỏ hơn (Subdomain):** Chia thêm ra của tên miền cấp hai trở xuống thường được sử dụng như chi nhánh, phòng ban của một cơ quan hay chủ đề nào đó.

**Phân loại tên miền:**

 - **Com:** dùng cho các tổ chức thương mại.  
 - **Edu:** dùng cho các cơ quan giáo dục, trường học.  
 - **Net:** dùng cho các tổ chức mạng lớn.  
 - **Gov:** dùng cho các tổ chức chính phủ.  
 - **Org:** dùng cho các tổ chức khác.  
 - **Int:** dùng cho các tổ chức quốc tế.
 - **Info:** dùng cho việc phục vụ thông tin.
 - **Arpa:** tên miền ngược.
 - **Mil:** dành cho các tổ chức quân sự, quốc phòng

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

    # cp /etc/bind/db.local /etc/bind/db.tuananh.org


Đến đây, bạn hiệu chỉnh file **/etc/bind/db.tuananh.org** bằng cách thay localhost. 
  
Bằng tên đầy đủ của máy chủ DNS (FQDN). Thay 127.0.0.1 bằng địa chỉ IP của DNS Server và root.localhost thành một địa chỉ email chính xác, nhưng sử dụng dấu chấm "." thay vì biểu tượng "@”.
  
Đồng thời, bạn cũng tạo ra một bản ghi (A) tương ứng với ns.tuananh.org. Nội dung của file sẽ như sau:  

    ;
     ; BIND data file for local loopback interface
     ;
     $TTL 604800
    @    IN    SOA   ns.tuananh.org.  root.tuananh.org. (
                       2          ; Serial
                  604800          ; Refresh
                   86400          ; Retry
                 2419200          ; Expire
                  604800 )        ; Negative Cache 
    TTL
    ;
    @    IN    NS ns.tuananh.org.
    @    IN    A 192.168.1.10
    @    IN    AAAA ::1
    ns   IN    A 192.168.1.10

Tiếp theo, bạn khởi động lại dịch vụ **BIND9** để những thao tác cấu hình vừa thực hiện có hiệu lực:

    # /etc/init.d/bind9 restart

### 3.3 Kiểm tra

Để kiểm tra hoạt động của DNS Server, bạn sử dụng lệnh ping như sau:

    # ping ns.tuananh.org  


## 4. Xây dựng mô hình DNS master- slave
Mục đích của việc xây dựng Slave DNS chính là thực hiện nhiệm vụ sao lưu dự phòng cho Master DNS. Vì khi Master DNS có sự cố thì việc phân giải tên miền sẽ không thể phân giải được. Slave DNS sẽ giải quyết vấn đề đó khi Master DNS không thể hoạt động vì một lý do nào đó.  

### 4.1 Máy Master

Cấu hình như phần 3 và ta gắn thêm cho nó các dải địa chỉ IP:  
- 192.168.1.10 - tuananh.org
- 192.168.1.11 - dns1.tuananh.org (Địa chỉ máy Master)
- 192.168.1.12 - dns2.tuananh.org (Địa chỉ máy Slave)  

**Bước 1**: 
 - Tạo file `db.forward.com` bằng cách coppy file `db.local` từ **/etc/bind/**, chỉnh sửa hostname, thêm các tên miền mối và địa chỉ.
 - Tạo file `db.resere.com` bằng cách coppy file `db.127` từ **etc/bind/**, chỉnh sửa hostname, thêm các tên miền mới và địa chỉ.  

**Bước 2**:  
 - Sửa file name.conf.local. Ta thêm một số dòng vào zone thuận, cho phép tự động cập nhật trên đường mạng 192.168.1.0/24 và transfer sang máy Slave DNS 192.168.10.4. Ở đây chúng ta đang cấu hình trên máy Master DNS nên type là master.  

    zone "tuananh.org"{
    	type master;
    	file "/etc/bind/db.forward.com"  
    	allow-update {192.168.1.0/24;};
    	allow-transfer {192.168.1.12;};
    };  
    zone "10.168.192.in-addr.arpa"{
    	type master;
    	file "etc/bind/db.reverse.com";
    	allow-update {192.168.1.0/24;};
    	allow-transfer {192.168.1.12;};
    }  

**Bước 3**:
- Thêm địa chỉ máy Slave vào file `db.forward.com` và file `db.reverse.com` 
- Khởi động lại dịch vụ bind: `sudo /etc/init.d/bind9 restart`  
- Dùng lệnh `dig` để kiểm tra. 

### 4.2 Máy Slave 
**Bước 1:**

- Thiết lập Ip tĩnh cho máy:
`sudo ifconfig enp0s3 192.168.1.12 netmask 255.255.255.0`  
`sudo route add default gw 192.168.1.1`

**Bước 2**:

- Sửa file **/etc/resolv.conf**  

    nameserver 192.268.1.10
    search tuananh.org  

**Bước 3:**
- Thêm tham số allow-transfer và master vào file **/etc/bind/name.còn.local**, type là slave tương tự như mục 4.1.  
- Khởi động lại dịch vụ `sudo /etc/init.d/bind9 restart`
- Dùng lệnh `dig` để kiểm tra. 
