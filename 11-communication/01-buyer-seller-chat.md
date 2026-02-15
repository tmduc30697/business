# Buyer-seller chat

### Quản lý phiên chat và lịch sử tin nhắn

Bài toán này tập trung vào việc lưu trữ hàng triệu tin nhắn giữa người mua và người bán. Hệ thống cần phân biệt giữa tin nhắn văn bản, hình ảnh, và liên kết sản phẩm. Bạn phải giải quyết cách tổ chức bảng để truy vấn lịch sử hội thoại nhanh chóng theo thời gian thực, đồng thời đảm bảo rằng khi một người dùng xóa lịch sử ở phía họ thì người kia vẫn nhìn thấy được nội dung đó.

### Gắn kèm ngữ cảnh sản phẩm và đơn hàng vào hội thoại

Trong thực tế, người mua thường bắt đầu chat từ một trang sản phẩm cụ thể hoặc một đơn hàng đang gặp sự cố. Bài toán yêu cầu thiết kế sao cho mỗi cuộc hội thoại có thể liên kết với một ID sản phẩm hoặc ID đơn hàng tương ứng. Khi người bán mở chat, họ phải thấy ngay thông tin tóm tắt của sản phẩm hoặc đơn hàng đó để phản hồi chính xác mà không cần hỏi lại người mua.

### Trạng thái tin nhắn và thông báo thời gian thực

Hệ thống cần theo dõi trạng thái của từng tin nhắn bao gồm đã gửi, đã nhận và đã xem. Thách thức ở đây là việc cập nhật trạng thái "đã xem" cho toàn bộ các tin nhắn cũ khi người dùng mở khung chat. Ngoài ra, bạn cần tính đến việc đẩy thông báo (push notification) cho người dùng khi họ không online trong ứng dụng nhưng có tin nhắn mới đến.

### Phân quyền và quản lý nhân viên chăm sóc khách hàng

Đối với các shop lớn, người phản hồi không chỉ là chủ shop mà có thể là nhiều nhân viên trực chiến. Bài toán đặt ra là làm thế nào để điều phối một cuộc chat từ người mua đến đúng nhóm nhân viên đang online. Hệ thống cần ghi vết xem nhân viên nào đã trả lời tin nhắn nào để chủ shop có thể đánh giá hiệu quả công việc và kiểm soát chất lượng tư vấn.

### Hệ thống trả lời tự động và tin nhắn mẫu

Để giảm tải cho người bán, hệ thống cần cho phép thiết lập các kịch bản trả lời tự động khi shop offline hoặc khi người mua chào hỏi lần đầu. Ngoài ra, người bán cần một kho tin nhắn mẫu để gửi nhanh các thông tin như hướng dẫn bảo hành, địa chỉ shop hoặc lời cảm ơn. Việc thiết kế database phải linh hoạt để lưu trữ các quy tắc kích hoạt tin nhắn tự động này.

### Bộ lọc nội dung vi phạm và chặn người dùng

Để bảo vệ cộng đồng, hệ thống chat cần có khả năng lọc các từ khóa cấm, số điện thoại hoặc liên kết ngoài nhằm tránh giao dịch gian lận ngoài hệ thống. Bên cạnh đó, bài toán còn bao gồm tính năng chặn người dùng (block). Khi một người bán chặn người mua, họ sẽ không nhận được tin nhắn mới nhưng lịch sử cũ vẫn phải được bảo lưu để phục vụ việc đối soát hoặc khiếu nại sau này.

### Đánh giá hiệu suất phản hồi của người bán

Sàn thương mại điện tử thường hiển thị tỉ lệ phản hồi và thời gian phản hồi trung bình của shop để người mua tin tưởng hơn. Bài toán yêu cầu bạn phải thiết kế cách log dữ liệu sao cho có thể tính toán được thời gian từ lúc người mua gửi tin nhắn đầu tiên đến lúc người bán phản hồi, từ đó tổng hợp thành các chỉ số KPI hiển thị trên trang cá nhân của shop.

### Quản lý khiếu nại và sự can thiệp của Quản trị viên

Khi có tranh chấp về đơn hàng, người mua hoặc người bán có thể yêu cầu Quản trị viên sàn nhảy vào cuộc trò chuyện để phân xử. Bài toán này yêu cầu thiết kế hệ thống cho phép "mời" một bên thứ ba vào xem nội dung chat nhưng không được phép sửa đổi dữ liệu. Quản trị viên cần có quyền trích xuất biên bản hội thoại để làm bằng chứng giải quyết khiếu nại.
