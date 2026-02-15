# Partial cancellation

### Hủy sản phẩm lỗi khi kiểm kho tại trạm trung chuyển

Trong mô hình thương mại điện tử, đơn hàng sau khi rời kho người bán sẽ đi qua kho phân loại. Tại đây, nhân viên vận chuyển phát hiện một trong số năm món hàng bị vỡ hỏng. Thay vì trả toàn bộ đơn hàng về cho người bán, hệ thống cho phép nhân viên kho cập nhật trạng thái hủy riêng món hàng lỗi đó. Đơn hàng vẫn tiếp tục hành trình với các món còn lại. Bạn cần xử lý việc cập nhật lại khối lượng kiện hàng và thông báo cho người mua về sự thay đổi này trước khi hàng đến tay họ.

### Khách hàng đổi ý tại cửa hàng trong đơn hàng đa kênh

Một khách hàng đặt mua trực tuyến 3 chiếc áo với kích cỡ khác nhau để thử và chọn hình thức thanh toán trước, nhận hàng tại cửa hàng (Click and Collect). Khi đến cửa hàng, khách thử đồ và quyết định chỉ lấy 2 chiếc, hủy 1 chiếc không vừa ý. Nhân viên cửa hàng thực hiện thao tác hủy một phần ngay trên hệ thống quản lý tại chỗ. Bài toán này yêu cầu bạn thiết kế cách hoàn tiền một phần vào ví điện tử của khách hàng và cập nhật lại tồn kho thực tế của cửa hàng đó ngay lập tức.

### Hoàn trả một phần bộ sản phẩm Combo hoặc Bundle

Hệ thống bán hàng có các gói sản phẩm khuyến mãi, ví dụ mua một bộ gồm bàn phím, chuột và tai nghe với giá ưu đãi thấp hơn mua lẻ. Sau khi nhận hàng, khách hàng muốn trả lại duy nhất chiếc tai nghe vì lý do cá nhân. Việc hủy một phần ở đây trở nên phức tạp vì giá trị của từng món hàng trong Combo đã được chiết khấu theo tỷ lệ. Bạn phải thiết kế logic để tính toán số tiền hoàn lại sao cho công bằng, đồng thời quyết định xem các khuyến mãi đi kèm có còn hiệu lực cho những món còn lại hay không.

### Hủy đơn hàng do nhà cung cấp hết hàng cục bộ

Một đơn hàng thực phẩm trực tuyến bao gồm nhiều nguyên liệu từ các gian hàng khác nhau. Đến giờ chuẩn bị, một gian hàng thông báo hết món rau xanh nhưng các món thịt và gia vị vẫn sẵn sàng. Thay vì hủy cả bữa tối của khách, hệ thống tự động hủy phần sản phẩm hết hàng và tiếp tục điều phối shipper lấy các phần còn lại. Bài toán này tập trung vào việc quản lý trạng thái đơn hàng theo từng đơn vị cung cấp (Sub-order) và tính toán lại phí vận chuyển khi kích thước kiện hàng thay đổi.

### Điều chỉnh số lượng sản phẩm trong đơn hàng dịch vụ lưu trú

Khách hàng đặt phòng khách sạn kèm theo các dịch vụ phụ thêm như 4 suất ăn sáng và 4 vé tham quan bảo tàng. Một ngày trước khi nhận phòng, khách báo giảm số lượng xuống còn 2 suất ăn và 2 vé do có thành viên trong đoàn không tham gia được. Hệ thống cần ghi nhận việc giảm số lượng này thay vì hủy hoàn toàn dịch vụ. Thử thách ở đây là quản lý các phiên bản của đơn hàng và đảm bảo hóa đơn cuối cùng khớp với số lượng thực tế đã sử dụng.

### Hủy sản phẩm trong đơn hàng thanh toán trả góp

Khách hàng mua một danh sách thiết bị điện tử trả góp thông qua công ty tài chính. Sau khi đơn hàng được xác nhận, khách hàng muốn hủy một món đồ trong danh sách đó. Việc này ảnh hưởng trực tiếp đến hợp đồng trả góp đã ký, bao gồm số tiền gốc, tiền lãi hàng tháng và số tiền trả trước. Bạn cần thiết kế hệ thống sao cho khi một phần đơn hàng bị hủy, thông tin sẽ được đồng bộ sang hệ thống của bên tài chính để điều chỉnh lại lịch thanh toán mà không cần làm lại toàn bộ hồ sơ.

### Xử lý đơn hàng bị từ chối một phần khi giao hàng

Trong mô hình giao hàng thực phẩm hoặc hàng tiêu dùng nhanh, khách hàng có quyền kiểm tra hàng khi shipper đến. Khách thấy quả dưa bị dập nên từ chối nhận quả dưa nhưng vẫn lấy các loại thực phẩm khác trong đơn. Shipper cần có công cụ để xác nhận hủy món hàng đó ngay tại điểm giao. Hệ thống cần xử lý luồng tiền mặt (COD) sao cho số tiền khách phải trả khớp với những gì họ giữ lại, đồng thời tạo ra một phiếu nhập kho ảo cho món hàng bị trả về.

### Hủy dòng hàng gắn liền với voucher giảm giá theo ngưỡng tiền

Một đơn hàng có giá trị 1 triệu đồng để được áp dụng mã giảm giá 100 nghìn đồng (cho đơn từ 900 nghìn trở lên). Khách hàng yêu cầu hủy một món hàng trị giá 200 nghìn đồng. Lúc này, tổng giá trị đơn hàng chỉ còn 800 nghìn đồng, không còn đủ điều kiện hưởng voucher ban đầu. Bạn cần thiết kế hệ thống có khả năng tính toán lại toàn bộ bảng giá của các sản phẩm còn lại, thu hồi giá trị voucher đã áp dụng và cập nhật lại số tiền cuối cùng khách phải thanh toán.
