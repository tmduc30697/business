# Filter by rating

### Hệ thống đánh giá của sàn thương mại điện tử đa quốc gia

Trong kịch bản này, một sản phẩm có hàng triệu lượt đánh giá từ nhiều quốc gia và ngôn ngữ khác nhau. Hệ thống cần hiển thị số sao trung bình theo thời gian thực và cho phép người dùng lọc sản phẩm theo từng mức sao cụ thể từ một đến năm. Thách thức nằm ở chỗ số lượng đánh giá cực lớn khiến việc tính toán trung bình cộng trực tiếp từ bảng lưu trữ mỗi khi người dùng nhấn lọc sẽ gây quá tải cho cơ sở dữ liệu. Bạn cần thiết kế giải pháp lưu trữ dữ liệu sao cho việc truy vấn lọc theo sao diễn ra nhanh chóng nhưng vẫn đảm bảo tính chính xác khi có đánh giá mới được thêm vào liên tục.

### Nền tảng đặt phòng khách sạn với các tiêu chí đánh giá chi tiết

Khách hàng không chỉ đánh giá chung cho khách sạn mà còn chấm điểm riêng biệt cho các mục như vị trí, độ sạch sẽ, thái độ phục vụ và giá cả. Bài toán yêu cầu người dùng có thể lọc những khách sạn có điểm sạch sẽ từ bốn sao trở lên hoặc những khách sạn có điểm phục vụ xuất sắc. Việc thiết kế bảng dữ liệu phải hỗ trợ được nhiều thuộc tính đánh giá khác nhau cho cùng một thực thể và cho phép lọc linh hoạt theo từng tiêu chí hoặc kết hợp nhiều tiêu chí đánh giá cùng lúc để đưa ra kết quả chính xác nhất.

### Ứng dụng đặt đồ ăn với tính năng lọc theo đánh giá của người dùng uy tín

Để tăng độ tin cậy, hệ thống cho phép người dùng lọc các quán ăn dựa trên số sao trung bình nhưng chỉ tính từ những thực thần hoặc người dùng có cấp bậc cao. Điều này có nghĩa là mỗi món ăn hoặc cửa hàng sẽ có nhiều loại điểm trung bình khác nhau tùy thuộc vào đối tượng đánh giá. Bạn cần thiết kế cấu trúc API và database sao cho có thể phân loại được trọng số của các đánh giá và trả về kết quả lọc theo sao dựa trên tệp khách hàng mục tiêu mà người dùng đang quan tâm.

### Trang web đánh giá khóa học trực tuyến theo từng phiên bản cập nhật

Một khóa học công nghệ có thể thay đổi nội dung qua từng năm, dẫn đến việc đánh giá của phiên bản cũ không còn phản ánh đúng chất lượng hiện tại. Bài toán yêu cầu hệ thống lọc sản phẩm dựa trên số sao trung bình của phiên bản mới nhất hoặc trong khoảng thời gian sáu tháng gần đây. Người dùng muốn tìm những khóa học đang có xu hướng tốt thay vì những khóa học có điểm cao nhờ tích lũy từ nhiều năm trước nhưng nội dung đã lỗi thời. Việc này đòi hỏi thiết kế hệ thống có khả năng xử lý dữ liệu theo thời gian và phiên bản rất chặt chẽ.

### Hệ thống phân phối trò chơi điện tử với bộ lọc đánh giá tích cực

Thay vì chỉ dùng thang điểm từ một đến năm sao, hệ thống này sử dụng cơ chế đánh giá tích cực hoặc tiêu cực để tính phần trăm. Người dùng muốn lọc ra những trò chơi có tỷ lệ đánh giá tích cực trên tám mươi phần trăm và có tối thiểu một nghìn lượt đánh giá để tránh các trường hợp gian lận điểm số. Bạn cần giải quyết vấn đề về ngưỡng dữ liệu tối thiểu khi thực hiện các tác vụ lọc và cách thức cập nhật các con số thống kê này vào bộ nhớ đệm để tăng hiệu suất phản hồi của API.

### Sàn giao dịch sản phẩm cũ với cơ chế lọc độ uy tín của người bán

Trong mô hình này, người dùng không chỉ lọc sản phẩm mà còn lọc dựa trên số sao trung bình của chính người bán đó. Một sản phẩm có thể tốt nhưng nếu người bán có đánh giá thấp về khâu vận chuyển hoặc giao tiếp, khách hàng sẽ muốn loại bỏ khỏi danh sách tìm kiếm. Điều này dẫn đến một truy vấn phức tạp kết hợp giữa bảng sản phẩm và bảng người dùng. Bạn cần thiết kế ERD sao cho mối liên kết giữa uy tín người bán và trạng thái hiển thị của sản phẩm được tối ưu, tránh tình trạng truy vấn lồng nhau gây chậm trễ hệ thống.

### Ứng dụng xem phim và chương trình truyền hình có phân loại theo nguồn đánh giá

Hệ thống tổng hợp điểm số từ nhiều nguồn khác nhau như từ khán giả đại chúng, từ các nhà phê bình chuyên nghiệp và từ các trang tạp chí nghệ thuật. Người dùng có quyền chọn lọc phim dựa trên số sao trung bình của riêng nhóm phê bình hoặc của riêng khán giả. Bài toán này yêu cầu một kiến trúc dữ liệu linh hoạt để lưu trữ và phân tách các nguồn đánh giá khác nhau cho cùng một bộ phim, đồng thời đảm bảo API có thể xử lý các tham số lọc đa dạng từ phía người dùng một cách mượt mà.

### Dịch vụ thuê xe tự lái với bộ lọc đánh giá dựa trên tình trạng thực tế

Khách hàng thuê xe thường quan tâm đến đánh giá về độ mới và khả năng vận hành của xe sau mỗi chuyến đi. Bài toán đặt ra là hệ thống cần lọc ra những xe có đánh giá từ bốn sao trở lên nhưng phải loại trừ các đánh giá quá cũ hoặc các đánh giá từ những tài khoản chưa được xác minh danh tính. Thiết kế hệ thống cần chú trọng vào quy trình kiểm soát chất lượng dữ liệu đầu vào và các trạng thái của đánh giá để bộ lọc sao trung bình luôn hiển thị những giá trị trung thực và hữu ích nhất cho người dùng tiếp theo.
