# Email campaign

### Gửi chiến dịch Email Marketing hàng loạt theo phân khúc khách hàng

Một quản trị viên muốn gửi một thông điệp quảng bá sản phẩm mới đến 500.000 khách hàng cùng một lúc. Hệ thống cần cho phép tạo chiến dịch, soạn thảo nội dung email và lựa chọn danh sách người nhận dựa trên các tiêu chí như độ tuổi, giới hạn địa lý hoặc lịch sử mua hàng. Bài toán này yêu cầu thiết kế cấu trúc dữ liệu để lưu trữ thông tin chiến dịch, danh sách khách hàng mục tiêu và trạng thái gửi của từng email trong một tệp dữ liệu khổng lồ.

### Kịch bản tự động gửi email nhắc nhở giỏ hàng bị bỏ quên

Khi khách hàng thêm sản phẩm vào giỏ hàng nhưng không tiến hành thanh toán sau một khoảng thời gian nhất định, ví dụ là 2 giờ đồng hồ, hệ thống sẽ tự động gửi một email nhắc nhở kèm theo danh sách các sản phẩm đang chờ. Nếu khách hàng vẫn chưa quay lại sau 24 giờ, hệ thống tiếp tục gửi một email thứ hai kèm mã giảm giá để kích thích mua hàng. Hệ thống cần theo dõi trạng thái giỏ hàng và thời gian tương tác cuối cùng của người dùng để kích hoạt các bước trong kịch bản một cách chính xác.

### Quản lý danh sách từ chối nhận email và hủy đăng ký

Để tuân thủ các quy định về quyền riêng tư và tránh bị đánh dấu là thư rác, hệ thống phải cung cấp một đường dẫn hủy đăng ký trong mỗi email gửi đi. Khi người dùng nhấn vào đường dẫn này, hệ thống cần cập nhật trạng thái của họ vào danh sách đen hoặc danh sách từ chối nhận tin cho một chiến dịch cụ thể hoặc toàn bộ hệ thống. Các lần gửi email tiếp theo phải thực hiện đối soát với danh sách này để đảm bảo không gửi nhầm cho những người đã yêu cầu dừng nhận tin.

### Theo dõi hiệu quả chiến dịch thông qua tỷ lệ mở và nhấn link

Sau khi gửi email, doanh nghiệp cần biết có bao nhiêu người đã thực sự mở email và bao nhiêu người đã nhấn vào các đường dẫn bên trong nội dung. Hệ thống cần ghi lại các sự kiện tương tác của người dùng kèm theo thông tin về thời gian, loại thiết bị và vị trí địa lý. Điều này đòi hỏi thiết kế database cho phép lưu trữ hàng triệu bản ghi sự kiện một cách tối ưu để có thể truy vấn báo cáo tổng hợp theo thời gian thực cho từng chiến dịch cụ thể.

### Tự động hóa chuỗi email chào mừng cho thành viên mới đăng ký

Ngay sau khi một người dùng đăng ký tài khoản thành công, hệ thống sẽ bắt đầu một chuỗi email tự động được lập lịch sẵn. Email đầu tiên gửi ngay lập tức để xác nhận tài khoản, email thứ hai gửi sau 1 ngày để hướng dẫn sử dụng dịch vụ, và email thứ ba gửi sau 3 ngày để giới thiệu các tính năng cao cấp. Bài toán yêu cầu thiết kế một hệ thống quản lý luồng công việc giúp theo dõi vị trí của từng người dùng trong chuỗi email và đảm bảo các email được gửi đúng tiến độ.

### Gửi email chúc mừng sinh nhật và ưu đãi định kỳ hàng năm

Hệ thống cần quét cơ sở dữ liệu khách hàng vào mỗi buổi sáng để tìm ra những người có ngày sinh nhật trùng với ngày hiện tại. Đối với mỗi khách hàng tìm thấy, hệ thống sẽ tự động cá nhân hóa nội dung email với tên của họ và gửi kèm một mã quà tặng có thời hạn sử dụng ngắn. Đây là bài toán về lập lịch công việc định kỳ và xử lý dữ liệu theo lô để đảm bảo không bỏ sót khách hàng nhưng cũng không làm quá tải máy chủ gửi thư.

### Kiểm soát giới hạn tốc độ gửi và ưu tiên loại email

Hệ thống cần phân loại email thành hai nhóm chính là email giao dịch như xác nhận đơn hàng, lấy lại mật khẩu và email marketing. Email giao dịch luôn phải được ưu tiên gửi đi ngay lập tức, trong khi email marketing có thể được gửi chậm hơn theo từng đợt để tránh bị các nhà cung cấp dịch vụ email chặn vì gửi quá nhanh. Hệ thống cần một cơ chế hàng đợi ưu tiên để điều tiết luồng dữ liệu đi ra bên ngoài dựa trên tầm quan trọng của từng loại thông điệp.

### Thử nghiệm nội dung email để tìm ra phiên bản hiệu quả nhất

Trong một chiến dịch, người quản lý muốn thử nghiệm hai mẫu tiêu đề email khác nhau trên một nhóm nhỏ khách hàng để xem mẫu nào có tỷ lệ mở cao hơn. Sau một khoảng thời gian theo dõi, mẫu chiến thắng sẽ tự động được sử dụng để gửi cho toàn bộ số lượng khách hàng còn lại trong danh sách. Bài toán này yêu cầu thiết kế hệ thống có khả năng chia tách nhóm người nhận, so sánh dữ liệu tương tác giữa các phiên bản và tự động đưa ra quyết định gửi thư tiếp theo.
