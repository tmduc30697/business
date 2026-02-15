# Filter by price

### Sàn thương mại điện tử đa quốc gia với biến động tỷ giá

Hệ thống cần quản lý sản phẩm được bán bởi các nhà cung cấp từ nhiều quốc gia khác nhau, mỗi người niêm yết giá bằng đơn vị tiền tệ địa phương như USD, EUR, hay VND. Khi người dùng thực hiện lọc sản phẩm trong khoảng từ 500.000 đến 1.000.000 đơn vị tiền tệ họ đang chọn, hệ thống phải thực hiện chuyển đổi tỷ giá thời gian thực để trả về kết quả chính xác. Thách thức ở đây là làm sao để lưu trữ giá gốc và giá quy đổi sao cho việc truy vấn không bị chậm khi bảng sản phẩm có hàng triệu bản ghi.

### Hệ thống đặt phòng khách sạn theo mùa và ngày lễ

Giá phòng khách sạn không cố định mà thay đổi liên tục dựa trên ngày nhận phòng và ngày trả phòng của khách hàng. Một phòng có thể có giá khác nhau vào ngày thường, cuối tuần hoặc các dịp lễ tết. Khi người dùng lọc tìm các phòng có giá từ 2 triệu đến 3 triệu mỗi đêm, hệ thống phải tính toán giá trung bình hoặc giá cụ thể cho toàn bộ thời gian lưu trú dự kiến trước khi lọc. Điều này đòi hỏi thiết kế cấu trúc dữ liệu bảng giá theo thời gian (Time-series) và logic tính toán tại tầng API.

### Trang web đấu giá trực tuyến với giá thầu thay đổi liên tục

Trong một sàn đấu giá, giá của sản phẩm không phải là giá niêm yết mà là giá cao nhất hiện tại được trả bởi người mua. Người dùng muốn lọc các cuộc đấu giá sắp kết thúc có mức giá hiện tại nằm trong ngân sách của họ. Hệ thống cần xử lý việc cập nhật giá liên tục vào Database và đảm bảo rằng kết quả lọc luôn phản ánh đúng con số mới nhất, tránh tình trạng người dùng lọc giá 100 USD nhưng khi bấm vào thì giá đã nhảy lên 150 USD.

### Nền tảng tuyển dụng với lọc dải lương thực tế và kỳ vọng

Các tin tuyển dụng thường không có một con số giá duy nhất mà là một khoảng lương từ tối thiểu đến tối đa. Ngoài ra, một số tin tuyển dụng lại để trạng thái lương thỏa thuận. Bài toán đặt ra là khi ứng viên lọc các công việc có mức lương tối thiểu từ 20 triệu trở lên, hệ thống phải xử lý logic so khớp trên cả hai cột lương min và lương max, đồng thời quyết định cách hiển thị các công việc không công khai lương sao cho phù hợp với trải nghiệm người dùng.

### Hệ thống phân phối vé máy bay với nhiều hạng ghế

Một chuyến bay có nhiều mức giá khác nhau tùy thuộc vào hạng ghế như phổ thông, thương gia hoặc hạng nhất, và thậm chí trong cùng một hạng ghế cũng có các nhóm giá khác nhau tùy điều kiện hoàn hủy. Khi người dùng tìm kiếm chuyến bay với bộ lọc giá, hệ thống phải xác định xem sẽ lấy giá thấp nhất của chuyến bay đó để lọc hay cho phép người dùng chọn lọc theo từng hạng ghế cụ thể. Điều này ảnh hưởng trực tiếp đến cách thiết kế bảng quan hệ giữa chuyến bay, hạng ghế và bảng giá chi tiết.

### Chợ ứng dụng phần mềm với mô hình đăng ký định kỳ

Khác với sản phẩm vật lý, các phần mềm SaaS thường có giá tính theo tháng hoặc theo năm với các gói dịch vụ khác nhau như Basic, Pro, Enterprise. Người dùng có nhu cầu lọc các phần mềm có chi phí sử dụng hàng tháng dưới một mức nhất định. Bài toán yêu cầu thiết kế Database sao cho có thể chuẩn hóa các hình thức thanh toán khác nhau về một đơn vị thời gian chung để thực hiện phép so sánh lọc giá một cách nhất quán trên toàn hệ thống.

### Trang web bất động sản với giá theo diện tích

Trong lĩnh vực bất động sản, giá có thể được niêm yết dưới dạng tổng giá trị căn nhà hoặc đơn giá trên mỗi mét vuông. Bộ lọc giá cần phải thông minh để hiểu được người dùng đang muốn lọc theo tổng ngân sách hay lọc theo đơn giá. Hệ thống cần lưu trữ các thông số về diện tích và đơn giá riêng biệt, đồng thời phải hỗ trợ các truy vấn tính toán động để trả về kết quả khi người dùng thay đổi tiêu chí lọc giữa tổng giá và giá theo diện tích.

### Hệ thống bán lẻ với giá khuyến mãi và thẻ thành viên

Giá bán lẻ của một sản phẩm có thể thay đổi tùy thuộc vào việc sản phẩm đó có đang trong chương trình giảm giá hay không, hoặc khách hàng đó có phải là thành viên VIP được hưởng chiết khấu riêng hay không. Khi một khách hàng đã đăng nhập và thực hiện lọc sản phẩm theo giá, hệ thống phải ưu tiên lọc dựa trên giá sau khi đã áp dụng tất cả các loại chiết khấu dành riêng cho cá nhân đó. Đây là bài toán về thiết kế System Design để xử lý logic tính giá phức tạp trước khi thực hiện bước lọc dữ liệu.
