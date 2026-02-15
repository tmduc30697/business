# Payment timeout

### Giữ chỗ vé máy bay và dịch vụ du lịch

Trong hệ thống đặt vé máy bay, khi người dùng chọn chỗ ngồi, hệ thống cần tạm khóa ghế đó để tránh tình trạng trùng lặp. Bài toán đặt ra là nếu người dùng không thanh toán trong vòng mười lăm phút, ghế phải được giải phóng để hành khách khác có thể đặt. Việc này đòi hỏi hệ thống phải quản lý trạng thái giữ chỗ nghiêm ngặt, xử lý các trường hợp thanh toán trễ do lỗi mạng và đảm bảo tính nhất quán giữa dữ liệu ghế ngồi với trạng thái giao dịch.

### Mua sắm hàng giới hạn trong các đợt Flash Sale

Các trang thương mại điện tử thường tổ chức các sự kiện bán sản phẩm số lượng có hạn với giá ưu đãi. Hệ thống cần giữ hàng trong giỏ cho khách trong một khoảng thời gian ngắn, ví dụ năm phút. Nếu quá thời hạn này mà hóa đơn chưa được xác nhận thanh toán, số lượng tồn kho của sản phẩm đó phải được hoàn trả ngay lập tức. Thử thách ở đây là xử lý lượng truy cập cực lớn đồng thời cùng lúc và đảm bảo hệ thống kiểm tra thời hạn thanh toán hoạt động chính xác đến từng giây.

### Đặt đồ ăn và gọi xe trực tuyến

Khi một đơn hàng được tạo trên ứng dụng giao đồ ăn, nhà hàng chỉ bắt đầu chế biến khi tiền đã được chuyển hoặc giao dịch được xác thực. Hệ thống yêu cầu khách hàng hoàn tất thanh toán trong vòng mười phút kể từ khi gửi đơn. Nếu quá hạn, đơn hàng sẽ tự động chuyển sang trạng thái hủy để tránh việc nhà hàng chuẩn bị đồ ăn mà không có người nhận. Bạn cần thiết kế cách hệ thống thông báo cho cả khách hàng và nhà hàng về sự thay đổi trạng thái này theo thời gian thực.

### Thanh toán hóa đơn tiện ích định kỳ

Đối với các dịch vụ như tiền điện, tiền nước hoặc cước internet, hệ thống thường tạo ra một mã thanh toán tạm thời hoặc mã QR động có thời hạn sử dụng. Nếu người dùng không thực hiện quét mã và thanh toán trong vòng hai mươi bốn giờ, mã đó sẽ hết hiệu lực và đơn thanh toán bị đóng. Bài toán này tập trung vào việc quản lý vòng đời của các mã thanh toán và cách hệ thống đối soát dữ liệu từ ngân hàng trả về sau khi mã đã hết hạn trên hệ thống nội bộ.

### Đăng ký tham gia giải chạy marathon hoặc sự kiện lớn

Tại các giải chạy lớn, số lượng suất đăng ký thường hết rất nhanh. Khi người dùng điền xong thông tin cá nhân, hệ thống cho phép họ có ba mươi phút để hoàn tất lệ phí thi đấu. Nếu không thanh toán đúng hạn, suất đó sẽ được nhường cho những người trong danh sách chờ. Hệ thống cần cơ chế tự động quét các đơn hàng quá hạn và thực hiện quy trình chuyển giao suất đăng ký cho người tiếp theo một cách công bằng.

### Thuê phim hoặc nội dung số trực tuyến

Trên các nền tảng xem phim trả phí, khi người dùng chọn thuê một bộ phim lẻ, họ có một khoảng thời gian nhất định để thực hiện giao dịch. Nếu sau ba tiếng kể từ lúc bắt đầu lệnh thuê mà chưa có tín hiệu thanh toán thành công từ cổng thanh toán, quyền truy cập tạm thời vào bộ phim sẽ bị thu hồi. Việc này đòi hỏi thiết kế hệ thống có khả năng kiểm tra quyền truy cập dựa trên mốc thời gian của giao dịch cuối cùng.

### Đấu giá tài sản trực tuyến

Trong các phiên đấu giá, người thắng cuộc có một khoảng thời gian quy định, chẳng hạn như bốn mươi tám giờ, để thanh toán toàn bộ số tiền đã trả giá. Nếu quá thời gian này, kết quả đấu giá sẽ bị hủy bỏ, người mua mất tiền đặt cọc và tài sản được chuyển trạng thái để đấu giá lại hoặc giao cho người trả giá cao thứ hai. Bài toán này phức tạp ở chỗ phải xử lý nhiều điều kiện ràng buộc về tiền đặt cọc, phí phạt và thay đổi chủ sở hữu tài sản.

### Nạp tiền vào tài khoản trò chơi trực tuyến

Người chơi game thường nạp tiền qua các cổng thanh toán trung gian để mua vật phẩm. Khi một yêu cầu nạp tiền được tạo ra, hệ thống sẽ chờ phản hồi xác nhận từ nhà mạng hoặc ngân hàng. Nếu trong vòng một giờ không nhận được tín hiệu thành công, yêu cầu nạp sẽ bị đánh dấu là thất bại. Hệ thống cần một cơ chế để xử lý các trường hợp thanh toán thành công muộn, tức là tiền đã trừ khỏi tài khoản người dùng nhưng hệ thống game đã lỡ chuyển đơn hàng sang trạng thái hủy do quá thời gian chờ.
