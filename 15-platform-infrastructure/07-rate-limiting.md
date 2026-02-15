# Rate limiting

### Giới hạn số lượt gửi mã OTP xác thực qua số điện thoại

Để tránh việc bị kẻ xấu lợi dụng gửi tin nhắn rác liên tục gây tốn kém chi phí viễn thông cho doanh nghiệp, hệ thống cần áp dụng quy tắc nghiêm ngặt cho tính năng gửi OTP. Cụ thể, một số điện thoại chỉ được phép yêu cầu gửi tối đa 3 mã xác thực trong vòng 5 phút. Nếu vượt quá số lượng này, người dùng phải đợi ít nhất 30 phút mới có thể thực hiện lại thao tác. Bài toán này yêu cầu bạn thiết kế cách lưu trữ mốc thời gian và bộ đếm cho từng thực thể định danh là số điện thoại.

### Chống tấn công dò mật khẩu tại giao diện đăng nhập

Hệ thống cần ngăn chặn các cuộc tấn công Brute Force bằng cách giới hạn số lần đăng nhập sai trên một tài khoản hoặc từ một địa chỉ IP. Nếu một địa chỉ IP thực hiện quá 10 lần đăng nhập thất bại trong vòng 1 phút, hệ thống sẽ tạm khóa quyền truy cập của IP đó vào trang đăng nhập trong 15 phút. Việc thiết kế cần đảm bảo hệ thống phân biệt được giữa việc người dùng quên mật khẩu bình thường và một cuộc tấn công có quy mô lớn từ nhiều nguồn khác nhau.

### Quản lý hạn ngạch sử dụng cho các gói dịch vụ API trả phí

Một nền tảng cung cấp dữ liệu thời tiết chia khách hàng thành các gói: Miễn phí, Tiêu chuẩn và Cao cấp. Gói Miễn phí chỉ được gọi 100 request mỗi giờ, trong khi gói Cao cấp được phép gọi 10.000 request mỗi giờ. Hệ thống Gateway cần một cơ chế kiểm tra nhanh chóng thông tin gói cước của người dùng dựa trên API Key và trừ dần hạn mức tương ứng trong một chu kỳ thời gian cố định. Đây là bài toán điển hình về việc kết hợp giữa dữ liệu cấu hình người dùng và dữ liệu đếm thời gian thực.

### Ngăn chặn hành vi thu thập dữ liệu tự động trên trang chi tiết sản phẩm

Các đối thủ thường sử dụng robot hoặc công cụ tự động để quét giá và thông tin sản phẩm trên website thương mại điện tử. Để hạn chế việc này, hệ thống áp dụng giới hạn cho các yêu cầu truy cập vào trang chi tiết sản phẩm dựa trên User Agent và địa chỉ IP. Nếu một nguồn truy cập có tần suất quá 60 lượt xem trang mỗi phút, hệ thống sẽ yêu cầu người dùng phải giải mã CAPTCHA hoặc tạm dừng phản hồi. Bài toán này đòi hỏi thiết kế hệ thống lưu trữ có khả năng ghi nhận và truy vấn dữ liệu truy cập cực nhanh.

### Giới hạn tần suất đăng bài và bình luận trên mạng xã hội

Để giữ cho môi trường cộng đồng không bị ngập trong các nội dung spam, một tài khoản mạng xã hội mới tạo sẽ bị giới hạn chỉ được đăng tối đa 5 bài viết và 20 bình luận trong vòng 1 giờ đầu tiên. Hệ thống cần theo dõi loại hành động và vai trò của người dùng để áp dụng các ngưỡng giới hạn khác nhau. Việc thiết kế database cần hỗ trợ phân loại hành động của người dùng để áp dụng các chính sách Rate Limit tương ứng một cách linh hoạt.

### Điều tiết lưu lượng cho tính năng tìm kiếm toàn trang

Tính năng tìm kiếm thường tiêu tốn nhiều tài nguyên CPU và RAM của hệ thống database. Để bảo vệ dịch vụ không bị treo, hệ thống giới hạn mỗi phiên làm việc của người dùng chỉ được thực hiện tối đa 10 lượt tìm kiếm trong 1 phút. Nếu người dùng thực hiện các từ khóa tìm kiếm thay đổi quá nhanh liên tục, hệ thống sẽ trả về lỗi yêu cầu người dùng thao tác chậm lại. Bài toán này tập trung vào việc quản lý trạng thái phiên làm việc và tài nguyên xử lý phía backend.

### Giới hạn lượt tải tài liệu cho tài khoản khách

Trên một trang web chia sẻ tài liệu, người dùng không đăng nhập vẫn được phép tải xuống nhưng bị giới hạn nghiêm ngặt để khuyến khích họ tạo tài khoản. Cụ thể, mỗi địa chỉ IP chỉ được tải tối đa 2 tài liệu mỗi ngày. Hệ thống cần một bảng lưu trữ lịch sử tải xuống dựa trên IP và định danh thiết bị, đồng thời có cơ chế tự động dọn dẹp dữ liệu cũ hàng ngày để tránh bảng dữ liệu phình to quá mức theo thời gian.

### Bảo vệ API tạo đơn hàng trong các chiến dịch khuyến mãi

Trong các đợt mở bán giới hạn, lượng người dùng đổ vào tạo đơn hàng cùng lúc có thể gây nghẽn hệ thống thanh toán. Hệ thống cần áp dụng cơ chế hàng đợi và Rate Limiting để chỉ cho phép tối đa 500 yêu cầu tạo đơn hàng được xử lý mỗi giây trên toàn bộ hệ thống. Những yêu cầu vượt quá ngưỡng này sẽ được đưa vào hàng đợi chờ hoặc phản hồi bận. Đây là bài toán về thiết kế hệ thống phân tán và khả năng chịu tải của các API mang tính giao dịch cao.
