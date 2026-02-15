# Forgot password

### Hệ thống gửi mã xác thực qua email và thời hạn hiệu lực của token

Bài toán này tập trung vào quy trình cơ bản nhất khi người dùng nhập địa chỉ email vào form quên mật khẩu. Hệ thống cần tạo ra một chuỗi ký tự ngẫu nhiên gọi là reset token và lưu trữ vào cơ sở dữ liệu kèm theo thời gian hết hạn cụ thể. Khi người dùng click vào đường dẫn trong email, hệ thống phải so khớp token này và kiểm tra xem nó còn trong thời gian cho phép hay đã quá hạn. Bạn cần thiết kế bảng lưu trữ token sao cho có thể quản lý trạng thái của chúng và tự động vô hiệu hóa các token cũ khi một yêu cầu mới được tạo ra.

### Giới hạn tần suất yêu cầu để chống tấn công spam và brute force

Trong thực tế, một người dùng hoặc kẻ tấn công có thể liên tục nhấn nút gửi yêu cầu để làm tràn ngập hộp thư đến hoặc làm tiêu tốn tài nguyên máy chủ gửi mail. Bài toán đặt ra yêu cầu thiết kế một cơ chế giới hạn số lần yêu cầu reset mật khẩu trong một khoảng thời gian nhất định, ví dụ như tối đa ba lần mỗi giờ. Bạn sẽ cần cân nhắc việc lưu trữ lịch sử các lần yêu cầu, địa chỉ IP của người dùng và trạng thái khóa tạm thời để bảo vệ hệ thống khỏi các hành vi lạm dụng nhưng vẫn đảm bảo trải nghiệm cho người dùng thật.

### Xác thực đa yếu tố và lựa chọn phương thức nhận mã reset

Thay vì chỉ gửi qua email, các hệ thống hiện đại cho phép người dùng chọn nhận mã xác thực qua tin nhắn điện thoại hoặc ứng dụng xác thực. Bài toán yêu cầu thiết kế cơ sở dữ liệu có khả năng lưu trữ nhiều phương thức liên lạc cho một tài khoản và ghi nhận lựa chọn của người dùng tại thời điểm quên mật khẩu. Hệ thống phải quản lý được các loại mã khác nhau như đường dẫn dài chứa token hoặc mã số OTP ngắn sáu chữ số, đồng thời đảm bảo tính bảo mật cho từng kênh truyền tin.

### Quản lý phiên đăng xuất tập trung sau khi đổi mật khẩu thành công

Khi người dùng đã đặt lại mật khẩu thành công, một vấn đề quan trọng là phải đảm bảo tất cả các thiết bị khác đang đăng nhập bằng mật khẩu cũ phải bị đăng xuất ngay lập tức. Bài toán này đòi hỏi bạn thiết kế hệ thống quản lý session hoặc sử dụng token thu hồi để vô hiệu hóa toàn bộ các phiên làm việc cũ. Bạn cần tư duy về cách liên kết giữa ID người dùng và danh sách các token đang hoạt động trong bộ nhớ đệm hoặc cơ sở dữ liệu để thực hiện thao tác đăng xuất đồng loạt trên mọi nền tảng.

### Ngăn chặn sử dụng lại mật khẩu cũ trong lịch sử

Để tăng cường bảo mật, nhiều doanh nghiệp yêu cầu người dùng không được phép đặt lại mật khẩu giống với những mật khẩu họ đã sử dụng trong vòng sáu tháng qua. Bài toán này yêu cầu bạn thiết kế một bảng lưu trữ lịch sử mật khẩu đã được mã hóa kèm theo mốc thời gian. Khi người dùng nhập mật khẩu mới ở bước reset, hệ thống phải thực hiện so sánh mật khẩu mới với danh sách các mật khẩu cũ trong quá khứ trước khi cho phép cập nhật chính thức vào bảng người dùng chính.

### Quy trình xác thực danh tính qua câu hỏi bảo mật dự phòng

Trong trường hợp người dùng mất quyền truy cập vào cả email lẫn số điện thoại, hệ thống có thể sử dụng các câu hỏi bảo mật đã thiết lập từ trước. Bài toán yêu cầu thiết kế danh mục các câu hỏi mẫu và lưu trữ câu trả lời đã được băm của người dùng. Bạn cần xây dựng logic API sao cho người dùng phải trả lời đúng một số lượng câu hỏi nhất định trước khi được chuyển đến trang đặt lại mật khẩu, đồng thời đảm bảo các câu trả lời này không bị lộ dưới dạng văn bản thuần trong cơ sở dữ liệu.

### Theo dõi và ghi nhật ký hoạt động để kiểm toán bảo mật

Mọi hành động liên quan đến thay đổi thông tin nhạy cảm như mật khẩu đều cần được ghi lại để phục vụ việc tra soát sau này. Bài toán đặt ra yêu cầu thiết kế hệ thống logging chi tiết bao gồm thời gian yêu cầu, thiết bị thực hiện, địa chỉ mạng, trạng thái thành công hay thất bại và nguyên nhân lỗi nếu có. Dữ liệu này cần được tổ chức sao cho quản trị viên có thể dễ dàng truy vấn khi có báo cáo về việc tài khoản bị xâm nhập trái phép thông qua tính năng quên mật khẩu.

### Xử lý tranh chấp khi có nhiều yêu cầu reset đồng thời

Đôi khi hệ thống gặp tình trạng người dùng nhấn gửi yêu cầu liên tục do mạng chậm hoặc do có kẻ gian đang cố gắng chiếm quyền tài khoản cùng lúc với chủ sở hữu. Bài toán yêu cầu bạn thiết kế logic xử lý tranh chấp, đảm bảo rằng chỉ có token mới nhất được sinh ra là có hiệu lực và các token trước đó sẽ bị hủy ngay lập tức. Việc này giúp tránh tình trạng người dùng click nhầm vào các link cũ trong email dẫn đến thông báo lỗi không rõ ràng hoặc tạo ra các lỗ hổng logic trong quá trình xác thực.
