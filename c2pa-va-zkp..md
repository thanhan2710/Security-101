# C2PA và ZKP.

## I. C2PA( Colalition for Content Provenance and Authenticity ).

C2PA là một tiêu chuẩn về việc xác minh nguồn gốc và tính xác thực của nội dung số (video, hình ảnh, âm thanh), đặc tả kỹ thuật về siêu dữ liệu dành cho các phương tiện truyền thông kĩ thuật số  được phát triển bởi [Colalition for Content Provenance and Authenticity](#user-content-fn-1)[^1]

**Mục đích của C2PA :**

* [x] Trong bối cảnh AI tạo ra những hình ảnh nhân tạo ngày càng sắc nét và khó nhận biết nhằm mục đích tuyên truyền các thông tin sai lệch hoặc gây hại hoặc các thông tin không chính thống được truyền đi trên mạng xã hội nhằm vào các mục đích xấu thì chuẩn C2PA đã cung cấp giải pháp gắn vào tệp nội dung một hay nhiều lớp siêu dữ liệu được ký bằng mật mã học với mục đích làm rõ thời gian tạo ra nội dung đó, người tạo ra nó là ai ? thiết bị nào tạo ra nội dung này ?

Chuẩn C2PA cung cấp đầy đủ thông tin để người dùng có thể xác nhận được nguồn gốc, lịch sử và tính xác thực của nội dung số . Việc sử dụng chữ ký số bằng mật mã học khiến cho thông tin khó bị thay đổi mà không để lại dấu vết.

Khi một nền tảng hoặc phần mềm hỗ trợ tiêu chuẩn này, người dùng có thể truy cập vào dữ liệu xác thực để biết được nguồn gốc của nội dung và những lần nội dung bị chỉnh sửa trong quá khứ hay không.

**Qua đó ta thấy được tiêu chuẩn C2PA muốn nhắm đến việc :**&#x20;

* [x] Chống tin giả và deepfake.
* [x] Bảo vệ bản quyền nội dung số.
* [x] Tăng tính minh bạch của nội dung số.

**Một số ứng dụng của C2PA trong thực tế :**&#x20;

* Các thiết bị máy ảnh của Sony, Nikon hay Canon và một số thiết bị điện thoại di động như Google pixel 10, Samsung Galaxy S25 Series đã được tích hợp chuẩn C2PA khi chụp ảnh.
* Các phần mềm Adobe Photoshop, Lightroom cho phép xuất file kèm chứng chỉ nội dung theo đúng tiêu chuẩn C2PA.

## II. ZKP (Zero-knowledge Proofs).

1. **Khái niệm về ZKP.**

Zero-knowledge Proof là một công nghệ mật mã học dùng để xác thực thông tin mà không cần tiết lộ bất kì nội dung nào khác của thông tin đó. Cơ chế hoạt động của nó là một người chứng minh (prover) chứng minh một cái bằng chứng với bên xác nhận (Verifier) rằng bằng chứng đó là đúng mà không cần phải tiết lộ thêm bất cứ thông tin nào của bằng chứng đó.

Mục đích của ZKP là giữ nguyên tính bảo mật của đầu vào nhưng vẫn đảm bảo tính xác thực đúng đắn cho đầu ra.

2. **Cách thức họat động của ZKP.**

ZKP cho phép một người chứng minh rằng tôi biết một bí mật/ một thông tin đúng mà không cần tiết lộ chính thông tin hay bí mật đó.

Giống như khi bạn muốn chứng minh với server rằng bạn biết mật khẩu nhưng lại không muốn gửi mật khẩu đó cho server. ZKP sẽ cung cấp kiểu chứng minh như vậy.

3\.  **Ba tính chất quan trọng.**

* [x] Completeness : Nếu prover biết sự thật, họ có thể thuyết phục verifier.
* [x] Soundness : Nếu prover không biết mật khẩu, họ không thể lừa được người kiểm tra.
* [x] Zero-Knowledge : Verifier tin rằng bạn biết bí mật, nhưng không biết gì về bí mật đó.

4. **Các loại ZKP nổi bật**.

Interactive ZKP (ZKP tương tác): Prover và verifier phải kiểm tra hỏi đáp nhiều vòng.

Non-interactive ZKP (ZKP không tương tác): Prover và Verifier chỉ cần tạo và chứng minh 1 bằng chứng duy nhất, các công nghệ phổ biến của loại Non-interactive ZKP:&#x20;

1. Zk-SNARK :&#x20;
2. Zk-STARK:

## III. ZK-IMG: tested Images via Zero-Knowledge Proofs to Fight Disinformation.

Với việc deepfake và các thông tin giả mạo hiện nay đang trở nên phổ biến hơn do sự bành trướng của trí tuệ nhân tạo thì việc có một công nghệ mới nhằm chống lại điều đó là tất yếu. Các nghiên cứu đã đề xuất sử dụng ZK-SNARKs và camera được chứng thực để xác minh hình ảnh ngay khi chụp.     Mặc dù ZK-SNARK cho phép xác thực hình ảnh một cách không tương tác, tuy nhiên nghiên cứu này không bảo vệ quyền riêng tư và dữ liệu của đầu vào và bằng một cách nào đó nó chỉ hoạt động trên các hình ảnh 128 x 128.

Nhằm giải quyết vấn đề,ZK-IMG là một thư viện cho chứng thực sự biến đổi hình ảnh mà vẫn ẩn đi  được hình ảnh trước khi biến đổi. ZK-IMG là công nghệ đầu tiên có khả năng chứng thực sự biến đổi hình ảnh HD trên phần cứng thông dụng một cách an toàn và riêng tư.

* [x] Cơ chế hoạt động:&#x20;

1. Input là hình ảnh được chứng thực từ camera và các phép biến đổi đúng với đặc tả được công bố.
2. Tạo một bằng chứng ZK-SNARK cho các phép biến đổi hình ảnh và hình ảnh đầu ra.
3. Chứng thực với verifier bằng bằng chứng vừa tạo bằng ZK-SNARK.

ZK-IMG đã tận dụng hệ thống chứng minh ZK-SNARK đa dụng gần đây, cụ thể là **halo2.**

Tức là làm sao để các phép biến đổi ảnh thông thường trở thành các phép tính mà halo2 có thể chứng minh được một cách hiệu quả.

Để halo2 có thể hiểu được các phép biến đổi, ZK-IMG phải biến đổi nó thành các ràng buộc toán học maf halo2 hiểu được. Và phải triển khai bằng cách kết hợp và đóng gói các phép biến đổi lại để giảm dữ liệu trung gian giúp việc tính toán một cách hiệu quả hơn trong cấu trúc ZK-SNARK.

ZK-IMG còn cung cấp một phương pháp liên kết các phép biến đổi hình ảnh mà không tiết lộ đầu ra trung gian. ZK-IMG sẽ đóng gói càng nhiều phép biến đổi vào một bằng chứng duy nhất càng tốt. Để tránh tiết lộ thông tin, ZK-IMG băm các input và output và chỉ tiết lộ các giá trị băm như là một phần của bằng chứng và chỉ tiết lộ giá trị băm của đầu ra cuối cùng.

Bằng những cách thức đó, ZK-IMG có khả năng xác minh số lượng tùy ý các phép biến đổi trên hình ảnh HD bằng phần cứng thông dụng với thời gian ngắn và chi phí rẻ.







&#x20;





[^1]: Một tổ chức tiêu chuẩn do nhiều công ty công nghệ và tổ chức truyền thông thành lập. Trong đó có Adobe,google,Microsoft và Intel.
