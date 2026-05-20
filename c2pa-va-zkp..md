# C2PA và ZKP.

## I. C2PA( Colalition for Content Provenance and Authenticity ).

### 1.Tổng quan về C2PA.

C2PA là một tiêu chuẩn về việc xác minh nguồn gốc và tính xác thực của nội dung số (video, hình ảnh, âm thanh), đặc tả kỹ thuật về siêu dữ liệu dành cho các phương tiện truyền thông kĩ thuật số  được phát triển bởi [Colalition for Content Provenance and Authenticity](#user-content-fn-1)[^1].

Trong bối cảnh AI tạo ra những hình ảnh nhân tạo ngày càng sắc nét và khó nhận biết nhằm mục đích tuyên truyền các thông tin sai lệch hoặc gây hại hoặc các thông tin không chính thống được truyền đi trên mạng xã hội nhằm vào các mục đích xấu thì chuẩn C2PA đã cung cấp giải pháp gắn vào tệp nội dung một hay nhiều lớp siêu dữ liệu được ký bằng mật mã học với mục đích làm rõ thời gian tạo ra nội dung đó, người tạo ra nó là ai ? thiết bị nào tạo ra nội dung này ?

Chuẩn C2PA cung cấp đầy đủ thông tin để người dùng có thể xác nhận được nguồn gốc, lịch sử và tính xác thực của nội dung số . Việc sử dụng chữ ký số bằng mật mã học khiến cho thông tin khó bị thay đổi mà không để lại dấu vết.

Khi một nền tảng hoặc phần mềm hỗ trợ tiêu chuẩn này, người dùng có thể truy cập vào dữ liệu xác thực để biết được nguồn gốc của nội dung và những lần nội dung bị chỉnh sửa trong quá khứ hay không.

### 2. Tổng quan kỹ thuật

Về cấu trúc, C2PA gồm nhiều **assertion**, tức là các khẳng định riêng lẻ về tài sản số. Các assertion này có thể mô tả tác giả, bản quyền, thiết bị ghi hình, phần mềm xử lý, thao tác chỉnh sửa hoặc mối liên kết với nội dung gốc. Nhiều assertion được gom lại thành một **claim**, hay có thể hiểu là bản khai tổng hợp về tài sản số.

Để đảm bảo claim không bị giả mạo, C2PA sử dụng **chữ ký số**. Chữ ký số giúp xác minh rằng các thông tin trong claim không bị thay đổi sau khi được ký. Ngoài ra, C2PA có thể kết hợp thêm **Verifiable Credentials tức là các giấy chứng nhận điện tử** nhằm cung cấp các thông tin xác thực bổ sung, giúp tăng độ tin cậy cho nội dung.

Tất cả các thành phần như assertion, claim, chữ ký số và thông tin xác thực được liên kết với nhau tạo thành **C2PA Manifest**. Manifest này được tạo bởi một phần mềm hoặc thiết bị gọi là **Claim Generator**, ví dụ như máy ảnh, phần mềm chỉnh sửa ảnh hoặc công cụ `c2patool`.

<figure><img src=".gitbook/assets/Manifest.drawio.svg" alt=""><figcaption></figcaption></figure>

Tóm lại, C2PA không trực tiếp khẳng định nội dung là đúng hay sai, mà cung cấp một “hồ sơ nguồn gốc” giúp người dùng kiểm tra lịch sử tạo lập, chỉnh sửa và tính toàn vẹn của nội dung số. Đây là cơ sở quan trọng trong việc hỗ trợ chống tin giả và xác minh thông tin trên môi trường số.

### 3. Thiết lập lòng tin trong C2PA.

Trong C2PA, lòng tin được xây dựng dựa trên danh tính của chủ thể ký nội dung và khóa ký mật mã được sử dụng trong quá trình tạo Tệp kê khai C2PA. Chủ thể này có thể là cá nhân, tổ chức, thiết bị phần cứng đáng tin cậy hoặc phần mềm hỗ trợ C2PA. Khi một Manifest được tạo, các thông tin về nguồn gốc, hành động chỉnh sửa và liên kết với nội dung sẽ được ghi lại, sau đó được ký bằng chữ ký số để đảm bảo tính toàn vẹn.

C2PA không yêu cầu danh tính của chủ thể phải luôn được công khai. Danh tính có thể là tên thật, bút danh, ẩn danh hoặc thuộc về một thiết bị/dịch vụ đáng tin cậy. Ngoài ra, Manifest cũng có thể chứa thông tin xác thực như chứng chỉ mật mã để người kiểm tra biết chữ ký còn hợp lệ, đã hết hạn hay bị thu hồi hay chưa.

Ví dụ, khi người dùng chụp ảnh bằng máy ảnh hoặc điện thoại có hỗ trợ C2PA, thiết bị sẽ tạo một Manifest chứa các thông tin như thời gian chụp, thiết bị sử dụng, hình thu nhỏ và mã băm liên kết ảnh với Manifest. Các thông tin này được đưa vào Claim, sau đó Claim được ký số và nhúng vào tệp ảnh đầu ra, chẳng hạn như tệp JPEG.

Khi một công cụ kiểm tra như C2PA Validator đọc ảnh, nó sẽ trích xuất Manifest, kiểm tra chữ ký số, chứng chỉ liên quan và tính toàn vẹn của các assertion. Nhờ đó, người dùng có thể biết nội dung có nguồn gốc từ đâu, đã bị thay đổi hay chưa và có đủ cơ sở để tin cậy hay không.

C2PA thiết lập lòng tin không phải bằng cách khẳng định nội dung là đúng tuyệt đối, mà bằng cách cung cấp bằng chứng kỹ thuật về nguồn gốc, lịch sử xử lý, chữ ký số và thông tin xác thực của nội dung số.

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

## III. ZK-IMG: Attested Images via Zero-Knowledge Proofs to Fight Disinformation.

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
