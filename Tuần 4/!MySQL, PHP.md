# MySQL, PHP

## Cài đặt PHP

Để cài đặt PHP và các module PHP cho Apache trên Ubuntu, hãy gõ lệnh sau:  
`sudo apt-get install php5 libapache2-mod-php5 php5-mcrypt`  

- Thiết lập cấu hình để nó ưu tiên index file index.php thay vì index.html bằng cách sửa file **/etc/apache2/mods-enabled/dir.conf** thành dưới đây (thêm index.php):

<IfModule mod_dir.c>
          DirectoryIndex index.php index.html index.cgi index.pl index.php index.xhtml index.htm
</IfModule>

- Sau đó khởi động lại apache
- Kiểm tra cách tạo file **info.php** trong thư mục với nội dung như sau: `<?php phpinfo(); ?>`




## Cài đặt MySQL
Trên Ubuntu sử dụng lệnh : `apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql`    


## Một số lệnh Transact-SQL (T-SQL) căn bản  
Trong cơ sở dữ liệu SQL, để tương tác với dữ liệu hay đối tượng cơ sở dữ liệu bạn cần sử dụng các đoạn lệnh được cung cấp bằng hệ quản trị cơ sở dữ liệu (CSDL). Trong bài viết này mình sẽ nói đến các lệnh T-SQL trong SQL Server. Cũng tương tự nhưng ở các hệ quản trị CSDL khác, thì nó cũng được chia thành 2 loại là loại ngôn ngữ thao tác với dữ liệu (DML – Data manipulation language), thường được các lập trình viên sử dụng và loại ngôn ngữ định nghĩa dữ liệu, tương tác với đối tượng trong CSDL (DDL – data definition language) thường được các nhà quản trị csdl (DBA) sử dụng.  

## 1. Các nhóm lệnh thao tác dữ liệu -DML

