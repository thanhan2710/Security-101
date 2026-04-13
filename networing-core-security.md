# Networing Core Security

## 1.TLS( Transport Layer Security).

TLS Là một cung cấp bảo mật cho các giao thức ở tầng giao vận, giúp các gói tin dữ liệu được vận chuyển đảm bảo được tính đảm bảo và toàn vẹn khi truyền qua không gian mạng không bảo mật thay vì truyền dữ liệu đi dưới dạng cleartext. Phiên bản TLS phổ biến hiện nay là TLS version 1.3

Ngày nay có rất nhiều giao thức sử dụng cơ chế bảo vệ này như HTTPS,Dot(DNS Over TLS),SMTPS,... với 'S' đại diện cho cơ chế bảo mật SSL/TLS

Bước đầu tiên đối với một server hoặc client cần tự xác thực danh tính là phải có được một chứng chỉ TLS đã được kí. Thông thường thì quản trị viên máy chủ sẽ gửi đi một yêu cầu kí chứng chỉ(Certificate Sigining Request) tới cơ quan chứng thực(Certificate Authority), CA sẽ xác minh cái CSR đấy và cấp một chứng chỉ số(digital certificate).Sau khi có chữ kí số đó, client hoặc server có thể tự xác thực danh tính với các bên khác-Các bên mà có khả năng xác nhận tính hợp lệ của chữ kí số đó, tức là chứng chỉ của các cơ quan như CA phải được đặt ở trên máy chủ đó.Ví dụ:

<figure><img src=".gitbook/assets/5f04259cf9bf5b57aed2c476-1721903285393.png" alt=""><figcaption></figcaption></figure>

Nếu như CA không phát hiện chữ kí số trùng khớp trên máy chủ thì nó sẽ báo kết nối là không an toàn.

## 2.HTTPS(HTTP Over TLS).

Nếu như thông thường để bắt đầu một phiên HTTP là TCP handshake 3 bước tại cổng 80 sau đó truyền dữ liệu đi một cách thiếu thận trọng. Thì HTTPS sử dụng bắt tay 3 bước TCP cổng số 443 sau đó thực hiện một phiên TLS rồi mới đến bước truyền dữ liệu, như vậy dữ liệu truyền đi sẽ được đảm bảo hơn.

Một phiên HTTPS diễn ra như theo các bước cụ thể như sau:

1. Thiết lập kết nối TCP cổng số 443.
2. Thiết lập TLS
3. Gửi dữ liệu dưới dạng mã hóa.

<figure><img src=".gitbook/assets/5f04259cf9bf5b57aed2c476-1721903449717.png" alt=""><figcaption></figcaption></figure>

Dữ liệu mã hóa được gửi đi:

<figure><img src=".gitbook/assets/5f04259cf9bf5b57aed2c476-1721903354908.png" alt=""><figcaption></figcaption></figure>

Bằng một cách rất hiếm khi xảy ra, ta có được private key của phiên TLS đó, ta dùng chìa khóa đó để mã hóa cho một phiên TLS, dữ liệu ta thấy được sẽ được giải mã:

<figure><img src=".gitbook/assets/5f04259cf9bf5b57aed2c476-1721903477148.png" alt=""><figcaption></figcaption></figure>

