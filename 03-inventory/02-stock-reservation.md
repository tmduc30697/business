# Stock reservation

### Giữ hàng trong giỏ hàng có thời hạn cố định

Đây là bài toán cơ bản nhất thường thấy ở các trang web đặt vé máy bay hoặc mua đồ hiệu giảm giá số lượng giới hạn. Khi khách hàng nhấn nút thêm vào giỏ hàng, hệ thống sẽ tạm giữ sản phẩm đó trong khoảng mười lăm phút. Nếu trong thời gian này khách hàng không tiến hành thanh toán, số lượng hàng này sẽ tự động được giải phóng ngược lại kho để người khác có thể mua. Thử thách ở đây là làm sao để xử lý hàng ngàn giỏ hàng hết hạn cùng lúc mà không làm treo hệ thống.

### Xử lý sự kiện Flash Sale với lượng truy cập đột biến

Trong các sự kiện giảm giá lớn, có hàng chục ngàn người cùng nhấn nút mua một sản phẩm chỉ có số lượng tồn kho là một trăm. Hệ thống cần một cơ chế giữ hàng cực nhanh ở tầng cache trước khi ghi xuống cơ sở dữ liệu chính thức. Bài toán này yêu cầu thiết kế cách kiểm tra tồn kho và tạm giữ sao cho không xảy ra tình trạng bán quá số lượng thực tế nhưng vẫn đảm bảo tốc độ phản hồi dưới một giây cho người dùng.

### Giữ hàng theo nhiều trạng thái của đơn hàng

Trong quy trình vận hành thực tế, việc giữ hàng không chỉ dừng lại ở lúc nhấn mua. Hàng cần được giữ từ khi đơn hàng ở trạng thái chờ thanh toán, sau đó chuyển sang trạng thái đang đóng gói, và chỉ thực sự trừ kho vật lý khi đơn hàng đã rời kho. Nếu khách hàng hủy đơn ở bất kỳ bước nào trước khi giao, số lượng hàng giữ phải được hoàn lại đúng vị trí cũ. Việc thiết kế các trạng thái này đòi hỏi sự chính xác tuyệt đối trong database để tránh thất thoát.

### Quản lý tồn kho ảo cho các chiến dịch marketing

Đôi khi chủ cửa hàng muốn dành riêng một phần kho cho các kênh bán hàng khác nhau, ví dụ giữ lại năm mươi chiếc cho livestream trên TikTok và một trăm chiếc cho website. Dù thực tế hàng nằm chung một kho vật lý, nhưng hệ thống giữ hàng phải tách biệt được các "pool" này. Khi khách hàng thêm vào giỏ từ nguồn nào thì hệ thống chỉ được phép tạm giữ trong phạm vi số lượng đã phân bổ cho nguồn đó, tránh việc kênh này chiếm dụng hết hàng của kênh kia.

### Giữ hàng cho các sản phẩm combo hoặc bộ sưu tập

Khi khách hàng mua một bộ sản phẩm gồm áo, quần và thắt mắt, việc tạm giữ hàng trở nên phức tạp hơn vì hệ thống phải kiểm tra và giữ cùng lúc cả ba mặt hàng riêng lẻ. Nếu một trong ba món hết hàng, việc giữ hàng cho hai món còn lại phải bị hủy bỏ để tránh tình trạng đơn hàng không thể hoàn tất nhưng vẫn chiếm dụng tồn kho của các sản phẩm lẻ. Điều này đòi hỏi thiết kế logic ràng buộc chặt chẽ giữa các bảng ghi giữ hàng.

### Ưu tiên giữ hàng cho khách hàng thân thiết

Một số hệ thống bán lẻ cao cấp áp dụng chính sách ưu tiên cho khách hàng VIP. Khi kho hàng chỉ còn số lượng ít, nếu một khách hàng VIP và một khách hàng mới cùng thêm hàng vào giỏ, hệ thống có thể cho phép khách hàng VIP "ghi đè" hoặc được ưu tiên giữ chỗ lâu hơn. Bài toán này yêu cầu thiết kế thêm các tầng logic về phân quyền và trọng số ưu tiên trong bảng dữ liệu tạm giữ hàng thay vì chỉ áp dụng quy tắc ai đến trước phục vụ trước.

### Giữ hàng tại các chi nhánh kho gần vị trí người mua

Trong mô hình bán hàng đa kho, hệ thống không chỉ giữ hàng dựa trên số lượng tổng mà còn phải giữ tại đúng kho vật lý gần địa chỉ của khách hàng nhất. Khi khách hàng thêm vào giỏ, hệ thống cần định vị kho dự kiến sẽ xuất hàng và thực hiện lệnh giữ hàng tại kho đó. Nếu kho đó hết hàng nhưng kho khác vẫn còn, hệ thống phải tính toán xem có nên giữ hàng ở kho xa hơn hay không, dẫn đến việc quản lý tọa độ và logic phân vùng trong thiết kế hệ thống.

### Xử lý tranh chấp giữ hàng khi thanh toán thất bại

Một vấn đề nhức nhối là khi khách hàng đã đi đến bước thanh toán cuối cùng nhưng thẻ bị lỗi hoặc hết tiền. Lúc này, hệ thống thường giữ hàng thêm một khoảng thời gian ngắn để khách hàng thử lại bằng phương thức khác. Tuy nhiên, nếu giữ quá lâu sẽ làm mất cơ hội của người mua khác. Bài toán đặt ra là thiết kế cơ chế gia hạn thời gian giữ hàng linh hoạt dựa trên phản hồi từ các cổng thanh toán quốc tế và nội địa.
