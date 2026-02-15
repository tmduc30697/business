# Payment retry

### Xử lý tranh chấp dữ liệu khi người dùng nhấn nút thử lại liên tục

Trong giao diện người dùng, khi một giao dịch đang ở trạng thái chờ kết quả từ phía ngân hàng, người dùng có thể mất kiên nhẫn và nhấn nút thanh toán lại nhiều lần trong thời gian ngắn. Bài toán yêu cầu hệ thống phải kiểm soát được tính nhất quán để không tạo ra hai yêu cầu thanh toán song song cho cùng một đơn hàng. Bạn cần thiết kế cơ chế để ghi nhận trạng thái của yêu cầu đầu tiên và ngăn chặn các yêu cầu tiếp theo nếu yêu cầu trước đó chưa thực sự thất bại hoặc vẫn đang trong quá trình xử lý (Idempotency).

### Cơ chế Retry tự động cho các gói đăng ký dịch vụ định kỳ

Đối với các mô hình kinh doanh đăng ký trả phí hàng tháng như Netflix hay Spotify, khi đến hạn thanh toán mà thẻ của khách hàng bị từ chối do hết hạn hoặc không đủ số dư, hệ thống không nên hủy gói ngay lập tức. Bài toán đặt ra là thiết kế một lịch trình thử lại tự động theo các khoảng thời gian tăng dần, ví dụ thử lại sau 1 giờ, 1 ngày, hoặc 3 ngày. Bạn cần lưu trữ lịch sử các lần thử, mã lỗi trả về từ cổng thanh toán để quyết định có nên tiếp tục thử lại hay yêu cầu người dùng cập nhật phương thức thanh toán mới.

### Chuyển đổi thông minh giữa các cổng thanh toán khi xảy ra lỗi hệ thống

Một hệ thống thương mại điện tử lớn thường kết nối với nhiều cổng thanh toán khác nhau như VNPay, Momo, hoặc Stripe. Khi người dùng thanh toán thất bại ở cổng A do lỗi kỹ thuật của nhà cung cấp, hệ thống cần cung cấp tùy chọn hoặc tự động điều hướng người dùng thử lại bằng cổng B mà vẫn giữ nguyên thông tin đơn hàng. Bài toán này tập trung vào việc thiết kế cấu trúc dữ liệu để theo dõi vết giao dịch xuyên suốt qua nhiều nhà cung cấp khác nhau và đối soát dữ liệu sau này.

### Quản lý trạng thái kho hàng trong quá trình chờ thanh toán lại

Khi một giao dịch thất bại và người dùng đang thực hiện thanh toán lại, vấn đề giữ chỗ hàng hóa trong kho trở nên phức tạp. Nếu hệ thống giải phóng hàng ngay khi giao dịch thất bại, người dùng khác có thể mua mất sản phẩm đó trong lúc người dùng cũ đang nhập lại mã OTP. Bài toán yêu cầu thiết kế một cơ chế giữ hàng có thời hạn (TTL) và đồng bộ trạng thái kho với các phiên thanh toán lại để đảm bảo trải nghiệm mua sắm không bị gián đoạn nhưng cũng không gây ra tình trạng tồn kho ảo.

### Phân tích nguyên nhân thất bại để gợi ý phương thức thử lại phù hợp

Không phải mọi lỗi thanh toán đều giống nhau. Có những lỗi có thể thử lại ngay như lỗi mạng, nhưng có những lỗi không nên thử lại bằng cùng một phương thức như thẻ bị khóa hoặc sai thông tin chủ thẻ. Bài toán yêu cầu hệ thống phải phân loại được mã lỗi trả về từ ngân hàng, lưu trữ vào cơ sở dữ liệu và trả về chỉ dẫn cụ thể cho người dùng trên API. Việc này giúp hệ thống quyết định hiển thị nút Thử lại ngay hay nút Chọn phương thức thanh toán khác cho người dùng.

### Hệ thống thông báo và nhắc nhở thanh toán lại qua nhiều kênh

Khi giao dịch thất bại trên ứng dụng di động nhưng người dùng đã thoát ứng dụng, hệ thống cần có cơ chế gửi thông báo đẩy hoặc email kèm theo một đường dẫn định danh để người dùng quay lại đúng trang thanh toán đó. Bài toán này yêu cầu thiết kế các Token thanh toán có thời hạn và liên kết chặt chẽ với ID giao dịch cũ. Bạn cần giải quyết việc khôi phục lại giỏ hàng và trạng thái thanh toán từ một liên kết bên ngoài ứng dụng mà vẫn đảm bảo tính bảo mật.

### Đối soát dữ liệu và xử lý thanh toán trùng lặp sau khi Retry

Trong một số trường hợp hy hữu, giao dịch đầu tiên tưởng chừng thất bại nhưng thực tế tiền vẫn bị trừ sau đó do độ trễ của ngân hàng, trong khi người dùng đã thực hiện thử lại thành công ở lần thứ hai. Bài toán yêu cầu thiết kế hệ thống đối soát (Reconciliation) để phát hiện các trường hợp một đơn hàng có hai giao dịch thành công. Bạn cần xây dựng quy trình ghi nhận log chi tiết, ID tham chiếu phía ngân hàng và quy trình hoàn tiền tự động cho các giao dịch dư thừa này.

### Giới hạn số lần thử lại để ngăn chặn tấn công giả mạo thanh toán

Việc cho phép thử lại vô hạn có thể bị kẻ xấu lợi dụng để dò tìm thông tin thẻ hoặc thực hiện các cuộc tấn công từ chối dịch vụ vào cổng thanh toán. Bài toán đặt ra yêu cầu thiết kế cơ chế Rate Limiting dựa trên ID người dùng hoặc địa chỉ IP cho các yêu cầu thanh toán lại. Bạn cần lưu trữ số lần thử thất bại liên tiếp vào bộ nhớ đệm và thiết kế logic khóa tạm thời tính năng thanh toán của người dùng nếu vượt quá ngưỡng cho phép để bảo vệ hệ thống.
