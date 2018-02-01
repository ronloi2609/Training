# Router
## Mục lục
> ### 1. Khái niệm Router
> ### 2. Tầng hoạt động của Router
> ### 3. Chức năng của Router

## 1. Khái niệm Router
##### Router hay còn gọi là thiết bị định tuyến hoặc bộ định tuyến:
- là một thiết bị mạng máy tính dùng để **chuyển các gói dữ liệu** qua một liên mạng và đến các đầu cuối, thông qua một tiến trình được gọi là định tuyến.

### Ưu điểm của Router:  
- Về mặt vật lý, Router có thể kết nối với các loại mạng khác lại với nhau, từ những Ethernet cục bộ tốc độ cao cho đến đường dây điện thoại đường dài có tốc độ chậm.

### Nhược điểm của Router:  
-  Router **chậm hơn** Bridge vì chúng đòi hỏi nhiều tính toán hơn để tìm ra cách dẫn đường cho các gói tin, đặc biệt khi các mạng kết nối với nhau không cùng tốc độ.  
- Router có đặc điểm **chuyên biệt theo giao thức**. Tức là cách một máy tính kết nối mạng giao tiếp với một router IP thì sẽ khác biệt với cách nó giao tiếp với một router Novell hay DECnet. 
- Tất cả các Router thương mại đều có thể xử lý nhiều loại giao thức, thường với chi phí phụ thêm cho mỗi giao thức.

## 2.Tầng hoạt động của Router
- Router hoạt động ở **tầng 3**, trên nền giao thức IP, nên có thể **tái tạo** lại các packet ở tầng 3 và **đọc** được các thông số IP, dựa vào nó mà **so sánh** với bảng routing (bảng dẫn đường) để chuyển tiếp gói tin trong mạng Lan hay Wan.
- Nhiệm vụ của Router đều là **định tuyến hết**. Nhưng ở Wan, thì sẽ có thêm một chức năng quan trọng hơn, đó là **kết nối các đường truyền** chạy các giao thức khác nhau, làm cho chúng hiểu được nhau.  

## 3. Chức năng của Router

- Theo cách nói thông thường, một router hoạt động như một **liên kết giữa hai hoặc nhiều mạng và chuyển các gói dữ liệu** giữa chúng. Router đưa vào **bảng định tuyến (routing table)** để tìm đường đi cho gói dữ liệu.

**Bảng định tuyến được người quản trị mạng cấu hình tĩnh (static).**
  
> Được thiết lập một lần và thường do quản trị mạng nhập bằng tay, hoặc động (dynamic).  
>  Bảng tự học đường đi thông qua các giao thức định tuyến và nội dung tự động thay đổi theo sự thay đổi của tô pô mạng.  

- **Phân cách** các mạng máy tính thành các segment riêng biệt để giảm hiện tượng **đụng độ**, giảm **broadcast** hay thực hiện chức năng bảo mật.

- **Kết nối** các mạng máy tính hay kết nối các user với mạng máy tính **ở các khoảng cách xa** với nhau thông qua các đường truyền thông: Điện thoại, ISDN, T1, X.25…

- Switch phát triển, Router chỉ còn phải đảm nhận việc thực hiện các kết nối truy cập từ xa **(remote access)** hay các **kết nối WAN** cho hệ thống mạng LAN.

Do hoạt động ở tầng thứ 3 của mô hình OSI, router sẽ hiểu được các protocol quyết định phương thức truyền dữ liệu. Các địa chỉ mà router hiểu là các địa chỉ “giả” được quy định bởi các protocol. Ví dụ như địa chỉ IP đối với protocol TCP/IP, địa chỉ IPX đối với protocol IPX… Do đó tùy theo cấu hình, router quyết định phương thức và đích đến của việc chuyển các packet từ nơi này sang nơi khác. Một cách tổng quát router sẽ chuyển packet theo các bước sau:  

- Đọc packet.
- Gỡ bỏ dạng format quy định bởi protocol của nơi gửi.
- Thay thế phần gỡ bỏ đó bằng dạng format của protocol của đích đến.
- Cập nhật thông tin chuyển dữ liệu: địa chỉ, trạng thái của nơi gửi, nơi nhận.
- Gứi packet đến nơi nhận qua đường truyền tối ưu nhất.

-----

# Switch
## Mục lục
> ### 1. Khái niệm Switch 
> ### 2. Chức năng của Switch
> ### 3. Phân loại

## 1. Switch là gì?
### Switch hay còn gọi là thiết bị chuyển mạch  
- là một thiết bị dùng để kết nối các đoạn mạng với nhau theo mô hình mạng hình sao (star).
- Theo mô hình này, switch đóng vai trò là thiết bị trung tâm, tất cả các máy tính đều được nối về đây.

Switch làm việc như một **Bridge** nhiều cổng.  
 
Khác với Hub nhận tín hiệu từ một cổng rồi chuyển tiếp tới tất cả các cổng còn lại, switch **nhận tín hiệu vật lý** chuyển đổi thành dữ liệu từ một cổng, **kiểm tra địa chỉ đích** rồi gửi tới một cổng tương ứng.


![](https://networklessons.com/wp-content/uploads/2016/12/switch-star-topology-hosts.png)

Trong mô hình tham chiếu **OSI**, switch hoạt động ở **tầng Liên kết dữ liệu**, ngoài ra có một số loại switch cao cấp hoạt động ở tầng Mạng.

## 2. Chức năng của Switch
* Switch quyết định chuyển frame dựa trên địa chỉ MAC,  được xếp vào **thiết bị Lớp 2**. Chính nhờ Switch có khả năng **lựa chọn đường dẫn** để chuyển frame nên mạng LAN có thể hoạt động hiệu quả hơn.
* Switch nhận biết máy nào kết nối với cổng của nó bằng cách học địa chỉ MAC nguồn trong frame mà nó nhận được.
* Switch **chỉ thiết lập một mạch ảo** giữa hai cổng tương ứng mà không làm ảnh hưởng đến lưu thông trên các cổng khác => mạng LAN có hiệu suất cao thường sử dụng chuyển mạch toàn bộ.

* Switch xử lý **mỗi cổng là một đoạn mạng riêng biệt**. Khi các máy ở các cổng khác nhau cần liên lạc với nhau, Switch sẽ chuyển frame từ cổng này sang cổng kia và đảm bảo cung cấp chọn băng thông cho mỗi phiên kết nối.

## 3. Phân loại Switch

* **Workgroup switch**: được thiết kế nhằm để **nối trực tiếp** các máy tính lại với nhau hình thành một mạng ngang hàng. Như vậy, tương ứng với một cổng của switch chỉ có **một địa chỉ** máy tính trong bảng địa chỉ. Giá thành thấp hơn các loại khác. Vì thế, loại này không cần thiết phải có bộ nhớ lớn cũng như tốc độ xử lý cao. 

* **Segment switch**: **nối các Hub hay workgroup switch** lại với nhau, hình thành một liên mạng ở tầng hai. Tương ứng với mỗi cổng trong trường hợp này sẽ có **nhiều địa chỉ** máy tính, vì thế bộ nhớ cần thiết phải đủ lớn. Tốc độ xử lý đòi hỏi phải cao vì lượng thông tin càn xử lý tại switch là lớn.

* **Backbone switch**: kết **nối các segment switch** lại với nhau. **Bộ nhớ và tốc độ xử lý** của switch phải rất **lớn để đủ chứa địa chỉ** cho tất cả các máy tính trong toàn liên mạng và hoán chuyển kịp thời dữ liệu giữa các nhánh mạng.