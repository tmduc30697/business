# Wallet top-up

### Xử lý giao dịch nạp tiền qua nhiều cổng thanh toán khác nhau

Hệ thống cần tích hợp với nhiều đối tác như VNPay, MoMo, hoặc thẻ Visa/Mastercard. Mỗi đối tác sẽ có quy trình phản hồi kết quả khác nhau (callback hoặc redirect). Bạn cần thiết kế cách lưu trữ để quản lý trạng thái giao dịch từ lúc người dùng khởi tạo yêu cầu, gửi sang bên thứ ba, cho đến khi nhận được xác nhận thành công hoặc thất bại để cộng tiền vào ví.

### Quản lý số dư và tính nhất quán dữ liệu khi nạp tiền

Khi một giao dịch nạp tiền được xác nhận thành công, hệ thống phải cập nhật số dư ví của người dùng. Bài toán đặt ra là làm sao để đảm bảo việc cộng tiền diễn ra chính xác một lần duy nhất (idempotency), tránh việc người dùng nhấn nạp một lần nhưng hệ thống xử lý trùng lặp dẫn đến cộng tiền hai lần, hoặc xảy ra lỗi tranh chấp dữ liệu khi có nhiều luồng xử lý cùng lúc.

### Hệ thống khuyến mãi và hoàn tiền khi nạp tiền vào ví

Để thu hút người dùng, nền tảng thường có các chương trình như nạp tiền lần đầu được tặng thêm tiền hoặc nạp tiền vào khung giờ vàng để nhận voucher. Bạn cần thiết kế logic để kiểm tra điều kiện áp dụng khuyến mãi, tính toán số tiền thưởng thực tế và lưu vết rõ ràng đâu là tiền gốc người dùng nạp, đâu là tiền thưởng trong lịch sử giao dịch.

### Kiểm soát hạn mức nạp tiền và định danh người dùng

Dựa trên quy định pháp luật hoặc chính sách rủi ro, mỗi tài khoản sẽ có hạn mức nạp tiền tối đa trong ngày hoặc trong tháng tùy theo cấp độ định danh (KYC). Hệ thống cần kiểm tra tổng giá trị các giao dịch đã thực hiện trong một khoảng thời gian trước khi cho phép tạo giao dịch mới, đồng thời ngăn chặn các hành vi nạp tiền vượt ngưỡng cho phép.

### Đối soát dữ liệu định kỳ với các đối tác thanh toán

Thực tế luôn có sự chênh lệch giữa dữ liệu tại hệ thống ví và dữ liệu tại phía ngân hàng hoặc cổng thanh toán do lỗi mạng hoặc timeout. Bài toán yêu cầu thiết kế một quy trình đối soát (reconciliation) để so khớp các mã giao dịch, số tiền và trạng thái giữa hai bên, từ đó phát hiện ra các giao dịch treo để xử lý bù hoặc hoàn tiền tự động.

### Quản lý phí giao dịch nạp tiền theo từng phương thức

Mỗi phương thức nạp tiền sẽ có mức phí khác nhau (ví dụ nạp qua thẻ nội địa miễn phí nhưng nạp qua thẻ tín dụng mất phí phần trăm). Hệ thống cần có khả năng cấu hình phí linh hoạt, hiển thị phí dự kiến cho người dùng trước khi nạp và tách biệt rõ ràng giữa số tiền người dùng thực nạp, phí giao dịch và số tiền thực nhận vào số dư ví.

### Xây dựng luồng phê duyệt thủ tục nạp tiền cho doanh nghiệp

Đối với các tài khoản doanh nghiệp hoặc đại lý nạp số tiền lớn, giao dịch không được thực hiện tự động mà phải qua bước phê duyệt của quản trị viên. Bạn cần thiết kế luồng trạng thái từ chờ duyệt, đang xử lý đến hoàn tất, kèm theo việc lưu trữ bằng chứng chuyển khoản (hình ảnh hoặc mã tham chiếu ngân hàng) để nhân viên vận hành có cơ sở xác nhận.

### Theo dõi lịch sử và biến động số dư chi tiết

Người dùng cần một màn hình hiển thị danh sách các giao dịch nạp tiền với đầy đủ thông tin về thời gian, phương thức sử dụng, trạng thái và đặc biệt là số dư trước và sau khi thay đổi. Điều này yêu cầu cách thiết kế bảng lịch sử giao dịch (audit log) sao cho tối ưu hóa việc truy vấn nhưng vẫn đảm bảo tính bảo mật và không thể bị sửa đổi trái phép.
