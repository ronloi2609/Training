# VPN
# Mục lục 
>## 1. VPN là gì ?, Cách thức hoạt động
>## 2. Các mô hình kết nối VPN thông dụng
>## 3. Các giao thức sử dụng trong VPN
>## 4. Ưu và Nhược điểm của VPN

 ----

## 1 VPN là gì?
![](https://f9official.com/wp-content/uploads/2017/10/VPN-Featured-Image.png)
- **VPN (Virtual Private Network)**: là phương pháp làm cho một mạng công cộng (ví dụ như Internet) hoạt động giống như mạng nội bộ, có cùng các đặc tính như bảo mật và ưu tiên.

**Đơn giản hiểu** : VPN như là một đường hầm mà dữ liệu được mã hóa của bạn đi qua, giúp bạn an toàn hơn và ẩn danh khi trực tuyến.


### Cách thức hoạt động của VPN:
- **VPN thành lập các kết nối riêng** với người dùng ở xa, các văn phòng chi nhánh và đối tác sử dụng mạng công cộng.
 - **Mạng WAN truyền thống** yêu cầu công ty phải trả chi phí và duy trì nhiều loại đường dây riêng, song song với đầu tư thiết bị và đội ngũ cán bộ 
 - **VPN lại không bị rào cản** này vì được thực hiện qua mạng công cộng.

- VPN **mã hoá dữ liệu** ngăn ngừa các người dùng không được phép truy cập đến dữ liệu và bảo đảm dữ liệu không bị sửa đổi.
- **Định hướng đường hầm (tunneling)** là một cơ chế dùng cho việc đóng gói một giao thức vào trong một giao thức khác.
 - Trong ngữ cảnh **Internet**, **tunneling** cho phép những giao thức như **IPX, Apple Talk và IP được mã hoá**.
 - Trong ngữ cảnh **VPN**, tunneling **che giấu giao thức** lớp mạng nguyên thuỷ bằng cách **mã hoá gói dữ liệu** và **chứa gói đã mã hoá** vào trong một **vỏ bọc IP**. 

VPN còn cung cấp các thoả thuận về **chất lượng dịch vụ (QoS)**. 

#### *Ta có thể định nghĩa VPN qua công thức*:

**VPN = Tunneling + Bảo mật + Các thoả thuận về QoS**

----

## 2. Các mô hình kết nối VPN thông dụng

#### Mục tiêu công nghệ VPN quan tâm đến 3 yêu cầu :

* Các nhân viên, người dùng di động từ xa của một công ty có thể **truy cập vào tài nguyên mạng** của công ty họ bất cứ lúc
nào.

* Có khả năng **kết nối từ xa** giữa các nhánh văn phòng.
* **Kiểm soát truy cập** của các khách hàng, nhà cung cấp là đối tác quan trọng đối với giao dịch thương mại của công ty.

----

### 3 loại mô hình của VPN: 

* **VPN Truy cập từ xa (Remote Access VPN)**: **cung cấp kết nối** cho người dùng làm việc **từ xa và di động**. Nó là một sự thay thế cho các kết nối dial chuyên dụng hoặc ISDN. 

* **VPN Cục bộ (Intranet VPN)**: **kết nối trụ sở** công ty, văn phòng từ xa và văn phòng **chi nhánh** qua một cơ sở hạ tầng **chia sẻ sử dụng các kết nối** chuyên dụng.
 
* **VPN Mở rộng (Extranet VPN)**: kết nối khách hàng, nhà cung cấp, đối tác, hoặc cộng đồng người sử dụng thông qua một cơ sở hạ tầng chia sẻ sử dụng kết nối chuyên dụng. 

## 3. Các giao thức sử dụng trong VPN
> ### 3.1 Point-to-Point Tunneling Protocol (PPTP)
> ### 3.2 Internet Protocol Security (IPSec)
> ### 3.3 Layer2 Tunneling Protocol (L2TP)
> ### 3.4 Secure Socket Layer (SSL) 

### 3.1. Point-to-Point Tunneling Protocol (PPTP)

- PPTP là sự mở rộng của giao thức Internet chuẩn Point-to-Point (PPP) và sử dụng cùng kiểu xác thực như PPP (PAP, SPAP, CHAP, MS-CHAP, EAP).
- Là phương pháp VPN được hỗ trợ rộng rãi nhất giữa các máy trạm chạy Windows. 

PPTP **thiết lập đường hầm** (tunnel) nhưng **không mã hóa**.  

#### Ưu điểm khi sử dụng PPTP:
- là nó không yêu cầu hạ tầng mã khóa công cộng (Public Key Infrastructure).

### 3.2. Internet Protocol Security (IPSec)

- IPsec **tích hợp trong nhiều giải pháp VPN** "tiêu chuẩn", đặc biệt trong các giải pháp VPN gateway-to-gateway (site-to-site) để nối 2 mạng LAN với nhau. -
- IPsec **hoạt động tại tầng Mạng** (tầng 3) trong mô hình OSI.

**IPSec trong chế độ đường hầm**: bảo mật các gói tin trao đổi giữa hai gateway hoặc giữa máy tính trạm và gateway. 
  
- IPsec **chỉ hoạt động với các mạng và ứng dụng** dựa trên nền tảng IP (IP-based network). Giống như PPTP và L2TP, IPsec yêu cầu các máy tính trạm VPN phải được cài đặt sẵn phần mềm VPN client.

- Việc **xác thực** qua giao thức **Internet Key Exchange** (IKE) hoặc với **chứng chỉ số (digital certificates)** hoặc thông qua **khóa mã chia sẻ (preshared key)**.
- IPSec VPN có thể **chống lại hầu hết các phương pháp tấn công** thông dụng bao gồm **Denial of Service** (DoS - tấn công từ chối dịch vụ), **replay**, và **man-in-the-middle**.


### 3.3. Layer2 Tunneling Protocol (L2TP)
Giao thức Layer 2 Tunneling Protocol (L2TP) là sự kết hợp các đặc điểm của cả **PPTP và giao thức Layer 2 Forwarding (L2F)**.

- Giống như PPTP, L2TP **hoạt động tại lớp liên kết dữ liệu** (data link layer) của mô hình mạng OSI.

**L2TP** yêu cầu sử dụng chứng chỉ số (digital certificates).   

#### L2TP có một vài ưu điểm so với PPTP: 
 - PPTP cho người dùng khả năng bảo mật dữ liệu, nhưng L2TP còn tiến xa hơn khi cung cấp thêm khả năng **đảm bảo tính toàn vẹn dữ liệu**, khả năng **xác thực nguồn gốc** (xác định người dùng đã gửi dữ liệu có thực sự đúng người), và khả năng **bảo vệ chống gửi lại** – replay protection (chống lại việc hacker chặn dữ liệu đã được gửi.  

 - ví dụ thông tin quyền đăng nhập (credentials), rồi sau đó gửi lại (replay) chính thông tin đó để bẫy máy chủ. 

Mặt khác, do liên quan đến cung cấp các khả năng bảo mật mở rộng làm cho L2TP **chạy chậm hơn** chút ít so với PPTP.

### 3.4. Secure Socket Layer (SSL)
##### SSL còn được gọi là giải pháp "clientless".
- Điều này nghĩa là các giao thức có thể được xử lý bởi SSL sẽ bị hạn chế nhiều hơn. Nhưng nó đem lại lợi thế về bảo mật. 

**Với SSL**: 
 
- thay vì cho phép VPN client truy xuất vào toàn bộ mạng hoặc một mạng con (subnet) như với IPsec, có thể hạn chế chỉ cho phép truy xuất tới một số ứng dụng cụ thể.  
- Nếu một ứng dụng mà người dùng muốn họ truy cập không phải là là loại ứng dụng dựa trên trình duyệt (browser-based), thì cần phải tạo ra một plug-ins Java hoặc Active-X để làm cho ứng dụng đó có thể truy xuất được qua trình duyệt.

**SSL hoạt động ở tầng Phiên – cao hơn IPsec trong mô hình OSI**:  

- Điều này cho nó khả năng điều khiển truy cập theo khối tốt hơn. SSL sử dụng chứng chỉ số (digital certificates) để xác thực server. Mặc dù các phương pháp khác cũng có thể áp dụng, nhưng sử dụng chứng chỉ số được ưa chuộng vì khả năng bảo mật cao nhất.

## 4. Ưu điểm và nhược điểm của VPN

### Ưu điểm:
-  VPN là 1 giải pháp không hề tốn kém để xây dựng 1 hệ thống mạng riêng. 
- Môi trường Internet là cầu nối, giao tiếp chính để truyền tải dữ liệu nên chi phí rẻ hơn so với thiết lập 1 đường kết nối riêng với giá thành cao hơn.  

### Nhược điểm :

- VPN không có khả năng quản lý(QoS) qua môi trường Internet, do vậy các gói dữ liệu vẫn có nguy cơ bị thất lạc, rủi ro.
- Khả năng quản lý của các đơn vị cung cấp VPN là có hạn, không ai có thể ngờ trước được những gì có thể xảy ra với khách hàng của họ.