#  Mô Hình OSI

----
## Mô hình OSI là gì?
see [Wikipedia](https://vi.wikipedia.org/wiki/M%C3%B4_h%C3%ACnh_OSI)

> **Mô hình OSI** (Open Systems Interconnection Reference Model) hay còn được gọi là “**Mô hình tham chiếu 7 tầng OSI**”. Mô hình OSI mô tả cách thức truyền tin từ các chương trình ứng dụng của một hệ thống máy tính đến các chương trình ứng dụng của một hệ thống khác thông qua các phương tiện truyền thông vật lý.

----
## Chi tiết mô hình OSI
![OSI](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8d/OSI_Model_v1.svg/476px-OSI_Model_v1.svg.png)

- **Mô hình OSI bao gồm 7 tầng**: 
 * Mỗi một tầng đều có đặc tính và chỉ sử dụng chức năng của tầng dưới nó, đồng thời chỉ cho phép tầng trên sử dụng các chức năng của mình.
 * Cho phép chia nhỏ hoạt động thành các phần công việc đơn giản.
 * Các nhà thiết kế có khả năng phát triển trên từng module chức năng với các chuẩn giao tiếp chung cung cấp khả năng “plug and play” và tích hợp nhiều nhà cung cấp sản phẩm.
 * **3 tầng dưới** (thực hiện trên kênh truyền): Định nghĩa cách thức thiết lập đầu cuối trên thiết bị phần cứng cho kết nối.
 * **4 tầng trên** (thực hiện trên host): Phục vụ cho việc định nghĩa các chuẩn chung phát triển trên ứng dụng, giao tiếp người dùng.

* **Tầng 1. Physical Layer**(*tầng vật lý*): **Cung cấp phương thức truy cập vào đường truyền vật lý** để truyền các dòng Bit không cấu trúc, **cung cấp các chuẩn** về điện, dây cáp, đầu nối, kỹ thuật nối mạch điện ...  

* **Tầng 2. Data link Layer**(*tầng liên kết dữ liệu*): **Xác định cơ chế truy nhập thông tin** trên mạng, **các dạng thức chung trong các gói tin, đóng gói** và **phân phát** các gói tin. Có 2 lớp gồm:
 * **LLC**( Điều khiển logic liên kết):quản lý các khung cho các tầng trên và dưới, kiểm soát lỗi, điều khiển luồng. 
 * **Mac**(Kiểm soát truy cập media): Mang địa chỉ vật lý của mỗi thiết bị.
* **Có thể hiểu**: *Ở thực tế tầng 2 là người hướng dẫn viên có trách nhiệm hướng dẫn và đảm bảo cho ta đến các địa điểm*.  


* **Tầng 3. Network layer**(*tầng mạng*):Có nhiệm vụ **xác định việc chuyển hướng, vạch đường các gói tin** cung cấp địa chỉ logic mã router sử dụng để xác định đường đi đến ( địa chỉ IP).
 * **Các giao thức hay dùng** : IP, RIP, IPX,OSPF,AppleTalk.


* **Tầng 4. Transport layer**(*tầng vận chuyển*):** Xác định địa chỉ mạng** trên mạng, **cách thức chuyển giao gói tin** trên cơ sở trực tiếp giữa hai đầu mút, duy trì kiểm soát dòng chảy dữ liệu, kiểm tra lỗi và khôi phục dữ liệu.
 * **Các giao thức**: TCP, UDP, SPX.


* **Tầng 5.Session layer**(*tầng giao dịch*): Thực hiện **thiết lập, duy trì và kết thúc các phiên làm việc** giữa 2 hệ thống.
 * **Các giao thức**: NFS,X-Window System, ASP.


* **Tầng 6.Presentation layer**(*tầng trình bày*): **Chuyển đổi thông tin** từ cú pháp người sử dụng sang cú pháp truyền thông. **Nén, mã hóa** dữ liệu trước khi truyền. 
 * **Các chuẩn định dạng**: GiF, JPEG, PICT, MP3,..  
* **Có thể hiểu**: *tầng 6 như người dịch giả giúp định dạng các dữ liệu*.  


* **Tầng 7.Application layer**(*tầng ứng dụng*): Quy định **giao tiếp giữa các người sử dụng và môi trường** OSI, **cung cấp phương tiện** cho người dùng truy cập và sử dụng các dịch vụ của mô hình OSI.
 * **Các giao thức**: HTTP, FPT, SMTP, POP3, Telnet.
* **Chú ý**: *Các trình duyệt( CocCoc, Chrome, IE, FireFox,.... không thuộc lớp này*.

* **Ví dụ thực tế**: Để giúp bạn nhớ các chức năng của từng lớp một cách dễ dàng hơn, tôi tạo ra một câu chuyện thú vị trong đó Henry (tiếng Anh) muốn gửi một tài liệu để Charles (Pháp) để chứng minh làm thế nào mô hình OSI làm việc.
![Ví dụ](http://www.9tut.com/images/ccna_self_study/OSI/OSI_7_layers_fun.jpg)
----


