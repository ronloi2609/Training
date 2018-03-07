# Dựng website trên nền tảng LAMP server Ubuntu 16.04

## 1. Tạo database và User cho wordpress

### Bước 1: Đăng nhập vào MariaDB database
`mysql -u root -p`  

### Bước 2: Tạo Database và User
`CREATE DATABASE wordpress character set utf8 collate utf8_bin;`  

`GRANT ALL PRIVILEGES on wordpress.* to 'wpuser'@'localhost' identified by 'tuananh96';`  

`FLUSH PRIVILEGES; exit`  

Vậy là bạn đã có database và user để dùng cho wordpress:
Bạn có thể ghi chú lại như sau:  
Database: wordpress  
User: wpuser  
Pass: tuananh96  

## 2. Cài đặt Extension cho php 7 

### Bước 1: Cài đặt các extension cho php  
`sudo apt-get install php7.0-mysql php7.0-curl php7.0-json php7.0-cgi php7.0 libapache2-mod-php7.0 php7.0-mcrypt php7.0-xmlrpc php7.0-gd -y`  

### Bước 2: Download wordpress  

#### 2.1: Download source code  
Ở đây mình Download vào thư mục /tmp , còn các bạn có thể download và thư mục nào mà mình muốn.  

`cd /tmp  
curl -O https://wordpress.org/latest.tar.gz`  

#### 2.2: Giải nén và copy vào thư mục /var/www/html/wordpress  
`tar xzvf latest.tar.gz`  

**Đổi tên mặc định file config và xoá file config mặc định** 

`cp /tmp/wordpress/wp-config-sample.php /tmp/wordpress/wp-config.php && rm wp-config-sample.php`  

**copy vào thư mực /var/www/html/wordpress**

`sudo cp -a /tmp/wordpress/. /var/www/html/wordpress/`  

## 3. Cấu hình thư mục chứa source wordpress  
Để hạn chế sự dòm ngó của hacker cũng như tăng sự bảo mật cho website chúng ta cần cấu hình báo mật thự mục chứa source code wordpress  

### Bước 1: Cấu hình bảo mật thư mục /var/www/html/wordpress/  

`sudo chown -R www-data:www-data /var/www/html/wordpress/ sudo chmod -R 755 /var/www/html/wordpress/`   

## 4. Cấu hình file config wp-config.php trong /html/wordpress/  

`sudo vi wp-config.php`  

** Chỉnh sửa các phần màu đỏ được gạch chân :**  

![](https://nguyenhuuhoang.com/wp-content/uploads/2016/09/huong-dan-cai-dat-wordpress-tren-lamp-ubuntu-16.04-hinh-2-nguyenhuuhoang.com-min.jpg)  
**save và thoát**  
**restart lại các dịch vụ**  
`sudo systemctl restart mysql && systemctl restart apache2`  

## 5. Hoàn thành việc cài đặt wordpress

### Bước 1 : cấu hình các thông số cần thiết cho website

Đăng nhập vào trình duyệt với 
**http://ip-address/wordpress** hoặc **http://localhost/wordpress**  

![](https://nguyenhuuhoang.com/wp-content/uploads/2016/09/huong-dan-cai-dat-wordpress-tren-lamp-ubuntu-16.04-hinh-4-nguyenhuuhoang.com_.jpg)  

**Điền đầy đủ thông tin liên quan đến website của bạn**  

ví dụ:  
 
![](https://nguyenhuuhoang.com/wp-content/uploads/2016/09/huong-dan-cai-dat-wordpress-tren-lamp-ubuntu-16.04-hinh-5-nguyenhuuhoang.com_.jpg)  

![](https://nguyenhuuhoang.com/wp-content/uploads/2016/09/huong-dan-cai-dat-wordpress-tren-lamp-ubuntu-16.04-hinh-6-nguyenhuuhoang.com_.jpg)  

![](https://nguyenhuuhoang.com/wp-content/uploads/2016/09/huong-dan-cai-dat-wordpress-tren-lamp-ubuntu-16.04-hinh-7-nguyenhuuhoang.com_.jpg)  

![](https://nguyenhuuhoang.com/wp-content/uploads/2016/09/huong-dan-cai-dat-wordpress-tren-lamp-ubuntu-16.04-hinh-8-nguyenhuuhoang.com_.jpg)  



    