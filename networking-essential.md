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

## 2.ARP(Address Resolution Control).

ARP là giao thức phân giải địa chỉ IP thành địa chỉ MAC, dựa theo chức năng của nó ta xét nó là giao thức của lớp Internet trong mô hình TCP/IP, nhưng cũng có thể nói nó là tầng Link trong TCP/IP vì nó làm việc với địa chỉ MAC. Tuy nhiên cần phải biết rằng ARP giúp phân giải địa chỉ lớp 3 thành địa chỉ lớp 2.

Các thiết bị không cần phải luôn luôn biết địa chỉ MAC của nhau, nó chỉ cần biết địa chỉ MAC của nhau khi chúng giao tiếp với nhau, quá trình như sau:

1. ARP Request: Khi máy A cần giao tiếp với một B, nó sẽ gửi gói tin Broadcast MAC ff:ff:ff:ff:ff:ff hỏi địa chỉ IP này của ai ? Kèm theo đó là địa chỉ MAC của nó.&#x20;
2. ARP Reply: Sau khi nhận được gói tin Broadcast, máy B ngay lập tức trả lời bằng cách gửi Unicast lại địa chỉ MAC của mình, xác nhận rằng địa chỉ IP đó là của nó.
3. ARP Cache: Máy A lưu cặp IP-MAC của máy B vào bộ nhớ của mình để không phải hỏi lại lần sau.

Các gói tin ARP Request và ARP Reply không được đóng gói trong một UDP hay một IP packet mà nó được gửi đi trực tiếp trong một Ethernet frame.

## 3.ICMP(Internet Control Message Protocol).

Giao thức này là giao thức dùng để chẩn đoán mạng và thông báo lỗi.

Có 2 câu lệnh khá phổ biến dựa vào ICMP và nó khá hay ho để khắc phục sự cố mạng và bảo mật mạng là:

* &#x20;`ping`  : Sử dụng ICMP để kiểm tra kết nối tới thiết bị mục tiêu và đo lường [Round-trip time](#user-content-fn-1)[^1]
* &#x20;[`traceroute`](#user-content-fn-2)[^2] : Sử dụng để khám phá các router đi qua trong quá trình định tuyến đến thiết bị mục tiêu.

Trong trường hợp ping lỗi, một là thiết bị mục tiêu đang offline hoặc là firewall đã chặn các gói cần thiết để ICMP hoạt động.

Khi ta sử dụng ping để kiểm tra thiết bị mục tiêu, để ý rằng có một tham số TTL được gọi là time-to-live[^3], nếu giá trị này giảm về 0 thì router sẽ hủy gói tin và thông báo lỗi ICMP Time Exceeded message.

Trường dữ liệu TTL đôi khi được lệnh traceroute yêu cầu phải chạm mức bằng 0 để gửi lại gói tin ICMP Time Exceeded về, từ đó biết được địa chỉ IP của router đầu tiên mà nó đi qua.

## 4.Các giải thuật định tuyến của Router.

## 5.NAT(Network Address Translation).









[^1]: Thời gian khi gói tin ICMP gửi đi cho tới khi quay lại

[^2]: Trong hệ điều hành tựa UNIX hay LINUX thì ta dùng traceroute còn Window thì là tracert

[^3]: 
