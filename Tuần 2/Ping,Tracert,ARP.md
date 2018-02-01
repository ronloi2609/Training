# Lệnh Ping

## Ý nghĩa: Làm việc trên giao thức ICMP (Internet control message Protocol) dùng để kiểm tra tình trạng kết nối mạng giữa 2 host.

## Cách hoạt động : Khi lệnh Ping được thực thi
 + Host A gửi gói tin **ICMP echo request** cho Host B.
 + Khi Host B nhận được gói tin **ICMP echo request** nó sẽ gửi lại gói tin **ICPM echo reply** (với điều kiện Host B không bị firewall chặn gói ICMP)
 + Host A nhận được gói tin **ICMP echo reply** của host B thì quá trình kết nối được xác nhận.

 Markdown Live Preview

# Mục lục
>
## 1. Lệnh Ping
## 2. Lệnh Tracerouter
## 3. Lệnh ARP

----
# 1. Lệnh Ping
## Ý nghĩa của lệnh Ping:


> Làm việc trên giao thức ICMP (Internet control message Protocol) dùng để kiểm tra tình trạng kết nối mạng giữa 2 host.  
Ping còn được dùng để đo đường thời gian trễ của gói tin trong mạng

----
## Cách hoạt động :

![Ping](https://i.imgur.com/kZrUWw9.png)
+ Host A gửi gói tin **ICMP echo request** cho Host B.

+ Khi Host B nhận được gói tin **ICMP echo request** nó sẽ gửi lại gói tin **ICPM echo reply** (với điều kiện Host B không bị firewall chặn gói ICMP)
+ Host A nhận được gói tin **ICMP echo reply** của host B thì quá trình kết nối được xác nhận.

## Cú pháp lệnh Ping:
 - `Ping <Destination Address>  <tham số>(nếu có)`:

 - **Trong đó**:
  + **Destination**: có thể là **IP**, **Netbios name** (KT02) hay **Domain name** (google.com)

- Các tham số của lệnh ping :

![Ping](https://i.imgur.com/oAjBrgd.png)

----

## Demo ping đến Google.com
![Ping](https://i.imgur.com/omKQZbY.png)
- **bytes = 32**: kích thước mặc định của gói tin khi gởi là 32 bytes.
- **Time**: độ trễ.  
- **TTL**(time to live): nếu destination address là hệ điều hành Linux, Unix thì TTL lớn nhất là 64, còn hệ điều hành (HĐH) window TTL lớn nhất là 128. Mỗi lần gói tin qua 1 router (hops) thì TTL sẽ bị trừ đi 1. Bằng lệnh ping ta còn đoán để biết thêm HOST đó đang chạy HĐH gì, qua bao nhiêu router. Trong trường hợp trên ta biết server google được chạy HĐH Unix hoặc Linux và qua khoảng 9 router
----

## Dùng ping để tấn công từ chối dịch vụ (DOS)
### Ping of Death:

-  là kỹ thuật tấn công làm quá tải hệ thống mạng bằng cách gửi các gói tin ICMP có kích thước vượt quá 65.536 byte đến mục tiêu.
- Do kích thước này lớn hơn kích thước cho phép của các gói tin IP nên nó sẽ được chia nhỏ ra rồi gửi từng phần đến máy đích.
- Khi đến mục tiêu, nó sẽ được ráp lại thành gói tin hoàn chỉnh, do có kích thước quá mức cho phép, nó sẽ gây ra tràn bộ nhớ đệm và bị treo. 

----

# 2. Lệnh Tracerouter
## Ý nghĩa của lện Tracerouter:
> Tracert là công cụ kiểm tra đường đi của gói dữ liệu, xem nó đi qua các trạm nào, mất bao lâu, trạm nào bị nghẽn, không kết nối được không? trạm đó bị nghẽn thì có con đường nào khác để đến đích hay không? Thực tế càng qua nhiều trạm thì càng chậm và càng có rủi ro bị time out (mất kết nối).

----

## Cách hoạt động :
- Tracerouter hoạt động bằng cách gửi một chuỗi các gói tin bằng giao thức **ICMP** tới máy chủ đích(web).
- Các gói tin này chứa 1 giá trị **TTL** (time to live), giá trị TTL được sắp xếp theo thứ tự tăng dần , gói tin thứ nhất chứa gtri TTL là 1, gói thứ 2 là 2,...
- Khi gói tin đến được 1 router, giá trị của nó giảm đi 1, cho đến khi TTL bằng 0, router sẽ gửi 1 thông báo hết hạn cho máy tính.
----

## Cú pháp lệnh Tracert:

 `tracert <domain>` với windowns.  
 `tracerouter <domain>` với UNIX/Linux.

- **Trong đó:** <domain> là tên miền bạn kiểm tra.
- VD: **tracert google.com**

----

## Demo lệnh Tracert
![Ping](https://i.imgur.com/twOz0sR.png)

----

## Cách đọc
`1 Hop RTT1 RTT2 RTT3 Ten_mien [Dia_chỉ_IP]`
  
- **Hop**: khi 1 gói tin đi qua 1 router nào đó gọi là Hop.  
- **RTT1,RTT2,RTT3**: viết tắt của *Roud Trip Time*, là khoảng thời gian mà gói tin đi tới router và phản hồi về cho máy tính của bạn. Nếu cột *RTT* mà có dấu * thì có nghĩa là router đó không phản hồi lại.  
- **Tên_miền[Dia_chi_IP]**: Nếu như router đó có tên miền tiên thì tên miền này sẽ được hiển thị, thông qua tên miền của router, biết được vị trí của router ở mạng trên. Nếu router không có tên miền thì sẽ hiển thị **địa chỉ IP** của router.  

----

# 3. Lệnh ARP

## Ý nghĩa : 
> Hiển thị và thay đổi bảng chuyển địa chỉ IP - địa chỉ MAC sử dụng bởi giao thức ARP.
  
----

## Cách hoạt động:

- Hoạt động trên môi trường mạng giữa máy A thuộc mạng A và máy B thuộc mạng B phải truyền qua Router C có port X. Máy A sẽ biết được địa chỉ IP của Router C và biết được rằng để truyền gói tin tới B phải đi qua C. Thông tin như vậy sẽ được chứa trong một bảng gọi là bảng định tuyến.
- Quá trình truyền dữ liệu :
  - Máy A gửi một ARP request (broadcast) để tìm địa chỉ MAC của port X.

  - Router C trả lời, cung cấp cho máy A địa chỉ MAC của port X.

  - Máy A truyền gói tin đến port X của Router.

  -  Router nhận được gói tin từ máy A, chuyển gói tin ra port Y của Router. Trong gói tin có chứa địa chỉ IP của máy B. Router sẽ gửi ARP request để tìm địa chỉ MAC của máy B.

  - Máy B sẽ trả lời cho Router biết địa chỉ MAC của mình. Sau khi nhận được địa chỉ MAC của máy B, Router C gửi gói tin của A đến B.
- Ngoài bảng định tuyến người ta có thể sử dụng phương pháp **proxyARP**.

----

## Cú pháp lệnh ARP:

`ARP` Xem hướng dẫn lệnh arp. 
  
`ARP -a[inter_addr]` : Hiển thị giá trị tại bảng ARP (chuyển địa chỉ IP- địa chỉ MAC) của giao thức ARP trong máy tính. Nếu có địa chỉ **inet_addr** thì chỉ có máy có địa chỉ tương ứng thể hiện. 
 
`ARP -s inet_addr eth_addr` : Thêm 1 IP vào bảng ARP với địa chỉ IP **inet_addr** và địa chỉ MAC **eth_addr**. 
 
`ARP -d inet_addr`: Xóa địa chỉ IP **inet_addr**

----

## Demo lệnh ARP

![Ping](https://i.imgur.com/SBPBaoJ.png)

----
## Một số phương pháp tấn công ARP
### ARP poisoning

- ARP poisoning là một phương pháp tấn công hệ thống ARP, đầu độc hệ thống ARP làm cho thông tin của ARP table còn chính xác.
- ARP có một điểm yếu là không có cơ chế xác thực. Như đã biết để xây dựng ARP table, máy tính sẽ gửi các ARP request, sau đó nhận lại các ARP reply. Hệ thống hoàn toàn không có cơ chế xác minh xem thông tin của ARP reply đó là thật hay giả, thông tin này sẽ được lưu lại vào ARP table để sử dụng.
- Lợi dụng điểm yếu này người tấn công sẽ thực hiện đầu độc hệ thống ARP, sau đó tấn công hệ thống mạng theo một số phương pháp như: **man in the middle**, **denial of services**, **MAC flooding**…v.v.



 
Mục lục
1. Lệnh Ping
2. Lệnh Tracerouter
3. Lệnh ARP
1. Lệnh Ping
Ý nghĩa của lệnh Ping:
Làm việc trên giao thức ICMP (Internet control message Protocol) dùng để kiểm tra tình trạng kết nối mạng giữa 2 host.
Ping còn được dùng để đo đường thời gian trễ của gói tin trong mạng

Cách hoạt động :
Ping + Host A gửi gói tin ICMP echo request cho Host B.

Khi Host B nhận được gói tin ICMP echo request nó sẽ gửi lại gói tin ICPM echo reply (với điều kiện Host B không bị firewall chặn gói ICMP)
Host A nhận được gói tin ICMP echo reply của host B thì quá trình kết nối được xác nhận.
Cú pháp lệnh Ping:
Ping <Destination Address> <tham số>(nếu có):

Trong đó:

Destination: có thể là IP, Netbios name (KT02) hay Domain name (google.com)

Các tham số của lệnh ping :

Ping

Demo ping đến Google.com
Ping - bytes = 32: kích thước mặc định của gói tin khi gởi là 32 bytes. - Time: độ trễ.
- TTL(time to live): nếu destination address là hệ điều hành Linux, Unix thì TTL lớn nhất là 64, còn hệ điều hành (HĐH) window TTL lớn nhất là 128. Mỗi lần gói tin qua 1 router (hops) thì TTL sẽ bị trừ đi 1. Bằng lệnh ping ta còn đoán để biết thêm HOST đó đang chạy HĐH gì, qua bao nhiêu router. Trong trường hợp trên ta biết server google được chạy HĐH Unix hoặc Linux và qua khoảng 9 router

Dùng ping để tấn công từ chối dịch vụ (DOS)
Ping of Death:

là kỹ thuật tấn công làm quá tải hệ thống mạng bằng cách gửi các gói tin ICMP có kích thước vượt quá 65.536 byte đến mục tiêu.
Do kích thước này lớn hơn kích thước cho phép của các gói tin IP nên nó sẽ được chia nhỏ ra rồi gửi từng phần đến máy đích.
Khi đến mục tiêu, nó sẽ được ráp lại thành gói tin hoàn chỉnh, do có kích thước quá mức cho phép, nó sẽ gây ra tràn bộ nhớ đệm và bị treo.
2. Lệnh Tracerouter
Ý nghĩa của lện Tracerouter:
Tracert là công cụ kiểm tra đường đi của gói dữ liệu, xem nó đi qua các trạm nào, mất bao lâu, trạm nào bị nghẽn, không kết nối được không? trạm đó bị nghẽn thì có con đường nào khác để đến đích hay không? Thực tế càng qua nhiều trạm thì càng chậm và càng có rủi ro bị time out (mất kết nối).

Cách hoạt động :
Tracerouter hoạt động bằng cách gửi một chuỗi các gói tin bằng giao thức ICMP tới máy chủ đích(web).
Các gói tin này chứa 1 giá trị TTL (time to live), giá trị TTL được sắp xếp theo thứ tự tăng dần , gói tin thứ nhất chứa gtri TTL là 1, gói thứ 2 là 2,...
Khi gói tin đến được 1 router, giá trị của nó giảm đi 1, cho đến khi TTL bằng 0, router sẽ gửi 1 thông báo hết hạn cho máy tính.
Cú pháp lệnh Tracert:
tracert <domain> với windowns.
tracerouter <domain> với UNIX/Linux.

Trong đó: <domain> là tên miền bạn kiểm tra.
VD: tracert google.com
Demo lệnh Tracert
Ping

Cách đọc
1 Hop RTT1 RTT2 RTT3 Ten_mien [Dia_chỉ_IP]

Hop: khi 1 gói tin đi qua 1 router nào đó gọi là Hop.
RTT1,RTT2,RTT3: viết tắt của Roud Trip Time, là khoảng thời gian mà gói tin đi tới router và phản hồi về cho máy tính của bạn. Nếu cột RTT mà có dấu * thì có nghĩa là router đó không phản hồi lại.
Tên_miền[DiachiIP]: Nếu như router đó có tên miền tiên thì tên miền này sẽ được hiển thị, thông qua tên miền của router, biết được vị trí của router ở mạng trên. Nếu router không có tên miền thì sẽ hiển thị địa chỉ IP của router.
3. Lệnh ARP
Ý nghĩa :
Hiển thị và thay đổi bảng chuyển địa chỉ IP - địa chỉ MAC sử dụng bởi giao thức ARP.

Cách hoạt động:
Hoạt động trên môi trường mạng giữa máy A thuộc mạng A và máy B thuộc mạng B phải truyền qua Router C có port X. Máy A sẽ biết được địa chỉ IP của Router C và biết được rằng để truyền gói tin tới B phải đi qua C. Thông tin như vậy sẽ được chứa trong một bảng gọi là bảng định tuyến.
Quá trình truyền dữ liệu :

Máy A gửi một ARP request (broadcast) để tìm địa chỉ MAC của port X.

Router C trả lời, cung cấp cho máy A địa chỉ MAC của port X.

Máy A truyền gói tin đến port X của Router.

Router nhận được gói tin từ máy A, chuyển gói tin ra port Y của Router. Trong gói tin có chứa địa chỉ IP của máy B. Router sẽ gửi ARP request để tìm địa chỉ MAC của máy B.

Máy B sẽ trả lời cho Router biết địa chỉ MAC của mình. Sau khi nhận được địa chỉ MAC của máy B, Router C gửi gói tin của A đến B.

Ngoài bảng định tuyến người ta có thể sử dụng phương pháp proxyARP.
Cú pháp lệnh ARP:
ARP Xem hướng dẫn lệnh arp.

ARP -a[inter_addr] : Hiển thị giá trị tại bảng ARP (chuyển địa chỉ IP- địa chỉ MAC) của giao thức ARP trong máy tính. Nếu có địa chỉ inet_addr thì chỉ có máy có địa chỉ tương ứng thể hiện.

ARP -s inet_addr eth_addr : Thêm 1 IP vào bảng ARP với địa chỉ IP inet_addr và địa chỉ MAC eth_addr.

ARP -d inet_addr: Xóa địa chỉ IP inet_addr

Demo lệnh ARP
Ping

Một số phương pháp tấn công ARP
ARP poisoning

ARP poisoning là một phương pháp tấn công hệ thống ARP, đầu độc hệ thống ARP làm cho thông tin của ARP table còn chính xác.
ARP có một điểm yếu là không có cơ chế xác thực. Như đã biết để xây dựng ARP table, máy tính sẽ gửi các ARP request, sau đó nhận lại các ARP reply. Hệ thống hoàn toàn không có cơ chế xác minh xem thông tin của ARP reply đó là thật hay giả, thông tin này sẽ được lưu lại vào ARP table để sử dụng.
Lợi dụng điểm yếu này người tấn công sẽ thực hiện đầu độc hệ thống ARP, sau đó tấn công hệ thống mạng theo một số phương pháp như: man in the middle, denial of services, MAC flooding…v.v.
     
Copyright 2015 tanabe.

# Mục lục
>
## 1. Lệnh Ping
## 2. Lệnh Tracerouter
## 3. Lệnh ARP

----
# 1. Lệnh Ping
## Ý nghĩa của lệnh Ping:


> Làm việc trên giao thức ICMP (Internet control message Protocol) dùng để kiểm tra tình trạng kết nối mạng giữa 2 host.  
Ping còn được dùng để đo đường thời gian trễ của gói tin trong mạng

----
## Cách hoạt động :

![Ping](https://i.imgur.com/kZrUWw9.png)
+ Host A gửi gói tin **ICMP echo request** cho Host B.

+ Khi Host B nhận được gói tin **ICMP echo request** nó sẽ gửi lại gói tin **ICPM echo reply** (với điều kiện Host B không bị firewall chặn gói ICMP)
+ Host A nhận được gói tin **ICMP echo reply** của host B thì quá trình kết nối được xác nhận.

## Cú pháp lệnh Ping:
 - `Ping <Destination Address>  <tham số>(nếu có)`:

 - **Trong đó**:
  + **Destination**: có thể là **IP**, **Netbios name** (KT02) hay **Domain name** (google.com)

- Các tham số của lệnh ping :

![Ping](https://i.imgur.com/oAjBrgd.png)

----

## Demo ping đến Google.com
![Ping](https://i.imgur.com/omKQZbY.png)
- **bytes = 32**: kích thước mặc định của gói tin khi gởi là 32 bytes.
- **Time**: độ trễ.  
- **TTL**(time to live): nếu destination address là hệ điều hành Linux, Unix thì TTL lớn nhất là 64, còn hệ điều hành (HĐH) window TTL lớn nhất là 128. Mỗi lần gói tin qua 1 router (hops) thì TTL sẽ bị trừ đi 1. Bằng lệnh ping ta còn đoán để biết thêm HOST đó đang chạy HĐH gì, qua bao nhiêu router. Trong trường hợp trên ta biết server google được chạy HĐH Unix hoặc Linux và qua khoảng 9 router
----

## Dùng ping để tấn công từ chối dịch vụ (DOS)
### Ping of Death:

-  là kỹ thuật tấn công làm quá tải hệ thống mạng bằng cách gửi các gói tin ICMP có kích thước vượt quá 65.536 byte đến mục tiêu.
- Do kích thước này lớn hơn kích thước cho phép của các gói tin IP nên nó sẽ được chia nhỏ ra rồi gửi từng phần đến máy đích.
- Khi đến mục tiêu, nó sẽ được ráp lại thành gói tin hoàn chỉnh, do có kích thước quá mức cho phép, nó sẽ gây ra tràn bộ nhớ đệm và bị treo. 

----

# 2. Lệnh Tracerouter
## Ý nghĩa của lện Tracerouter:
> Tracert là công cụ kiểm tra đường đi của gói dữ liệu, xem nó đi qua các trạm nào, mất bao lâu, trạm nào bị nghẽn, không kết nối được không? trạm đó bị nghẽn thì có con đường nào khác để đến đích hay không? Thực tế càng qua nhiều trạm thì càng chậm và càng có rủi ro bị time out (mất kết nối).

----

## Cách hoạt động :
- Tracerouter hoạt động bằng cách gửi một chuỗi các gói tin bằng giao thức **ICMP** tới máy chủ đích(web).
- Các gói tin này chứa 1 giá trị **TTL** (time to live), giá trị TTL được sắp xếp theo thứ tự tăng dần , gói tin thứ nhất chứa gtri TTL là 1, gói thứ 2 là 2,...
- Khi gói tin đến được 1 router, giá trị của nó giảm đi 1, cho đến khi TTL bằng 0, router sẽ gửi 1 thông báo hết hạn cho máy tính.
----

## Cú pháp lệnh Tracert:

 `tracert <domain>` với windowns.  
 `tracerouter <domain>` với UNIX/Linux.

- **Trong đó:** <domain> là tên miền bạn kiểm tra.
- VD: **tracert google.com**

----

## Demo lệnh Tracert
![Ping](https://i.imgur.com/twOz0sR.png)

----

## Cách đọc
`1 Hop RTT1 RTT2 RTT3 Ten_mien [Dia_chỉ_IP]`
  
- **Hop**: khi 1 gói tin đi qua 1 router nào đó gọi là Hop.  
- **RTT1,RTT2,RTT3**: viết tắt của *Roud Trip Time*, là khoảng thời gian mà gói tin đi tới router và phản hồi về cho máy tính của bạn. Nếu cột *RTT* mà có dấu * thì có nghĩa là router đó không phản hồi lại.  
- **Tên_miền[Dia_chi_IP]**: Nếu như router đó có tên miền tiên thì tên miền này sẽ được hiển thị, thông qua tên miền của router, biết được vị trí của router ở mạng trên. Nếu router không có tên miền thì sẽ hiển thị **địa chỉ IP** của router.  

----

# 3. Lệnh ARP

## Ý nghĩa : 
> Hiển thị và thay đổi bảng chuyển địa chỉ IP - địa chỉ MAC sử dụng bởi giao thức ARP.
  
----

## Cách hoạt động:

- Hoạt động trên môi trường mạng giữa máy A thuộc mạng A và máy B thuộc mạng B phải truyền qua Router C có port X. Máy A sẽ biết được địa chỉ IP của Router C và biết được rằng để truyền gói tin tới B phải đi qua C. Thông tin như vậy sẽ được chứa trong một bảng gọi là bảng định tuyến.
- Quá trình truyền dữ liệu :
  - Máy A gửi một ARP request (broadcast) để tìm địa chỉ MAC của port X.

  - Router C trả lời, cung cấp cho máy A địa chỉ MAC của port X.

  - Máy A truyền gói tin đến port X của Router.

  -  Router nhận được gói tin từ máy A, chuyển gói tin ra port Y của Router. Trong gói tin có chứa địa chỉ IP của máy B. Router sẽ gửi ARP request để tìm địa chỉ MAC của máy B.

  - Máy B sẽ trả lời cho Router biết địa chỉ MAC của mình. Sau khi nhận được địa chỉ MAC của máy B, Router C gửi gói tin của A đến B.
- Ngoài bảng định tuyến người ta có thể sử dụng phương pháp **proxyARP**.

----

## Cú pháp lệnh ARP:

`ARP` Xem hướng dẫn lệnh arp. 
  
`ARP -a[inter_addr]` : Hiển thị giá trị tại bảng ARP (chuyển địa chỉ IP- địa chỉ MAC) của giao thức ARP trong máy tính. Nếu có địa chỉ **inet_addr** thì chỉ có máy có địa chỉ tương ứng thể hiện. 
 
`ARP -s inet_addr eth_addr` : Thêm 1 IP vào bảng ARP với địa chỉ IP **inet_addr** và địa chỉ MAC **eth_addr**. 
 
`ARP -d inet_addr`: Xóa địa chỉ IP **inet_addr**

----

## Demo lệnh ARP

![Ping](https://i.imgur.com/SBPBaoJ.png)

----
## Một số phương pháp tấn công ARP
### ARP poisoning

- ARP poisoning là một phương pháp tấn công hệ thống ARP, đầu độc hệ thống ARP làm cho thông tin của ARP table còn chính xác.
- ARP có một điểm yếu là không có cơ chế xác thực. Như đã biết để xây dựng ARP table, máy tính sẽ gửi các ARP request, sau đó nhận lại các ARP reply. Hệ thống hoàn toàn không có cơ chế xác minh xem thông tin của ARP reply đó là thật hay giả, thông tin này sẽ được lưu lại vào ARP table để sử dụng.
- Lợi dụng điểm yếu này người tấn công sẽ thực hiện đầu độc hệ thống ARP, sau đó tấn công hệ thống mạng theo một số phương pháp như: **man in the middle**, **denial of services**, **MAC flooding**…v.v.




  
