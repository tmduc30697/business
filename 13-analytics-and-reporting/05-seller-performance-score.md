# Seller performance score

### Tính toán điểm hiệu suất tổng hợp theo chu kỳ cố định

Hệ thống cần thu thập dữ liệu từ nhiều nguồn khác nhau bao gồm tổng số đơn hàng hoàn tất, số lượng đơn hàng bị hủy bởi người bán, số lượng đánh giá năm sao từ khách hàng và thời gian trung bình để bàn giao hàng cho đơn vị vận chuyển. Cứ vào ngày đầu tiên của mỗi tháng, hệ thống sẽ chạy một tiến trình để tính toán ra một con số điểm đại diện cho hiệu suất của tháng trước đó. Điểm số này sẽ quyết định thứ hạng của người bán và mức phí hoa hồng mà họ phải trả cho sàn thương mại điện tử trong tháng tiếp theo.

### Theo dõi tỷ lệ hủy đơn hàng gây ảnh hưởng đến uy tín

Một người bán có thể nhận được rất nhiều đơn hàng nhưng nếu họ thường xuyên hủy đơn do hết hàng hoặc sai giá, trải nghiệm người dùng sẽ bị ảnh hưởng nghiêm trọng. Bài toán yêu cầu hệ thống phải phân loại rõ ràng lý do hủy đơn: do người mua đổi ý, do lỗi hệ thống hay lỗi chủ quan từ phía người bán. Chỉ những đơn hàng bị hủy do lỗi chủ quan của người bán mới bị tính vào điểm phạt. Hệ thống cần lưu trữ trạng thái chi tiết của từng đơn hàng và người thực hiện hành động hủy để phục vụ việc truy vấn và đối soát khi người bán khiếu nại.

### Giám sát cam kết thời gian giao hàng và xử lý đơn hàng

Mỗi đơn hàng khi phát sinh đều có một mốc thời gian quy định gọi là hạn chót bàn giao cho đơn vị vận chuyển. Nếu người bán bàn giao sau thời điểm này, đơn hàng bị coi là vi phạm cam kết dịch vụ. Hệ thống cần ghi nhận chính xác thời điểm đơn hàng được tạo, thời điểm người bán xác nhận đơn và thời điểm đơn vị vận chuyển quét mã vận đơn đầu tiên. Từ các mốc thời gian này, hệ thống tính toán tỷ lệ đơn hàng trễ hạn trên tổng số đơn hàng phát sinh trong tuần để cảnh báo hoặc giảm điểm hiển thị của gian hàng.

### Phân tích phản hồi và đánh giá từ khách hàng sau khi mua

Điểm hiệu suất không chỉ dựa trên con số doanh thu mà còn dựa trên sự hài lòng của khách hàng thông qua số sao đánh giá và nội dung nhận xét. Bài toán đặt ra là phải tính toán điểm trung bình cộng của tất cả các đánh giá trong vòng 90 ngày gần nhất để đảm bảo điểm số phản ánh đúng chất lượng dịch vụ hiện tại. Hệ thống cần xử lý được trường hợp khách hàng thay đổi đánh giá từ xấu thành tốt sau khi được người bán hỗ trợ, và điểm số phải được cập nhật tương ứng theo các thay đổi đó.

### Hệ thống cảnh báo và xử phạt tự động dựa trên ngưỡng điểm

Dựa trên điểm hiệu suất được tính toán liên tục, hệ thống cần có cơ chế tự động đưa ra các hình phạt khi điểm số rơi xuống dưới một ngưỡng nhất định. Ví dụ, nếu điểm hiệu suất dưới mức trung bình, người bán sẽ bị giới hạn số lượng sản phẩm được đăng bán mới hoặc bị tạm dừng tham gia các chương trình khuyến mãi của sàn. Nếu điểm quá thấp, gian hàng có thể bị khóa tạm thời. Điều này đòi hỏi thiết kế database phải có bảng lưu trữ các ngưỡng cấu hình phạt và bảng ghi nhật ký các lệnh phạt đã áp dụng cho từng gian hàng.

### Xử lý trọng số dữ liệu theo thời gian thực cho các sự kiện đặc biệt

Trong các ngày hội mua sắm lớn với lượng đơn hàng tăng đột biến, hệ thống cần một cơ chế tính điểm tạm thời hoặc điều chỉnh trọng số để không làm khó người bán do quá tải vận chuyển ngoài ý muốn. Bài toán yêu cầu thiết kế một hệ thống có khả năng nhận diện các khoảng thời gian đặc biệt và áp dụng các công thức tính toán khác nhau cho cùng một tập chỉ số hiệu suất. Dữ liệu thô vẫn được giữ nguyên nhưng kết quả đầu ra của API lấy điểm số sẽ thay đổi tùy thuộc vào cấu hình của quản trị viên hệ thống.

### Đối soát và xử lý khiếu nại về chỉ số hiệu suất của người bán

Người bán có quyền khiếu nại nếu họ cho rằng một chỉ số nào đó bị tính sai, ví dụ như đơn hàng bị trễ do lỗi của đơn vị vận chuyển chứ không phải do họ. Hệ thống cần một quy trình cho phép điều chỉnh các bản ghi vi phạm. Khi một khiếu nại được phê duyệt, hệ thống phải thực hiện tính toán lại toàn bộ điểm hiệu suất của người bán đó trong giai đoạn liên quan và cập nhật lại thứ hạng của họ. Điều này đòi hỏi tính toàn vẹn dữ liệu rất cao giữa các bảng ghi vi phạm và bảng tổng hợp điểm.

### Báo cáo xu hướng hiệu suất và dự báo tăng trưởng cho gian hàng

Để giúp người bán cải thiện dịch vụ, hệ thống cần cung cấp các biểu đồ về sự thay đổi của các chỉ số hiệu suất theo thời gian như theo tuần hoặc theo tháng. Hệ thống không chỉ lưu điểm số hiện tại mà còn phải lưu trữ lịch sử điểm số để so sánh. Từ các dữ liệu lịch sử này, API sẽ trả về các thông tin tư vấn như chỉ số nào đang kéo điểm tổng xuống thấp nhất và người bán cần tập trung cải thiện khâu nào nhất để tăng điểm trong tương lai.
