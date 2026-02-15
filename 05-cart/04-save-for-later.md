# Save for later

### Quản lý trạng thái sản phẩm giữa Giỏ hàng và Danh sách chờ

Người dùng thường thêm rất nhiều mặt hàng vào giỏ hàng nhưng sau đó nhận ra tổng chi phí quá cao. Thay vì xóa bỏ, họ muốn chuyển các mặt hàng chưa cần thiết ngay lập tức sang một danh sách lưu trữ riêng. Bài toán yêu cầu hệ thống phải xử lý việc di chuyển dữ liệu giữa hai trạng thái này một cách nhất quán, đảm bảo rằng thông tin về số lượng người dùng đã chọn ban đầu vẫn được giữ nguyên khi chuyển qua lại, đồng thời cập nhật chính xác tổng tiền của giỏ hàng hiện hành.

### Đồng bộ giá và khuyến mãi tại thời điểm xem lại

Khi một sản phẩm được chuyển từ giỏ hàng sang danh sách lưu lại, nó có thể nằm ở đó trong vài tuần hoặc vài tháng. Trong khoảng thời gian này, giá của sản phẩm hoặc các chương trình khuyến mãi đính kèm có thể thay đổi. Bài toán đặt ra là làm thế nào để hệ thống ghi nhận giá tại thời điểm lưu nhưng vẫn hiển thị được giá thực tế hiện tại, đồng thời thông báo cho người dùng nếu sản phẩm đó vừa giảm giá hoặc sắp hết hàng để thúc đẩy hành vi mua sắm.

### Phân loại và nhóm sản phẩm lưu trữ theo nhu cầu

Người dùng có xu hướng lưu lại rất nhiều sản phẩm từ các ngành hàng khác nhau như điện tử, quần áo, và đồ gia dụng. Nếu tất cả nằm chung trong một danh sách dài, việc tìm kiếm sẽ rất khó khăn. Bài toán yêu cầu thiết kế khả năng cho phép người dùng tạo các thư mục hoặc gắn nhãn cho danh sách lưu lại. Điều này đòi hỏi cấu trúc dữ liệu phải hỗ trợ quan hệ giữa sản phẩm, người dùng và các thẻ phân loại tùy chỉnh.

### Quản lý biến thể sản phẩm khi lưu trữ lâu dài

Một thách thức lớn là khi người dùng lưu một chiếc áo size L màu xanh, nhưng sau một tháng, phiên bản màu sắc hoặc kích cỡ đó không còn được kinh doanh hoặc thay thế bằng mã sản phẩm mới. Hệ thống cần có cơ chế kiểm tra tính khả dụng của các thuộc tính cụ thể đã lưu. Nếu thuộc tính đó không còn tồn tại, hệ thống phải gợi ý người dùng chọn lại biến thể khác thay vì chỉ thông báo lỗi hoặc xóa mất mục đã lưu của họ.

### Tối ưu hóa hiệu suất truy vấn cho danh sách lưu trữ khổng lồ

Đối với những người dùng có thói quen sưu tầm, danh sách lưu lại mua sau có thể lên đến hàng trăm mục. Khi người dùng mở trang giỏ hàng, việc tải cả giỏ hàng hiện tại và danh sách lưu trữ lớn này cùng một lúc có thể gây chậm trễ. Bài toán này tập trung vào việc thiết kế API và cơ sở dữ liệu sao cho việc phân trang, lười tải dữ liệu và đếm số lượng mặt hàng diễn ra nhanh chóng mà không làm ảnh hưởng đến trải nghiệm thanh toán chính.

### Chuyển đổi hàng loạt giữa các trạng thái

Trong các dịp lễ mua sắm, người dùng muốn nhanh chóng chuyển tất cả sản phẩm từ danh sách lưu lại vào giỏ hàng để áp dụng mã giảm giá tổng thể. Ngược lại, họ cũng có thể muốn dọn dẹp giỏ hàng bằng cách chuyển toàn bộ sang danh sách lưu lại. Bài toán yêu cầu thiết kế các phương thức API hỗ trợ xử lý hàng loạt theo danh sách ID sản phẩm, đảm bảo tính toàn vẹn dữ liệu và xử lý các xung đột về tồn kho ngay lập tức.

### Theo dõi lịch sử thay đổi của danh sách lưu lại

Để phục vụ việc phân tích hành vi người dùng, bộ phận marketing cần biết một sản phẩm đã nằm trong danh sách lưu lại bao lâu trước khi được chuyển ngược vào giỏ hàng và thanh toán. Bài toán yêu cầu lưu trữ các mốc thời gian chuyển đổi giữa giỏ hàng và danh sách lưu, giúp hệ thống có thể tính toán được tỉ lệ chuyển đổi và thời gian chờ trung bình của từng loại mặt hàng cụ thể.

### Chia sẻ danh sách lưu lại cho người dùng khác

Đôi khi người dùng muốn gửi danh sách các sản phẩm họ đang phân vân cho bạn bè hoặc người thân để tham khảo ý kiến trước khi quyết định mua sau. Bài toán này yêu cầu thiết kế hệ thống phân quyền sao cho một danh sách lưu lại có thể được chuyển từ chế độ riêng tư sang chế độ chia sẻ qua một đường dẫn duy nhất, cho phép người khác xem nhưng không thể sửa đổi dữ liệu gốc của chủ sở hữu.
