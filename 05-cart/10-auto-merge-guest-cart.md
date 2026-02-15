# Auto merge guest cart

### Xử lý trùng lặp sản phẩm và cập nhật số lượng

Khi khách hàng thêm 2 sản phẩm A vào giỏ hàng ẩn danh, nhưng trong giỏ hàng đã lưu của tài khoản cũng đang có 3 sản phẩm A. Hệ thống cần xác định xem sẽ cộng dồn số lượng thành 5 hay ghi đè theo dữ liệu mới nhất từ giỏ hàng khách. Ngoài ra, cần kiểm tra xem tổng số lượng sau khi gộp có vượt quá giới hạn tồn kho của sản phẩm đó trong kho hàng hay không trước khi thực hiện cập nhật vào cơ sở dữ liệu.

### Đồng bộ trạng thái giá và chương trình khuyến mãi theo thời gian thực

Khách hàng có thể đã thêm sản phẩm vào giỏ hàng ẩn danh từ ba ngày trước với mức giá cũ. Khi họ đăng nhập, hệ thống cần thực hiện logic hợp nhất nhưng phải đồng thời kiểm tra lại bảng giá hiện hành và các mã giảm giá đang áp dụng cho tài khoản đó. Bài toán đặt ra là làm sao để hiển thị rõ ràng sự thay đổi giá cho người dùng sau khi hợp nhất và đảm bảo các ràng buộc về giá trị tối thiểu của đơn hàng để hưởng ưu đãi vẫn chính xác.

### Quản lý thuộc tính sản phẩm phức tạp trong quá trình gộp

Đối với các sản phẩm có nhiều biến thể như kích cỡ, màu sắc hoặc các tùy chọn cá nhân hóa (khắc tên, chọn quà tặng kèm), việc hợp nhất không chỉ dựa vào mã sản phẩm chính. Hệ thống cần so sánh chi tiết từng cặp thuộc tính của sản phẩm trong giỏ hàng khách và giỏ hàng tài khoản. Nếu cùng một đôi giày nhưng khác kích cỡ, chúng phải được giữ thành hai dòng riêng biệt, nếu trùng hoàn toàn mọi thuộc tính thì mới được phép cộng dồn số lượng.

### Giới hạn quy mô giỏ hàng sau khi hợp nhất

Mỗi hệ thống thường có một giới hạn tối đa cho số lượng đầu mục sản phẩm trong giỏ hàng để đảm bảo hiệu năng truy vấn và xử lý thanh toán. Khi thực hiện hợp nhất, tổng số lượng sản phẩm từ hai nguồn có thể vượt quá con số này. Bạn cần thiết kế cơ chế ưu tiên, ví dụ như giữ lại những sản phẩm mới thêm vào gần đây nhất hoặc những sản phẩm có giá trị cao nhất, và đưa ra thông báo phù hợp để người dùng điều chỉnh lại giỏ hàng.

### Xử lý xung đột giỏ hàng trên đa thiết bị

Người dùng có thể đang mở website trên cả máy tính (với tư cách khách) và điện thoại (đã đăng nhập tài khoản). Khi họ đăng nhập trên máy tính, hệ thống phải đối mặt với ba trạng thái giỏ hàng: giỏ hàng hiện tại trên máy tính, giỏ hàng đang lưu trên server của tài khoản, và có thể là một giỏ hàng khách khác trên điện thoại. Bài toán này đòi hỏi thiết kế hệ thống có khả năng xử lý bất đồng bộ và đảm bảo tính nhất quán dữ liệu cuối cùng trên tất cả các thiết bị.

### Ràng buộc về phân vùng kho hàng và địa lý

Trong các hệ thống lớn có nhiều kho hàng theo khu vực, giỏ hàng của khách thường dựa trên vị trí địa lý tạm thời (IP). Tuy nhiên, khi đăng nhập, địa chỉ mặc định của tài khoản có thể thuộc một khu vực kho khác. Quá trình hợp nhất lúc này phải kiểm tra xem các sản phẩm trong giỏ hàng khách có khả dụng tại kho hàng của khu vực người dùng đã đăng ký hay không. Nếu sản phẩm không hỗ trợ giao tới địa chỉ của tài khoản, hệ thống phải tách chúng ra hoặc loại bỏ khỏi giỏ hàng chính thức.

### Lưu vết và phục hồi trạng thái giỏ hàng trước khi hợp nhất

Đôi khi việc tự động hợp nhất khiến khách hàng bối rối vì họ không nhớ mình đã thêm gì trước đó hoặc muốn quay lại trạng thái giỏ hàng cũ. Bài toán thực tế là thiết kế một cơ chế lưu trữ tạm thời (staging) hoặc nhật ký thay đổi cho giỏ hàng. Điều này cho phép hệ thống cung cấp tính năng hoàn tác (undo) hoặc gửi email thông báo về các sản phẩm đã được tự động gộp vào tài khoản để người dùng dễ dàng kiểm soát.

### Hiệu suất ghi dữ liệu khi số lượng người dùng đăng nhập đồng loạt

Vào các mùa khuyến mãi lớn, hàng triệu người dùng thực hiện đăng nhập và hợp nhất giỏ hàng cùng lúc. Việc truy vấn giỏ hàng khách từ bộ nhớ đệm (Redis/Session) rồi ghi đè liên tục vào cơ sở dữ liệu quan hệ (SQL) có thể gây ra nghẽn cổ chai hoặc khóa bảng dữ liệu. Bạn cần thiết kế giải pháp xử lý hàng đợi hoặc chiến lược cập nhật từng phần để đảm bảo phản hồi của API đăng nhập vẫn nhanh chóng trong khi việc hợp nhất dữ liệu giỏ hàng diễn ra một cách an toàn ở phía sau.
