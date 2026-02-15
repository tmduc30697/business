# Full refund

### Quản lý hoàn tiền lỗi sản phẩm trên sàn thương mại điện tử

Người mua nhận được hàng nhưng sản phẩm bị vỡ hoặc không đúng mô tả nên yêu cầu hoàn trả toàn bộ số tiền. Hệ thống cần ghi nhận lý do hoàn tiền, hình ảnh bằng chứng từ khách hàng và trạng thái phê duyệt từ người bán. Khi đơn hàng chuyển sang trạng thái đã hoàn tiền, toàn bộ số tiền bao gồm giá trị sản phẩm và phí vận chuyển ban đầu phải được tính toán để trả lại cho ví điện tử của khách.

### Xử lý hoàn tiền tự động khi hủy đơn hàng chưa giao

Khách hàng đặt một đơn hàng đồ ăn trên ứng dụng nhưng sau đó muốn hủy đơn ngay lập tức khi nhà hàng chưa bắt đầu chế biến. Bài toán yêu cầu hệ thống kiểm tra điều kiện hủy đơn trong thời gian cho phép. Nếu hợp lệ, hệ thống phải tự động kích hoạt lệnh hoàn tiền thông qua cổng thanh toán trung gian mà không cần sự can thiệp thủ công của nhân viên vận hành, đồng thời cập nhật lại số lượng tồn kho của món ăn đó.

### Hoàn tiền vé máy bay do hãng hàng không hủy chuyến

Một chuyến bay bị hủy do điều kiện thời tiết xấu và hãng hàng không cam kết hoàn lại 100% tiền vé cho tất cả hành khách. Thách thức ở đây là một mã đặt chỗ có thể chứa nhiều hành khách và nhiều chặng bay khác nhau. Hệ thống phải bóc tách được số tiền thực tế khách đã trả sau khi trừ các voucher giảm giá không có giá trị quy đổi thành tiền mặt, sau đó thực hiện hoàn tiền hàng loạt theo danh sách hành khách bị ảnh hưởng.

### Chính sách hoàn trả cho khóa học trực tuyến trong 7 ngày đầu

Một nền tảng học tập từ xa cho phép học viên yêu cầu hoàn tiền toàn bộ học phí nếu họ không hài lòng trong tuần đầu tiên, với điều kiện học viên chưa xem quá 20% nội dung video. Bài toán cần theo dõi tiến độ học tập của từng tài khoản và đối chiếu với thời gian thanh toán. Nếu đủ điều kiện, hệ thống sẽ thực hiện hoàn tiền và đồng thời thu hồi quyền truy cập vào khóa học cũng như các tài liệu đính kèm của người dùng đó.

### Hoàn tiền cho đơn hàng thanh toán bằng nhiều hình thức kết hợp

Khách hàng mua một món đồ điện tử giá trị cao bằng cách kết hợp thẻ quà tặng và thẻ tín dụng. Khi phát sinh yêu cầu hoàn tiền toàn bộ do lỗi nhà sản xuất, hệ thống database phải thiết kế sao cho biết chính xác bao nhiêu tiền cần trả về số dư thẻ quà tặng và bao nhiêu tiền cần gửi yêu cầu hoàn tác giao dịch sang phía ngân hàng. Việc hoàn tiền phải đảm bảo tính toàn vẹn, không để xảy ra tình trạng hoàn thừa hoặc thiếu vào các nguồn tiền khác nhau.

### Xử lý hoàn tiền trong mô hình kinh doanh Marketplace đa người bán

Một đơn hàng của khách hàng chứa sản phẩm từ ba nhà bán hàng khác nhau. Khách hàng muốn trả hàng và hoàn tiền toàn bộ cho sản phẩm của duy nhất một nhà bán trong đơn đó. Tuy nhiên, bài toán đặt ra là nếu đơn hàng đó có áp dụng mã giảm giá chung của toàn sàn cho tổng giá trị đơn hàng, hệ thống phải tính toán lại tỷ lệ giảm giá đã phân bổ để hoàn lại đúng số tiền thực tế khách đã chi trả cho riêng sản phẩm đó.

### Hệ thống đối soát hoàn tiền giữa doanh nghiệp và cổng thanh toán

Sau khi thực hiện lệnh hoàn tiền trên hệ thống nội bộ, tiền không đến tay khách hàng ngay lập tức mà phụ thuộc vào ngân hàng. Bài toán yêu cầu thiết kế quy trình lưu trữ các mã tham chiếu giao dịch từ phía cổng thanh toán (Transaction ID) và trạng thái đối soát hàng ngày. Nhân viên chăm sóc khách hàng cần một giao diện để theo dõi xem lệnh hoàn tiền đang ở trạng thái chờ xử lý, đã thành công hay bị phía ngân hàng từ chối để kịp thời phản hồi cho khách.

### Hoàn tiền cho dịch vụ lưu trú khách sạn theo chính sách mùa vụ

Khách hàng đặt phòng khách sạn nhưng muốn hủy phòng trước ngày nhận phòng. Chính sách hoàn tiền thay đổi tùy thuộc vào thời điểm hủy (ví dụ: hủy trước 48 giờ được hoàn 100%, sau đó thì không). Bài toán yêu cầu hệ thống lưu trữ các quy tắc chính sách này theo từng loại phòng và thời điểm đặt phòng. Khi khách nhấn nút yêu cầu, hệ thống tự động tính toán số tiền được hoàn dựa trên thời gian thực tế so với quy định trong hợp đồng đặt phòng.
