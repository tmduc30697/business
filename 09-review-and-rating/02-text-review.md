# Text review

### Quản lý đánh giá đa phương tiện và xác thực mua hàng

Bài toán này tập trung vào việc lưu trữ các đánh giá kèm theo hình ảnh hoặc video từ phía người dùng. Hệ thống cần phân biệt rõ ràng giữa đánh giá từ những người đã thực sự mua hàng và những người đánh giá tự do. Bạn cần thiết kế cách liên kết giữa bảng đánh giá, bảng chi tiết đơn hàng và bảng lưu trữ tài nguyên đa phương tiện sao cho tối ưu truy vấn khi hiển thị trên trang sản phẩm.

### Hệ thống phản hồi đa cấp và tương tác cộng đồng

Thay vì chỉ là những dòng nhận xét đơn lẻ, bài toán này yêu cầu xây dựng tính năng cho phép người bán phản hồi lại đánh giá của khách và các khách hàng khác có thể nhấn thích hoặc không thích một đánh giá cụ thể. Điều này đòi hỏi cấu trúc dữ liệu dạng cây hoặc phân cấp để quản lý các lượt thảo luận lồng nhau và tính toán tổng số lượt tương tác theo thời gian thực.

### Kiểm duyệt nội dung tự động và thủ công

Trong thực tế, các đánh giá thường chứa từ ngữ nhạy cảm, quảng cáo rác hoặc nội dung không phù hợp. Bài toán đặt ra quy trình trạng thái của một đánh giá từ lúc đang chờ duyệt, đã xuất bản đến bị từ chối. Bạn cần thiết kế hệ thống có khả năng tích hợp các dịch vụ lọc từ khóa hoặc trí tuệ nhân tạo để gắn cờ nội dung vi phạm trước khi hiển thị công khai.

### Tổng hợp điểm số và thống kê xếp hạng chi tiết

Người dùng thường muốn nhìn thấy biểu đồ phân bổ sao từ 1 đến 5 và điểm trung bình ngay đầu trang. Thách thức ở đây là làm thế nào để cập nhật các con số thống kê này một cách nhanh chóng khi có hàng triệu đánh giá mà không làm giảm hiệu năng hệ thống. Bạn cần tính đến các phương án lưu trữ dữ liệu tổng hợp (metadata) thay vì đếm trực tiếp từ bảng đánh giá mỗi khi có người truy cập.

### Phân loại đánh giá theo thuộc tính sản phẩm cụ thể

Một chiếc áo có thể được đánh giá dựa trên các tiêu chí khác nhau như chất liệu, kích cỡ và màu sắc, trong khi một thiết bị điện tử lại cần đánh giá về độ bền và tính năng. Bài toán yêu cầu thiết kế database linh hoạt để lưu trữ các điểm số chi tiết theo từng tiêu chí tùy biến cho từng loại ngành hàng khác nhau thay vì chỉ có một con số đánh giá chung chung.

### Hệ thống lịch sử chỉnh sửa và ghi nhật ký thay đổi

Khách hàng có thể thay đổi ý định sau một thời gian sử dụng sản phẩm và muốn cập nhật lại nhận xét của mình. Bài toán này yêu cầu bạn thiết kế cơ chế lưu trữ các phiên bản cũ của đánh giá để quản trị viên có thể theo dõi sự thay đổi nội dung, đồng thời đảm bảo tính minh bạch trong việc đánh giá sản phẩm của người dùng.

### Đẩy thông báo và cập nhật thời gian thực cho người bán

Khi có một đánh giá tiêu cực (ví dụ 1 sao hoặc 2 sao), hệ thống cần ngay lập tức gửi thông báo đến bộ phận chăm sóc khách hàng của người bán để họ xử lý kịp thời. Bài toán này hướng bạn đến việc thiết kế kiến trúc hướng sự kiện, sử dụng các hàng đợi tin nhắn để tách biệt luồng ghi dữ liệu đánh giá và luồng gửi thông báo đa kênh như email, ứng dụng di động hoặc web.

### Tìm kiếm và lọc đánh giá nâng cao theo ngữ cảnh

Khách hàng thường có nhu cầu lọc xem các đánh giá có hình ảnh trước, hoặc tìm kiếm các đánh giá có chứa các từ khóa cụ thể như giao hàng nhanh hay đóng gói kỹ. Bài toán này yêu cầu thiết kế hệ thống chỉ mục tìm kiếm hiệu quả, cho phép người dùng kết hợp nhiều điều kiện lọc cùng lúc mà vẫn đảm bảo tốc độ phản hồi dưới một giây.
