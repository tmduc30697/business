# Product image upload

### Tối ưu hóa thứ tự hiển thị và ảnh đại diện

Trong một hệ thống thương mại điện tử, mỗi sản phẩm thường có một ảnh chính làm đại diện và nhiều ảnh phụ để mô tả chi tiết. Vấn đề đặt ra là làm sao để lưu trữ thông tin sao cho hệ thống luôn biết đâu là ảnh quan trọng nhất để hiển thị ở trang danh sách, đồng thời cho phép người quản trị thay đổi thứ tự sắp xếp của các ảnh phụ một cách linh hoạt. Bài toán này đòi hỏi việc thiết kế bảng sao cho thao tác truy vấn ảnh chính đạt tốc độ cao nhất và việc cập nhật vị trí các ảnh không gây xung đột dữ liệu.

### Quản lý biến thể sản phẩm đa dạng

Nhiều sản phẩm như quần áo hoặc giày dép có nhiều phiên bản khác nhau về màu sắc. Mỗi màu sắc lại cần một bộ sưu tập hình ảnh riêng biệt để người dùng không bị nhầm lẫn khi chọn mua. Bài toán yêu cầu thiết kế cấu trúc dữ liệu để liên kết chính xác nhóm hình ảnh với từng biến thể cụ thể, thay vì chỉ gắn ảnh vào sản phẩm cha. Điều này giúp khi khách hàng bấm chọn màu đỏ, toàn bộ album ảnh của sản phẩm sẽ tự động chuyển sang các góc chụp của phiên bản màu đỏ đó.

### Lưu trữ đa phiên bản và kích thước hình ảnh

Để tối ưu tốc độ tải trang trên các thiết bị khác nhau, một hình ảnh gốc sau khi tải lên thường được hệ thống tự động cắt và nén thành nhiều phiên bản như ảnh nhỏ cho danh mục, ảnh vừa cho trang chi tiết và ảnh lớn để phóng to. Bài toán đặt ra là quản lý danh sách các đường dẫn của các phiên bản này sao cho ứng dụng phía khách hàng có thể dễ dàng lấy đúng kích cỡ cần thiết mà không phải xử lý logic phức tạp, đồng thời đảm bảo việc xóa ảnh gốc sẽ kéo theo việc dọn dẹp tất cả các phiên bản phái sinh.

### Kiểm soát quyền truy cập và bảo mật hình ảnh

Một số sàn thương mại điện tử cần bảo vệ bản quyền hình ảnh bằng cách đóng dấu mờ hoặc chỉ cho phép xem ảnh chất lượng cao sau khi đăng nhập. Bài toán yêu cầu thiết kế hệ thống quản lý trạng thái của hình ảnh, bao gồm các thông tin về quyền sở hữu và các khóa bảo mật tạm thời. Hệ thống cần ghi nhận được ai là người đã tải lên, thời gian tải và tình trạng kiểm duyệt của hình ảnh trước khi nó được xuất hiện công khai trên website.

### Đồng bộ hóa hình ảnh từ các nguồn bên ngoài

Nhiều người bán hàng thường lấy dữ liệu sản phẩm từ kho của nhà cung cấp hoặc các sàn giao dịch khác thông qua đường dẫn URL thay vì tải trực tiếp file lên. Bài toán thực tế là thiết kế một cơ chế quản lý hình ảnh hỗ trợ cả hai hình thức: lưu trữ file vật lý trên server nội bộ và lưu trữ liên kết từ server bên ngoài. Hệ thống phải có khả năng kiểm tra tính khả dụng của các liên kết này và có phương án dự phòng nếu hình ảnh từ link bên ngoài bị xóa hoặc lỗi.

### Xử lý tải lên hàng loạt và trạng thái tiến trình

Khi người dùng tải lên hàng chục hình ảnh cùng lúc cho một bộ sưu tập sản phẩm, việc xử lý đồng bộ có thể gây treo ứng dụng hoặc mất kết nối giữa chừng. Bài toán yêu cầu thiết kế một quy trình quản lý trạng thái tải lên, cho phép ghi nhận những ảnh nào đã thành công, ảnh nào thất bại và lý do lỗi. Điều này hỗ trợ việc thiết kế các API dạng bất đồng bộ và giúp giao diện người dùng hiển thị được thanh tiến trình một cách chính xác nhất.

### Quản lý dung lượng và giới hạn tài nguyên

Để tránh việc người dùng lạm dụng tài nguyên máy chủ bằng cách tải lên các file ảnh quá lớn hoặc quá nhiều ảnh cho một sản phẩm, hệ thống cần một cơ chế kiểm soát chặt chẽ. Bài toán cần xác định cách lưu trữ thông tin về dung lượng của từng file, tổng số lượng ảnh hiện có của mỗi người dùng và thực hiện đối soát với các hạn mức được cấu hình sẵn. Việc này rất quan trọng cho việc tính toán chi phí lưu trữ và tối ưu hóa hiệu suất của hệ thống lưu trữ đám mây.

### Lưu trữ lịch sử thay đổi và phục hồi hình ảnh

Trong quá trình quản lý, người dùng có thể vô tình xóa nhầm ảnh hoặc muốn quay lại phiên bản ảnh cũ trước khi chỉnh sửa. Bài toán đặt ra là thiết kế một hệ thống không xóa cứng dữ liệu ngay lập tức mà sử dụng cơ chế xóa mềm hoặc lưu trữ các phiên bản lịch sử. Hệ thống cần ghi lại các hành động thay đổi hình ảnh để phục vụ mục đích kiểm soát và cho phép khôi phục lại dữ liệu trong một khoảng thời gian nhất định nếu cần thiết.
