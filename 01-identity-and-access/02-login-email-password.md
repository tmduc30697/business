# Login email/password

### Hệ thống quản lý khóa học trực tuyến cho giảng viên và học viên

Bài toán này yêu cầu phân biệt rõ ràng giữa hai đối tượng người dùng có quyền hạn khác nhau ngay từ bước đăng nhập. Bạn cần thiết kế làm sao để khi một tài khoản đăng nhập thành công, hệ thống biết được đó là giảng viên để hiển thị bảng điều khiển tạo khóa học, hoặc là học viên để hiển thị danh sách bài học đã mua. Ngoài ra, hệ thống cần lưu trữ lịch sử các thiết bị đã đăng nhập để người dùng có thể kiểm soát tài khoản của mình.

### Nền tảng thương mại điện tử với xác thực đa yếu tố

Trong mô hình này, việc chỉ sử dụng email và mật khẩu là chưa đủ an toàn cho các giao dịch tài chính. Sau khi người dùng nhập đúng mật khẩu, hệ thống sẽ yêu cầu một bước xác thực thứ hai qua mã OTP gửi về ứng dụng hoặc email. Bài toán yêu cầu bạn thiết kế quy trình trạng thái của token: từ lúc mới đăng nhập (chưa xác thực OTP) đến lúc hoàn toàn hợp lệ (đã xác thực OTP) để cho phép thanh toán.

### Hệ thống quản trị nội dung doanh nghiệp với phân quyền đa cấp

Thay vì chỉ có hai vai trò đơn giản, bài toán này tập trung vào việc quản lý quyền hạn chi tiết cho nhân viên trong một công ty. Một email đăng nhập có thể thuộc về phòng marketing (chỉ có quyền viết bài) hoặc phòng kỹ thuật (có quyền chỉnh sửa cấu hình). Bạn cần thiết kế hệ thống sao cho một người dùng có thể sở hữu nhiều vai trò và mỗi vai trò lại gắn liền với các quyền hạn cụ thể trên từng module của hệ thống.

### Ứng dụng mạng xã hội với tính năng thu hồi phiên đăng nhập từ xa

Người dùng thường đăng nhập tài khoản trên nhiều trình duyệt và điện thoại khác nhau. Bài toán đặt ra là làm thế nào để quản lý danh sách các session đang hoạt động. Khi người dùng đổi mật khẩu hoặc nhấn nút đăng xuất từ xa, hệ thống phải ngay lập tức vô hiệu hóa các token cũ trên tất cả các thiết bị khác. Điều này đòi hỏi thiết kế database phải lưu trữ thông tin về trình duyệt, địa chỉ IP và thời gian hết hạn của từng phiên làm việc.

### Dịch vụ phần mềm dạng thuê bao hỗ trợ nhiều tổ chức khách hàng

Đây là mô hình SaaS nơi một hệ thống phục vụ nhiều công ty khác nhau. Mỗi nhân viên sử dụng email công ty để đăng nhập vào không gian làm việc riêng biệt của công ty đó. Bài toán yêu cầu thiết kế database sao cho dữ liệu của công ty A hoàn toàn tách biệt với công ty B, dù họ có thể cùng sử dụng chung một giao diện đăng nhập. Việc xác thực phải gắn liền với mã định danh của tổ chức mà người dùng đó thuộc về.

### Hệ thống đặt lịch khám bệnh với quy trình khôi phục tài khoản phức tạp

Trong lĩnh vực y tế, tính bảo mật và khả năng phục hồi tài khoản rất quan trọng. Bài toán tập trung vào luồng quên mật khẩu: tạo ra các token tạm thời có thời hạn ngắn, gửi email xác nhận và đảm bảo người dùng không thể sử dụng lại mật khẩu cũ đã bị lộ. Bạn cần thiết kế các bảng lưu trữ lịch sử thay đổi mật khẩu và các yêu cầu khôi phục đang chờ xử lý để tránh bị tấn công spam email.

### Ví điện tử với tính năng khóa tài khoản tự động khi có nghi ngờ

Bài toán này chú trọng vào bảo mật chủ động. Hệ thống cần ghi lại mọi lần đăng nhập thất bại của một email. Nếu người dùng nhập sai mật khẩu quá 5 lần trong một khoảng thời gian ngắn, tài khoản sẽ bị khóa tạm thời. Bạn cần thiết kế cấu trúc dữ liệu để theo dõi số lần thử sai, thời điểm bị khóa và quy trình để người dùng có thể mở khóa tài khoản thông qua việc xác minh danh tính qua email.

### Hệ thống lưu trữ tệp tin đám mây với cơ chế Refresh Token

Để tăng trải nghiệm người dùng mà vẫn đảm bảo an toàn, hệ thống sử dụng cặp Access Token (thời gian sống ngắn) và Refresh Token (thời gian sống dài). Khi Access Token hết hạn, ứng dụng sẽ dùng Refresh Token để lấy mã mới mà không bắt người dùng nhập lại mật khẩu. Bài toán yêu cầu bạn thiết kế logic lưu trữ và kiểm tra tính hợp lệ của Refresh Token trong database để ngăn chặn việc đánh cắp token.
