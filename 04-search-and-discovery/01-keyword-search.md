# Keyword search

### Tìm kiếm sản phẩm đa thuộc tính trên sàn thương mại điện tử

Hệ thống cần xử lý lượng dữ liệu khổng lồ từ nhiều ngành hàng khác nhau như điện tử, thời trang, và gia dụng. Khi người dùng nhập từ khóa, hệ thống không chỉ tìm theo tên sản phẩm mà còn phải lục soát trong mô tả chi tiết, thương hiệu, và các thuộc tính biến thể như màu sắc hay kích cỡ. Thách thức ở đây là làm sao để ưu tiên kết quả có tên sản phẩm trùng khớp cao hơn là các sản phẩm chỉ chứa từ khóa trong phần mô tả dài dòng.

### Hệ thống gợi ý từ khóa thông minh (Search Autocomplete)

Đây là bài toán thiết kế một dịch vụ phản hồi cực nhanh khi người dùng vừa mới gõ những ký tự đầu tiên. Hệ thống phải lưu trữ các cụm từ tìm kiếm phổ biến, xử lý lỗi gõ sai chính tả và hiển thị danh sách gợi ý theo thời gian thực. Dữ liệu cần được tổ chức sao cho việc truy vấn theo tiền tố diễn ra với độ trễ thấp nhất có thể, đồng thời phải có cơ chế cập nhật xu hướng tìm kiếm hàng giờ.

### Tìm kiếm tin tức và bài báo theo thời gian thực

Hệ thống lưu trữ hàng triệu bài viết từ nhiều nguồn khác nhau. Người dùng muốn tìm kiếm các sự kiện nóng hổi vừa xảy ra. Bài toán yêu cầu thiết kế chỉ mục sao cho các bài viết mới xuất hiện phải được đưa vào kết quả tìm kiếm ngay lập tức. Ngoài việc khớp từ khóa, hệ thống cần có cơ chế xếp hạng dựa trên độ tươi mới của thông tin và uy tín của nguồn tin.

### Tra cứu phụ tùng kỹ thuật trong kho linh kiện

Trong một kho hàng công nghiệp, sản phẩm thường có tên gọi phức tạp, mã SKU dài và các thông số kỹ thuật khô khan. Người dùng có thể tìm theo mã số, tên linh kiện hoặc công dụng của chúng. Bài toán này tập trung vào việc thiết kế cơ sở dữ liệu hỗ trợ tìm kiếm chính xác tuyệt đối và tìm kiếm mờ khi người dùng nhớ nhầm mã số, đồng thời phải hiển thị được trạng thái còn hàng hay hết hàng tại từng kho cụ thể.

### Tìm kiếm khóa học trực tuyến dựa trên kỹ năng

Người dùng nhập các kỹ năng họ muốn học vào thanh tìm kiếm. Hệ thống phải quét qua tiêu đề khóa học, nội dung các bài giảng video, tên giảng viên và cả các đánh giá của học viên cũ. Kết quả trả về cần được phân loại theo cấp độ từ cơ bản đến nâng cao. Điểm khó ở đây là thiết kế API và Database sao cho có thể lọc nhanh kết quả theo khoảng giá, thời lượng học và đánh giá sao ngay sau khi có danh sách kết quả từ khóa.

### Hệ thống tìm kiếm địa điểm và món ăn trên ứng dụng giao hàng

Bài toán này kết hợp giữa tìm kiếm từ khóa văn bản và dữ liệu không gian. Khi người dùng nhập tên món ăn, hệ thống phải tìm các cửa hàng có bán món đó nhưng chỉ ưu tiên hiển thị những địa điểm nằm trong bán kính gần với vị trí hiện tại của người dùng. Việc thiết kế Database cần chú ý đến việc kết hợp giữa chỉ mục văn bản và chỉ mục địa lý để đảm bảo tốc độ phản hồi.

### Tìm kiếm tài liệu nội bộ trong doanh nghiệp (Enterprise Search)

Hệ thống cho phép nhân viên tìm kiếm các tệp tin, biên bản họp, và hợp đồng. Đặc thù của bài toán này là vấn đề phân quyền. Khi người dùng tìm kiếm một từ khóa, hệ thống chỉ được phép trả về những tài liệu mà người đó có quyền xem. Điều này đòi hỏi thiết kế hệ thống quyền hạn phức tạp lồng ghép trực tiếp vào các câu lệnh truy vấn tìm kiếm để đảm bảo bảo mật dữ liệu.

### Tìm kiếm và lọc sản phẩm cũ trên sàn đồ đã qua sử dụng

Người dùng tìm kiếm các mặt hàng thanh lý dựa trên từ khóa về tình trạng sản phẩm, khu vực địa lý và khoảng giá. Do đặc điểm là hàng cũ, mỗi sản phẩm thường là duy nhất. Hệ thống cần xử lý việc cập nhật chỉ mục tìm kiếm liên tục vì sản phẩm sẽ bị ẩn ngay sau khi có người mua. Bài toán này giúp bạn thực hành thiết kế hệ thống có tần suất ghi và xóa dữ liệu vào chỉ mục tìm kiếm rất cao.
