# Image review

### Quản lý phiên bản hình ảnh và kiểm duyệt tự động

Trong các hệ thống thương mại điện tử lớn, hình ảnh người dùng tải lên không được hiển thị ngay lập tức mà phải đi qua một quy trình kiểm duyệt. Bài toán yêu cầu thiết kế hệ thống lưu trữ trạng thái của từng hình ảnh như đang chờ duyệt, đã chấp nhận hoặc bị từ chối do vi phạm chính sách. Khi hình ảnh bị từ chối, hệ thống cần lưu lại lý do cụ thể để phản hồi cho người dùng. Ngoài ra, để tối ưu hóa trải nghiệm, hệ thống cần tự động tạo ra các phiên bản thu nhỏ với kích thước khác nhau từ hình ảnh gốc ngay khi quá trình tải lên hoàn tất.

### Phân loại hình ảnh theo tiêu chí đánh giá sản phẩm

Thay vì chỉ tải ảnh lên một cách chung chung, một số nền tảng yêu cầu người dùng gắn thẻ hình ảnh vào các tiêu chí cụ thể như chất lượng bao bì, ngoại hình sản phẩm hoặc hiệu năng sử dụng thực tế. Bài toán này đòi hỏi việc thiết kế cấu trúc dữ liệu sao cho một đánh giá có thể chứa nhiều hình ảnh, và mỗi hình ảnh lại liên kết với một hoặc nhiều danh mục phân loại khác nhau. Việc này giúp người mua sau có thể lọc nhanh các đánh giá chỉ xem ảnh về thực tế sử dụng thay vì ảnh chụp vỏ hộp.

### Hệ thống tương tác và phản hồi trên hình ảnh đánh giá

Để tăng tính minh bạch và tin cậy, các hình ảnh trong đánh giá thường cho phép người dùng khác vào tương tác. Bài toán đặt ra là thiết kế các tính năng như nhấn thích hình ảnh, báo cáo hình ảnh vi phạm hoặc thậm chí là phản hồi trực tiếp vào một bức ảnh cụ thể trong bộ sưu tập của người đánh giá. Hệ thống cần ghi nhận lịch sử tương tác của từng tài khoản để tránh việc gian lận lượt thích hoặc gửi báo cáo rác liên tục từ một người dùng.

### Đồng bộ hóa hình ảnh giữa đánh giá và thư viện ảnh sản phẩm

Nhiều nền tảng muốn tận dụng hình ảnh thực tế từ khách hàng để làm phong phú thêm bộ sưu tập ảnh của trang chi tiết sản phẩm. Bài toán yêu cầu thiết kế logic để khi một hình ảnh đánh giá đạt đủ số lượt tin tưởng hoặc được quản trị viên đánh dấu là ảnh chất lượng cao, nó sẽ được hiển thị ở một khu vực riêng gọi là thư viện ảnh từ khách hàng. Hệ thống cần quản lý được nguồn gốc của ảnh để khi người dùng xóa đánh giá gốc, hình ảnh đó cũng phải được xử lý tương ứng trong thư viện chung.

### Tối ưu hóa dung lượng và phân phối ảnh qua CDN

Khi số lượng đánh giá kèm hình ảnh lên tới hàng triệu, chi phí lưu trữ và tốc độ tải trang trở thành vấn đề lớn. Bài toán tập trung vào việc thiết kế API tải ảnh lên sao cho có thể tích hợp với các dịch vụ lưu trữ đám mây bên thứ ba. Bạn cần giải quyết việc lưu trữ đường dẫn ảnh, quản lý metadata của ảnh như dung lượng, định dạng và thông tin thiết bị chụp. Hệ thống cũng cần có cơ chế để sinh ra các đường dẫn tạm thời có thời hạn hoặc các đường dẫn đã qua bộ lọc CDN để tối ưu hóa tốc độ truy cập theo vị trí địa lý.

### Tìm kiếm và lọc đánh giá dựa trên nội dung hình ảnh

Người dùng thường có nhu cầu chỉ xem các đánh giá có hình ảnh để tiết kiệm thời gian kiểm chứng. Bài toán này yêu cầu thiết kế cơ sở dữ liệu và các câu truy vấn sao cho việc lọc các đánh giá có chứa tệp đính kèm được thực hiện nhanh nhất. Cao cấp hơn, hệ thống cần lưu trữ các kết quả phân tích từ trí tuệ nhân tạo như màu sắc chủ đạo của ảnh hoặc các vật thể xuất hiện trong ảnh để hỗ trợ tính năng tìm kiếm đánh giá theo hình ảnh tương đồng.

### Quản lý quyền sở hữu và bảo vệ bản quyền hình ảnh

Để tránh việc đối thủ cạnh tranh lấy ảnh đánh giá của khách hàng này để đăng cho sản phẩm khác, hệ thống cần tích hợp cơ chế đóng dấu ảnh tự động. Bài toán yêu cầu thiết kế luồng xử lý ảnh từ lúc người dùng tải lên, hệ thống sẽ chèn logo hoặc mã định danh của cửa hàng vào ảnh trước khi lưu trữ chính thức. Ngoài ra, cần quản lý quyền sở hữu để người dùng có thể chỉnh sửa hoặc xóa ảnh của chính họ mà không làm ảnh hưởng đến tính toàn vẹn dữ liệu của các bảng thống kê liên quan.

### Thống kê và xếp hạng người dùng đóng góp nội dung hình ảnh

Để khuyến khích người dùng chụp ảnh thực tế, hệ thống cần có cơ chế tích điểm hoặc trao danh hiệu cho những người thường xuyên đăng tải hình ảnh chất lượng. Bài toán yêu cầu thiết kế các bảng thống kê ghi lại số lượng ảnh đã đăng, tổng số lượt yêu thích nhận được từ ảnh và tỉ lệ ảnh được quản trị viên phê duyệt. Dữ liệu này sẽ được dùng để tính toán thứ hạng người dùng và hiển thị các huy hiệu uy tín bên cạnh tên của họ trong phần đánh giá sản phẩm.
