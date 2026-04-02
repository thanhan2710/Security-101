# Networking Essential

## 1. DHCP(Dynamic Host Configuration Protocol).

Khi chúng ta kết nối vào một mạng, chúng ta cần phải cấu hình:

1. Địa chỉ IP, subnet mark.
2. Router hoặc Gateway.
3. DNS server.

Vậy tại sao lại phải cấu hình những thứ này?&#x20;

* Như đã biết địa chỉ IP là địa chỉ định danh duy nhất mà mỗi thiết bị tham gia mạng đều phải có, subnet mark cho ta biết được địa chỉ mạng đó đang kết nối tới mạng nào và nó là ai ở trong mạng đó.
* Router hoặc Gateway giúp thiết bị định tuyến tới các nhà mạng cung cấp dịch vụ đó để  có thể truy cập vào các trình duyệt, ứng dụng,...
* DNS server là Domain Name System dùng để phân dải tên miền thành địa chỉ IP.

Đặc biệt với các thiết bị như điện thoại mobile, việc cấu hình thủ công địa chỉ IP hay phải quan tâm tới việc xử lí tên miền là một ý kiến không hề hay. Khi mà khả năng xảy ra xung đột địa chỉ IP, một địa chỉ IP xung đột sẽ bị cấm truy cập vào các tài nguyên trên mạng. Vì thế mà ta cần đến một giao thức để cấu hình tự động nó được gọi là Dynamic Host Configuration Protocol(DHCP) - là giao thức của tầng ứng dụng dựa vào UDP .

Khi ta mới đến một LAN segment khác, thiết bị của chúng ta sẽ được cấu hình để tự động gửi gói tin DHCP qua giao thức UDP tại cổng 68 đến DHCP Server nếu có, sau đó DHCP Server sẽ lắng nghe ở trên cổng UDP số 67.Quá trình này diễn ra như sau:

1. DHCP discover: client gửi gói tin DHCP Discover dưới dạng broatcast đi toàn mạng, lúc này địa chỉ IP của client là <kbd>0.0.0.0</kbd> .
2. DHCP Offer: DHCP Server gửi đi một gói tin DHCP Offer dưới dạng Unicast hoặc là Broadcast tùy vào cấu hình để gửi tới địa chỉ MAC của client các dải địa chỉ đang trống trong danh sách.
3. DHCP Request: Client nhận được gói tin DHCP Offer của Server và chọn lấy một cái sau đó gửi gói tin DHCP Request dưới dạng Broadcast để xác nhận với DHCP Server cũng như các DHCP Server khác trong mạng nếu có tồn tại rằng nó đã lấy địa chỉ IP này.
4. DHCP Acknowledge: DHCP Server trả lời lại với một gói Ack để xác nhận địa chỉ IP đó đã được giao cho client và cập nhật lại danh sách địa chỉ IP trống của mình.

Bản chất là DHCP Server cho Client đó mượn một địa chỉ IP còn trống trong danh sách để client đó có thể nhận được các dịnh vụ như:

* [x] Địa chỉ IP để truy cập mạng.
* [x] Gateway để định tuyến gói tin ra bên ngoài mạng.
* [x] Dịch vụ DNS để phân giải tên miền của các trang web mà Client truy cập.

