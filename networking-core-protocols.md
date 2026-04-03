# Networking Core Protocols

## 1.Dịch vụ phân giải tên miền DNS(Domain Name System).

DNS hoạt động tại tầng tứng dụng, nó chịu trách nghiệm phân giải tên miền thành địa chỉ IP, có các bản ghi của DNS như:

* [x] Bản ghi A: Có chức năng là phân giải tên miền thành một địa chỉ IPv4.
* [x] Bản ghi AAAA: Cũng là phân giải tên miền nhưng nó dành cho địa chỉ IPv6.
* [x] Bản ghi CNAME: Ánh xạ một tên miền này sang tên miền khác.
* [x] Bản ghi MX(Mail Exchange): Chỉ định một máy chủ thư điện tử xử lí email cho một tên miền.

Tức là khi bạn truy cập một trình duyệt chẳng hạn như <kbd>www.example.com</kbd> , nó sẽ truy vấn đến DNS Server và sử dụng bản ghi A để phân giải tên miền kia thành một địa chỉ IPv4 cái mà bạn dùng để truy cập. Hoặc chẳng hạn như bạn muốn gửi một tin nhắn đến email test@example.com, nó sẽ truy vấn tới DNS Server và sử dụng bản ghi MX để xử lí các email.

Bằng lệnh <kbd>nslookup</kbd>  bạn có thể tra cứu địa chỉ IP của một tên miền. Chẳng hạn như bạn muốn tra cứu địa chỉ IP của miền <kbd>www.google.com</kbd>&#x20;

<figure><img src=".gitbook/assets/2026-04-03_11-09.png" alt=""><figcaption></figcaption></figure>

Bạn có thể thấy <kbd>::1</kbd>  ở phần Server và Address thực chất là địa chỉ router của bạn, còn số hiệu cổng 53 là số hiệu cổng mặc định của DNS sử dụng UDP, trong một vài trường hợp nó cũng sử dụng cổng 53 TCP như một giải pháp thay thế.

Còn các dòng bên dưới là dải địa chỉ IP của google với bản ghi A cho địa chỉ IPv4 và bản ghi AAAA cho địa chỉ IPv6.

## 2.Các bản ghi WHOIS.

WHOIS là nơi lưu trữ thông tin của người đăng kí tên miền đó, bao gồm các thông tin như tên, số điện thoại, email và địa chỉ.Người đăng kí tên miền cũng có thể tùy chọn cài đặt riêng tư các thông tin cá nhân khi đăng kí tên miền.

Để xem thông tin của người đăng kí tên miền, ta có thể tra cứu trên dịch vụ trực tuyến có sẵn hoặc sử dụng dòng lệnh <kbd>whois</kbd> , hãy thử chúng với <kbd>google.com</kbd>  và cơ bản thứ xuất hiện là như này:

<figure><img src=".gitbook/assets/2026-04-03_11-29.png" alt=""><figcaption></figcaption></figure>

## 3.HTTP và HTTPS: Giao thức truy cập web và giao thức truy cập web bảo mật.

HTTP và HTTPS là giao thức được sử dụng ở tầng ứng dụng, với HTTP lắng nghe ở cổng TCP số 80 hoặc ít phổ biến hơn là cổng TCP 8080 và HTTPS lắng nghe ở cổng TCP số 443 hoặc là cổng TCP số 8443.

Khi ta sử dụng HTTP hay HTTPS tức là web browser của chúng ta sẽ gửi các dòng lệnh lên cho server chịu trách nghiệm quản lí trang web đó, một số các lệnh thường dùng như:

* <kbd>GET</kbd> : Truy xuất dữ liệu từ web server, chẳng hạn như mở một file HTMLpost hoặc là một hình ảnh.
* <kbd>POST</kbd> : Dùng để gửi dữ liệu lên máy chủ, chẳng hạn như điền vào một form và đẩy lên hoặc là tải lên server một file.
* <kbd>PUT</kbd> : Tạo một tài nguyên mới trên web server hoặc ghi đè lên một tài nguyên có sẵn trên web server.
* <kbd>DELETE</kbd> : Dùng để xóa các tài nguyên cụ thể trên web server.

Hãy quan tâm đến cách mà web browser thao tác với web server bằng các command, có thể là như sau:

<figure><img src=".gitbook/assets/5f04259cf9bf5b57aed2c476-1719849586345.png" alt=""><figcaption><p><strong>Với phần màu đỏ là của web browser gửi đi còn phần màu xanh là của web server trả lời.</strong></p></figcaption></figure>

Hoặc đơn giản hơn với telnet:

<figure><img src=".gitbook/assets/2026-04-03_11-59.png" alt=""><figcaption></figcaption></figure>

Với hình ảnh ở trên, ta đang truy cập đến web server có địa chỉ là <kbd>10.48.138.101</kbd> tại cổng 80. Các tham số là <kbd>GET /flag.thml HTTP/1.1</kbd>  tức là lấy file có tên flag.html bằng giao thức HTTP bản 1.1 và <kbd>Host: anything</kbd>  tức là truy cập đến server có tên anything vì ở đây chỉ là ví dụ. Trên thực tế giá trị ở phần Host ta nhập vào sẽ là địa chỉ IP của web server hoặc tên trang chính xác của nó.

## 4. FTP(File Tranfer Protocol).

Trong khi HTTP hay HTTPS được dùng để truy xuất đến một trang web thì FTP dùng để trao đổi file. FTP rất hiệu quả cho việc trao đổi file. FPT Server lắng nghe trên cổng TCP số 21, việc truyền dữ liệu được thực hiện thông qua một kết nối khác từ client đến server chỉ khi việc trao đổi file diễn ra.

Một số command thường được sử dụng:

<kbd>USER</kbd> : Người dùng nhập vào tài khoản.

<kbd>PASS</kbd> : Người dùng nhập vào mật khẩu.

<kbd>RETR</kbd> : Truy xuất đến một file trên FTP Server để tải xuống.

<kbd>STOR</kbd> : Đẩy file từ client lên FTP Server.

<figure><img src=".gitbook/assets/2026-04-03_14-47.png" alt=""><figcaption><p><strong>Phần màu đỏ là Client còn phần màu xanh là FTP Server trả lời.</strong></p></figcaption></figure>

Cơ bản thì quá trình diễn ra như trên.