![](https://tuandc.com/wp-content/uploads/2017/06/DML-SQL.png)
Đây là nhóm lệnh phổ biến được dùng nhiều trong các phần mềm để thao tác đến các dữ liệu. Nhóm này bao gồm 4 lệnh cơ bản sau:  

### Lệnh SELECT trong SQL Server 

- Lệnh được sử dụng để truy xuất các tập kết quả của các cột hay các hàng trong CSDL.
 Cú pháp: `SELECT tên_cột FROM Tên_bảng.`
- Trong lệnh select bạn có thể tạo ra các trường tính toán hoặc nối các bảng dữ liệu lại với nhau để truy vấn. ví dụ mình có 2 bảng sinh_vien và diem mình sẽ nối như sau:  
 `SELECT * FROM sinh_vien join diem ON sinh_vien.id = diem.id_sinhvien`.
- Trong SELECT còn có 2 phép Join là **Inner join** (chỉ hiển thị các dòng có các trường bằng nhau) và **outer join** (hiển thị cả những dòng không có trường bằng nhau).  
- Trong phần tên_cột bạn có thể thêm AS để đặt trên cho cột đó ví dụ:   `SELECT (toan+ly) AS diemtoanly FROM sinh_vien join diem ON sinh_vien.id = diem.id_sinhvien.`  

### Lệnh INSERT trong SQL Server 

- Để thêm dữ liệu vào CSDL bạn cần một câu lệnh để làm việc này và đó là lệnh INSERT.
- Cú pháp: `INSERT INTO Tên_bảng (tên_các_trường) VALUES (giá_trị_thêm)`.
- Trong lệnh này nếu muốn thêm vào dữ liệu có hỗ trợ chữ tiếng việt có đấu bạn phải thêm chữ N phía trước. Ví dụ:  
 `INSERT INTO sinh_vien (ten_sinh_vien, tuoi) VALUES (N"Tuấn",18).`

### Lệnh UPDATE trong SQL Server  

- Để cập nhật, thay đổi dữ liệu cần sử dụng một câu lệnh có tên UPDATE.
- Cú pháp: `UPDATE Tên_bảng SET tên_trường = giá_trị WHERE điều kiện.`
- Với lệnh này bạn thường phải đưa ra điều kiện để xác định, thông thường là trường ID, ví dụ:  
 `UPDATE sinh_vien SET ten = N"Tuấn ĐC" WHERE id=1.`

### Lệnh DELETE trong SQL Server

 - Mặc dù lệnh DELETE rất ít được sử dụng trong các vấn đề yêu cầu sự toàn vẹn và không để mất mát dữ liệu, nhưng lệnh này cũng được đưa ra như một vấn đề tất yếu.
- Cú pháp: `DELETE FROM tên_bảng WHERE điều_kiện.`
- Trong lệnh này bạn không cần đưa vào trường nhưng bạn cần đưa vào điều kiện để xóa. Nếu không có điều kiện dữ liệu trong bảng có thể bị xóa hết.  

### Tạo Procedure trong SQL Server

- Procedure là thủ tục được lưu trữ sẵn trong csdl. Nó được sử dụng để hạng chế phần mềm truy vấn thẳng để các bảng hay trường của csdl, thay vào đó chỉ cần truyền đến các thông số hoặc gửi yêu cầu.
- Cú pháp: `CREATE PROCEDURE tên_thủ_tục @Tham_số [kiểu_dữ_liệu] AS Lệnh_DML.`
- Cú pháp thực thi: `EXEC tên_thủ_tục 'Tham số'.`
- ví dụ: `CREATE PROCEDURE lay_du_lieu_sv @so_luong int AS SELECT TOP @so_luong FROM sinh_vien.`

----

## 2. Các nhóm lệnh định nghĩa dữ liệu – DDL
![](https://tuandc.com/wp-content/uploads/2017/06/DDL-SQL.png)
Các nhóm lệnh này rất ít được sử dụng bởi các phần mềm, tuy nhiên chúng là những lệnh rất quan trọng có thể làm thay đổi csdl ở mức lớn nhất. Nhóm lệnh này thường chỉ được sử dụng bởi các Database Admin (DBA).  

### Lệnh CREATE DATABASE trong SQL Server

- Trong một hệ quản trị csdl có chứa rất nhiều csdl. các hệ hỗ trợ những đoạn lệnh khác nhau để tạo ra một database. Trong SQL Server cũng có câu lệnh để làm việc này.
- Cú pháp: `CREATE DATABASE tên_csdl;`

### Lệnh CREATE TABLE trong SQL Server

- Chúng ta đã biết trong một database sẽ có nhiều bảng (table), để tạo ra các bảng ta có câu lệnh để tạo bảng.
- Cú pháp: `CREATE TABLE tên_bảng (tên_cột_1 [kiểu_dữ_liệu],  tên_cột_2 [kiểu_dữ_liệu],....);`

### Lệnh ALTER TABLE trong SQL Server

- SQL hỗ trợ các lệnh thay đổi bảng sau khi đã tạo như thêm (ADD) các trường (cột), Xóa (DROP) các trường, Sửa (ALTER) các trường.
- Cú pháp thêm cột vào bảng: `ALTER TABLE Tên_bảng ADD Tên_cột [kiểu_dữ_liệu];`
- Cú pháp xóa một cột trong bảng: `ALTER TABLE Tên_bảng DROP COLUMN Tên_cột;`
- Cú pháp sửa một cột trong bảng: `ALTER TABLE Tên_bảng ALTER COLUMN Tên_cột [kiểu_dữ_liệu];`

### Lệnh DROP DATABASE trong SQL Server

- Bạn có thể sử dụng lệnh DROP để xóa đi một database trong SQL. Tuy nhiên đây là lệnh hạn chế sử dụng nhất.
- Cú pháp: `DROP DATABASE Tên_bảng;`

### Lệnh DROP TABLE trong SQL Server

- Mặc dù không khuyến khích nhưng nó vẫn thường xuyên được sử dụng để loại bỏ đi các bảng thừa. Mặc dù có thể dùng Management studio (SSMS) để thực hiện việc này nhanh hơn nhưng với lệnh bạn có thể thao tác nhanh hơn.
- Cú pháp: `DROP TABLE Tên_bảng;`

---



## MysQL Replication.
- MySQL replication cho phép dữ liệu từ 1 MySQL database server (đóng vai trò master) được đọc và ghi dữ liệu sau đó cập nhập những dữ liệu đã thay đổi sang 1 hoặc nhiều MySQL database server khách( đóng vai trò slaves chỉ có quyền đọc dữ liệu).
- Với cơ sở dữ liệu, nhu cầu lưu trữ lớn, đòi hỏi cơ sở dữ liệu toàn vẹn, không bị mất mát trước những sự cố ngoài dự đoán là rất cao. Vì vậy, người ta nghĩ ra khái niệm “nhân bản”, tạo một phiên bản cơ sở dữ liệu giống hệt cơ sở dữ liệu đang tồn tại, và lưu trữ ở một nơi khác, đề phòng có sự cố.  
- Phiên bản cơ sở dữ liệu phục vụ ứng dụng được lưu trữ trên server master. Phiên bản cơ sở dữ liệu “nhân bản” được lưu trữ trên server slave. Quá trình nhân bản từ master sang slave gọi là replication.  
- Khi có một thay đổi trên cơ sở dữ liệu master, master sẽ ghi xuống log file (log ở dạng binary). Slave đọc log file, thực hiện những thao tác trong log file. Việc ghi, đọc log theo dạng binary được thực hiện rất nhanh.

### 1. Mô hình MySQL replication gồm có 2 thành phần: 
- MySQL master
- MySQL slave

### 2. Cách thức hoạt động  
- Tại thời điểm hoạt động bình thường mọi request sẽ được đưa đến vào MySQL master. Khi MySQL master gặp sự cố, request sẽ được đẩy qua cho MySQL slave xử lí. Khi MySQL master up lại bình thường, request sẽ được trả về cho MySQL master.  
- Quá trình chuyển đổi vai trò giữa MySQL master và MySQL slave sẽ được giới thiệu ở bài hướng dẫn sau. Bài hướng dẫn đầu tiên chỉ nêu các bước để cấu hình MySQL master và MySQL slave replicate cho nhau.  

### 3. Các bước cấu hình
**a.** Giả sử máy tính MySQL master có hostname là `master.mydomain.com.` Máy tính MySQL slave có hostname là `slave.mydomain.com.` 

**b.** Cài đặt mysql bằng các gói `rpm` trên MySQL master và MySQL slave.  

**c.** Start mysql trên MySQL master và MySQL slave.  

**d. Cấu hình master**  :

- Tạo user cho phép MySQL slave được quyền REPLICATE  
`mysql> GRANT REPLICATION SLAVE ON *.* TO 'repl'@'%.mydomain.com' IDENTIFIED BY 'slavepass';`  

- Sửa trong file /etc/my.cnf những option sau:  

    [mysqld]
    log-bin=mysql-bin
    server-id=1
    innodb_flush_log_at_trx_commit=1
    sync_binlog=1   

- Start mysql trên MySQL master  

**e. Cấu hình Slave**  
- Sửa trong file /etc/my.cnf option sau:  
`server-id=2`  
-  Start mysql trên MySQL slave.
- Để replication, cần xem tình trạng ghi log hiện tại của MySQL master, để điều khiển slave bắt đầu replicate như thế nào.  
- Ngưng mọi tác động trên cơ sở dữ liệu MySQL master  
`mysql> FLUSH TABLES WITH READ LOCK;`  

- Xem tình trạng của MySQL master:  

    mysql > SHOW MASTER STATUS;
    | File | Position | Binlog_Do_DB | Binlog_Ignore_DB |
    | mysql-bin.003 | 73 | test | manual,mysql |

- Cấu hình những thông tin cần thiết, để slave giao tiếp được với master:  

    mysql> CHANGE MASTER TO
    MASTER_HOST='master.mydomain.com',
    MASTER_USER='repl',
    MASTER_PASSWORD='slavepass',
    MASTER_LOG_FILE='recorded_log_file_name',
    MASTER_LOG_POS=recorded_log_position;   

Ghi chú: giá trị MASTER_LOG_FILE ở đây là file name [mysql-bin.003] và MASTER_LOG_POS là giá trị [Position] của câu lệnh SHOW MASTER STATUS;  

 - Nếu trước khi thực hiện replication, master không ghi thành log file, thì giá trị tương ứng ở đây là: chuỗi rỗng (“”) và 4.  
 -  Giải phóng các table trên master:  
 `mysql> UNLOCK TABLES;`   

 - Hoàn tất quá trình cấu hình , test thử  

 **f. Master đã có dữ liệu:**  

 - Giả sử trước khi thực hiện mô hình replication, master đã có dữ liệu. Vậy ta cần migrate dữ liệu qua slave trước, trước khi thực hiện các bước replication như ở trên.  

- Trên master, ngưng những tác động làm thay đổi cơ sở dữ liệu, dump database:   

`mysql> FLUSH TABLES WITH READ LOCK;`   
`shell> mysqldump --all-databases --master-data > dbdump.db`  

- Import cơ sở dữ liệu này vào MySQL slave.
- Tương tự phần trên, nếu trước khi thực hiện replication, MySQL master có ghi log, cần xem tình trạng log tại thời điểm đó, để cấu hình cho MySQL slave bắt đầu replication tại điểm nào.
- Cấu hình những thông tin cần thiết, để slave giao tiếp được với master:  

    mysql> CHANGE MASTER TO
    MASTER_HOST='master.mydomain.com',
    MASTER_USER='repl',
    MASTER_PASSWORD='slavepass',
    MASTER_LOG_FILE='recorded_log_file_name',
    MASTER_LOG_POS=recorded_log_position;

- Giải phóng các table trên master, start mysql trên MySQL slave  
`mysql> UNLOCK TABLES;`  
- Hoàn tất quá trình cấu hình, test thử.