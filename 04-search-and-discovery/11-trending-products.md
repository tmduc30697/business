# Trending products

### Hệ thống bảng xếp hạng sản phẩm bán chạy theo thời gian

Xây dựng một tính năng cho phép người dùng xem danh sách các sản phẩm có số lượng đơn hàng hoàn tất cao nhất trong các khoảng thời gian như 24 giờ qua, 7 ngày qua hoặc trong tháng hiện tại. Hệ thống cần ghi nhận thời điểm phát sinh giao dịch thành công và tổng hợp số lượng bán ra của từng mã hàng. Thách thức ở đây là việc xử lý dữ liệu lớn khi số lượng đơn hàng tăng cao và cách cập nhật thứ hạng sao cho đảm bảo tính thời gian thực mà không làm treo hệ thống.

### Theo dõi xu hướng tìm kiếm từ khóa phổ biến

Thiết kế một module ghi lại mọi từ khóa mà người dùng nhập vào thanh tìm kiếm của trang thương mại điện tử. Hệ thống phải phân tích được những từ khóa nào có tần suất xuất hiện tăng đột biến trong một khung giờ nhất định so với mức trung bình trước đó. Dữ liệu này giúp gợi ý cho người dùng những cụm từ đang là xu hướng và hỗ trợ bộ phận marketing nhập thêm các mặt hàng liên quan đến những từ khóa đang hot này.

### Đề xuất sản phẩm dựa trên lượt xem trang và tương tác

Bài toán tập trung vào việc thu thập các sự kiện người dùng click vào xem chi tiết sản phẩm hoặc thêm sản phẩm vào giỏ hàng nhưng chưa thanh toán. Một sản phẩm được coi là trending nếu nó nhận được lượng truy cập vượt trội trong một khoảng thời gian ngắn. Bạn cần thiết kế cách lưu trữ nhật ký hành vi người dùng sao cho có thể truy vấn nhanh danh sách các sản phẩm đang nhận được nhiều sự quan tâm nhất để hiển thị lên trang chủ.

### Phân tích xu hướng sản phẩm theo danh mục và khu vực địa lý

Thay vì chỉ xem xu hướng chung của toàn sàn, hệ thống cần bóc tách các sản phẩm nổi bật theo từng ngành hàng cụ thể hoặc theo vị trí địa lý của người mua. Ví dụ, áo khoác có thể là sản phẩm trending ở khu vực phía Bắc nhưng không phải ở phía Nam. Bài toán yêu cầu cấu trúc database phải liên kết chặt chẽ giữa thông tin sản phẩm, danh mục cha-con và địa chỉ giao hàng trong đơn hàng để đưa ra các báo cáo chính xác.

### Quản lý chiến dịch khuyến mãi gắn liền với sản phẩm hot

Trong các sự kiện Flash Sale, một số sản phẩm sẽ có lượng truy cập và mua hàng tăng vọt do được trợ giá. Bài toán đặt ra là làm thế nào để phân biệt giữa một sản phẩm trending tự nhiên và một sản phẩm trending do có chiến dịch quảng cáo. Hệ thống cần quản lý các phiên giảm giá, số lượng tồn kho giới hạn cho mỗi phiên và ghi nhận hiệu quả của chiến dịch thông qua việc theo dõi tốc độ bán hết hàng của các sản phẩm đó.

### Hệ thống cảnh báo sản phẩm hết hàng dựa trên tốc độ bán

Dựa trên dữ liệu bán hàng thực tế, hệ thống cần tính toán tốc độ tiêu thụ của từng mặt hàng để dự báo những sản phẩm nào sắp trở thành xu hướng và có nguy cơ hết hàng trong vài giờ tới. Đây là bài toán quan trọng trong quản trị kho bãi, yêu cầu database phải lưu trữ lịch sử nhập xuất kho chi tiết và hỗ trợ các truy vấn tính toán hiệu suất bán hàng để gửi thông báo kịp thời cho nhà bán hàng.

### Gợi ý sản phẩm trending theo nhóm đối tượng người dùng

Mỗi phân khúc khách hàng sẽ có xu hướng quan tâm đến các loại sản phẩm khác nhau. Bài toán yêu cầu thiết kế hệ thống có khả năng phân loại người dùng dựa trên thông tin nhân khẩu học như độ tuổi, giới tính hoặc sở thích cá nhân, sau đó hiển thị các sản phẩm đang hot tương ứng với nhóm đó. Việc này đòi hỏi sự kết hợp giữa bảng thông tin người dùng, lịch sử mua sắm và bảng xếp hạng sản phẩm chung của toàn hệ thống.

### Đánh giá độ nóng của sản phẩm dựa trên phản hồi và đánh giá

Một sản phẩm có thể có lượt mua cao nhưng nếu nhận về nhiều phản hồi tiêu cực thì không nên được ưu tiên hiển thị trong danh mục trending. Bài toán này yêu cầu xây dựng một hệ thống tính điểm dựa trên sự kết hợp giữa doanh số bán ra và điểm số đánh giá từ khách hàng. Chỉ những sản phẩm có lượng tương tác tích cực và điểm số trung bình cao trong thời gian gần nhất mới được xếp hạng vào danh sách các sản phẩm xu hướng hàng đầu.
