# Sort by popularity

### Hệ thống bảng xếp hạng bài hát trên nền tảng stream nhạc

Trong ứng dụng này, độ phổ biến của một bài hát không chỉ dựa vào tổng lượt nghe mà còn phụ thuộc vào tốc độ tăng trưởng trong ngắn hạn. Hệ thống cần ghi lại mỗi lần người dùng nhấn nút play, thời gian họ nghe bài hát đó và liệu họ có bỏ qua giữa chừng hay không. Thách thức ở đây là làm sao để các bài hát mới phát hành vẫn có cơ hội lọt vào danh sách phổ biến thay vì bị các bài hát cũ chiếm ưu thế nhờ tích lũy lượt nghe qua nhiều năm.

### Trang danh mục sản phẩm của sàn thương mại điện tử

Sàn thương mại điện tử cần sắp xếp hàng hóa dựa trên sự kết hợp giữa số lượng đơn hàng thành công, số lượt thêm vào giỏ hàng và số lượng đánh giá năm sao. Tuy nhiên, hệ thống cũng phải tính đến tỷ lệ hoàn hàng hoặc các đánh giá tiêu cực để hạ bậc các sản phẩm kém chất lượng. Bạn cần thiết kế cách lưu trữ các chỉ số này sao cho việc truy vấn danh sách sản phẩm đã sắp xếp diễn ra ngay lập tức dù có hàng triệu mặt hàng.

### Luồng tin tức xu hướng trên mạng xã hội

Bài toán này tập trung vào việc hiển thị các bài viết đang gây chú ý dựa trên số lượt yêu thích, bình luận và chia sẻ. Độ phổ biến ở đây mang tính thời điểm cực kỳ cao, nghĩa là một bài viết có một nghìn tương tác trong một giờ qua sẽ có thứ hạng cao hơn bài viết có mười nghìn tương tác từ tuần trước. Dữ liệu cần phản ánh được sự suy giảm giá trị theo thời gian của mỗi tương tác.

### Danh sách các khóa học trực tuyến được quan tâm nhất

Trên một nền tảng học tập, độ phổ biến được xác định bởi số lượng học viên đăng ký mới, tỷ lệ hoàn thành khóa học và số câu hỏi được đặt ra trong diễn đàn thảo luận. Hệ thống cần phân biệt được giữa việc một khóa học được quảng cáo nhiều dẫn đến lượt xem cao và một khóa học thực sự chất lượng dựa trên sự tương tác sâu của người dùng.

### Hệ thống gợi ý video trên nền tảng chia sẻ clip ngắn

Điểm phổ biến của video được tính toán dựa trên thời lượng xem trung bình và tỷ lệ người dùng nhấn vào trang cá nhân của tác giả sau khi xem. Hệ thống phải xử lý một lượng dữ liệu khổng lồ đổ về theo thời gian thực và cập nhật lại thứ hạng hiển thị liên tục. Điều này đòi hỏi cấu trúc lưu trữ dữ liệu phải hỗ trợ việc ghi và đọc với tần suất cực cao mà không gây trễ cho trải nghiệm người dùng.

### Bảng tin tuyển dụng hot trên website tìm việc làm

Các công việc được coi là phổ biến khi có nhiều lượt nộp hồ sơ, nhiều lượt lưu bài đăng và thời gian niêm yết còn hiệu lực. Bài toán đặt ra là khi một công việc đã đủ số lượng ứng viên hoặc hết hạn, nó phải được loại bỏ khỏi danh sách phổ biến ngay lập tức để tránh lãng phí tài nguyên của hệ thống và thời gian của người tìm việc.

### Xếp hạng các câu hỏi thường gặp trong hệ thống hỗ trợ khách hàng

Để giảm tải cho nhân viên tư vấn, hệ thống cần đẩy các câu hỏi được nhiều người quan tâm lên đầu trang trợ giúp. Độ phổ biến được tính bằng số lần người dùng tìm kiếm từ khóa liên quan và việc họ có nhấn vào nút xác nhận thông tin này hữu ích hay không. Dữ liệu này giúp bộ phận vận hành biết được những vấn đề nhức nhối nhất mà khách hàng đang gặp phải.

### Danh sách các nhà hàng nổi bật trên ứng dụng đặt đồ ăn

Một nhà hàng phổ biến không chỉ có nhiều đơn hàng mà còn phải có mật độ đơn hàng cao trong khu vực địa lý cụ thể của người dùng. Hệ thống cần tính toán điểm số dựa trên khoảng cách, thời gian chuẩn bị món ăn và các phản hồi tích cực gần đây. Việc thiết kế database phải cho phép lọc nhanh các nhà hàng phổ biến theo từng quận huyện hoặc bán kính nhất định.

### Bảng xếp hạng các dự án mã nguồn mở trên kho lưu trữ

Độ phổ biến của một dự án được đánh giá qua số lượng người theo dõi, số lần sao chép mã nguồn và số lượng đóng góp từ cộng đồng. Hệ thống cần thống kê được biến động theo tuần hoặc theo tháng để người dùng biết được dự án nào đang dẫn đầu xu hướng công nghệ. Việc này yêu cầu lưu trữ lịch sử tương tác một cách chi tiết để có thể truy vấn ngược lại các mốc thời gian trong quá khứ.

### Gợi ý các địa điểm du lịch trong ứng dụng bản đồ

Người dùng thường tìm kiếm những địa điểm phổ biến để tham quan dựa trên số lượt check-in và số lượng ảnh được tải lên tại vị trí đó. Bài toán yêu cầu tích hợp dữ liệu từ nhiều nguồn tương tác khác nhau và xử lý các trường hợp dữ liệu ảo hoặc hành vi spam để đảm bảo bảng xếp hạng phản ánh đúng thực tế mức độ yêu thích của cộng đồng.
