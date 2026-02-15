# Payment reconciliation

### Đối soát giao dịch thành công nhưng hệ thống nội bộ chưa ghi nhận

Đây là bài toán phổ biến nhất khi khách hàng đã bị trừ tiền phía Ngân hàng hoặc Ví điện tử, nhưng do lỗi mạng (Network Timeout) hoặc lỗi xử lý bất đồng bộ, hệ thống của bạn vẫn treo ở trạng thái chờ thanh toán. Bạn cần xây dựng cơ chế để lấy danh sách giao dịch thành công từ Cổng thanh toán, so sánh với các đơn hàng chưa hoàn tất trong cơ sở dữ liệu để cập nhật trạng thái đơn hàng và kích hoạt quy trình giao hàng kịp thời cho khách.

### Xử lý chênh lệch phí giao dịch giữa hệ thống và thực tế

Mỗi giao dịch qua cổng thanh toán thường đi kèm với một mức phí dịch vụ nhất định, có thể là phần trăm cố định hoặc phí cứng trên mỗi giao dịch. Bài toán đặt ra là khi đối soát cuối ngày, tổng số tiền thực nhận (Net Amount) trong báo cáo của Cổng thanh toán không khớp với số tiền dự tính trong hệ thống nội bộ do thay đổi chính sách phí hoặc sai số làm tròn. Hệ thống cần ghi nhận chi tiết từng loại phí để phục vụ báo cáo tài chính và kế toán.

### Đối soát các giao dịch hoàn tiền và hủy đơn

Giao dịch hoàn tiền (Refund) thường có độ trễ lớn và quy trình phức tạp hơn giao dịch thanh toán thông thường. Bài toán yêu cầu bạn quản lý việc đối soát giữa yêu cầu hoàn tiền từ phía chăm sóc khách hàng với danh sách các giao dịch đã thực chi thành công từ phía Cổng thanh toán. Bạn phải đảm bảo rằng một đơn hàng không bị hoàn tiền hai lần và số tiền hoàn lại phải khớp hoàn toàn với số tiền gốc sau khi đã trừ đi các loại phí liên quan nếu có.

### Xử lý giao dịch treo và giao dịch không rõ nguồn gốc

Trong thực tế, sẽ có những trường hợp Cổng thanh toán báo cáo một giao dịch thành công nhưng hệ thống nội bộ hoàn toàn không có thông tin về mã đơn hàng đó (thường do lỗi khởi tạo đơn hàng hoặc lỗi từ phía người dùng). Hệ thống đối soát cần có khả năng phân loại các giao dịch "mồ côi" này vào một danh sách riêng để bộ phận vận hành có thể tra soát thủ công hoặc liên hệ với phía Cổng thanh toán để xác minh danh tính người mua.

### Đối soát theo phiên thanh toán và chu kỳ quyết toán

Các cổng thanh toán không chuyển tiền ngay lập tức sau mỗi giao dịch mà thường gom lại và chuyển theo đợt (Payout) sau một khoảng thời gian như T+1 hoặc T+3. Bài toán này yêu cầu bạn thiết kế hệ thống có khả năng đối soát một mã tham chiếu quyết toán (Settlement ID) với hàng ngàn giao dịch con bên trong. Bạn cần xác định xem số tiền tổng mà Cổng thanh toán chuyển vào tài khoản công ty có khớp với tổng của tất cả các giao dịch lẻ đã thành công trong phiên đó hay không.

### Xử lý xung đột trạng thái do trễ thông báo Webhook

Webhook là phương thức phổ biến để Cổng thanh toán cập nhật trạng thái cho hệ thống của bạn, nhưng thứ tự Webhook gửi đến có thể bị đảo lộn hoặc bị gửi lặp lại nhiều lần (Idempotency). Bài toán yêu cầu thiết kế quy trình đối soát định kỳ để quét lại toàn bộ lịch sử giao dịch trong ngày, nhằm đính chính lại những sai sót nếu Webhook không đến hoặc đến sai thời điểm, đảm bảo trạng thái cuối cùng của giao dịch luôn phản ánh đúng thực tế khách quan.

### Đối soát đa tiền tệ và chênh lệch tỷ giá

Đối với các hệ thống thanh toán quốc tế, khách hàng có thể thanh toán bằng Đô la Mỹ nhưng hệ thống nội bộ hạch toán bằng Đồng Việt Nam. Bài toán thực tế là sự chênh lệch tỷ giá tại thời điểm giao dịch và thời điểm đối soát/quyết toán. Bạn cần thiết kế hệ thống lưu trữ được tỷ giá tại thời điểm phát sinh và tính toán được phần chênh lệch tỷ giá (Gain/Loss) để giải trình với bộ phận kế toán khi số dư cuối kỳ không khớp tuyệt đối.

### Đối soát giữa nhiều bên trung gian thanh toán

Một hệ thống thương mại điện tử lớn thường kết nối với nhiều đối tác như VNPay, MoMo, ShopeePay và các Ngân hàng cùng lúc. Bài toán ở đây là xây dựng một nền tảng đối soát tập trung có khả năng đọc và chuẩn hóa dữ liệu từ nhiều định dạng file khác nhau (CSV, Excel, JSON API) từ các đối tác. Hệ thống phải tạo ra một báo cáo tổng hợp duy nhất, cho biết đối tác nào đang khớp số liệu, đối tác nào đang lệch và nguyên nhân lệch cụ thể là gì.
