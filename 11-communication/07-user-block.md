# User block

### Chặn hai chiều trên mạng xã hội đa nền tảng

Người dùng khi thực hiện thao tác chặn một tài khoản khác thì hệ thống cần đảm bảo cả hai bên không thể tìm thấy hồ sơ của nhau qua thanh tìm kiếm, không thể xem các bài viết trên tường nhà đối phương và mọi thông báo tương tác cũ sẽ bị ẩn đi. Vấn đề trở nên phức tạp khi người dùng có thể chặn nhau trên ứng dụng di động nhưng dữ liệu phải được đồng bộ ngay lập tức trên bản web để tránh việc lộ thông tin qua các phiên đăng nhập khác nhau.

### Quản lý danh sách chặn trong nhóm chat cộng đồng

Trong một ứng dụng nhắn tin nhóm, một người dùng có thể chặn một thành viên khác nhưng cả hai vẫn cùng ở trong một nhóm chung. Bài toán đặt ra là khi người bị chặn gửi tin nhắn vào nhóm, hệ thống phải xử lý để người chặn không nhìn thấy nội dung đó hoặc hiển thị dưới dạng tin nhắn bị ẩn, trong khi các thành viên khác vẫn thấy bình thường. Điều này đòi hỏi logic xử lý tại tầng API hoặc Client để lọc dữ liệu dựa trên danh sách chặn cá nhân.

### Chặn liên lạc dựa trên định danh thiết bị và địa chỉ IP

Để ngăn chặn các đối tượng quấy rối chuyên nghiệp thường xuyên tạo tài khoản mới sau khi bị chặn, hệ thống cần một cơ chế chặn không chỉ dựa trên ID người dùng mà còn dựa trên dấu vân tay thiết bị hoặc địa chỉ IP. Khi một tài khoản bị chặn, tất cả các tài khoản khác được khởi tạo từ cùng một thiết bị đó cũng sẽ tự động rơi vào danh sách hạn chế để bảo vệ nạn nhân một cách triệt để.

### Hệ thống chặn tạm thời và tự động gỡ chặn theo thời gian

Người dùng muốn có tính năng chặn một ai đó trong một khoảng thời gian nhất định như 24 giờ, một tuần hoặc một tháng để tránh bị làm phiền trong lúc nóng giận hoặc bận rộn. Hệ thống cần một cơ chế hàng đợi hoặc lập lịch để tự động cập nhật lại trạng thái quan hệ giữa hai người dùng khi hết thời hạn mà không cần sự can thiệp thủ công, đồng thời phải lưu trữ lịch sử các lần chặn này.

### Phân cấp mức độ chặn và hạn chế tương tác

Thay vì chặn hoàn toàn, người dùng có nhu cầu chỉ hạn chế một số quyền cụ thể như không cho phép đối phương bình luận vào bài viết, không cho phép gọi điện video nhưng vẫn có thể nhắn tin văn bản. Bài toán này yêu cầu thiết kế cơ sở dữ liệu linh hoạt với các cờ trạng thái khác nhau thay vì chỉ là một cột boolean đơn giản, giúp hệ thống kiểm tra quyền hạn chi tiết cho từng loại hành động API.

### Chặn theo danh sách đen từ bên thứ ba hoặc từ cộng đồng

Trong các ứng dụng thương mại điện tử, người bán hàng có thể đăng ký sử dụng danh sách đen được chia sẻ bởi cộng đồng để chặn các tài khoản có lịch sử đặt hàng ảo hoặc đánh giá xấu không căn cứ. Hệ thống cần xử lý việc nhập dữ liệu hàng loạt, kiểm tra trùng lặp và đối soát quyền sở hữu để đảm bảo việc chặn dựa trên danh sách chia sẻ này không vi phạm các chính sách bảo mật cá nhân.

### Xử lý hệ quả của việc chặn đối với dữ liệu lịch sử

Khi một người dùng thực hiện hành động chặn, câu hỏi đặt ra là các dữ liệu trong quá khứ như lượt thích, bình luận cũ hay các giao dịch tài chính dùng chung sẽ được xử lý như thế nào. Hệ thống cần quyết định giữa việc xóa cứng dữ liệu, ẩn tạm thời hay giữ nguyên nhưng vô hiệu hóa liên kết để đảm bảo tính toàn vẹn của dữ liệu hệ thống mà vẫn đáp ứng được nhu cầu không nhìn thấy nhau của người dùng.

### Chặn liên lạc trong ứng dụng gọi xe và giao hàng

Trong mô hình kinh tế chia sẻ, hành khách có thể chặn tài xế hoặc ngược lại sau một chuyến đi tồi tệ để đảm bảo rằng trong tương lai, thuật toán ghép cặp của hệ thống sẽ không bao giờ kết nối hai người này lại với nhau. Bài toán này yêu cầu sự phối hợp chặt chẽ giữa dịch vụ quản lý người dùng và dịch vụ định tuyến chuyến đi để lọc kết quả ngay từ bước tìm kiếm tài xế trong thời gian thực.
