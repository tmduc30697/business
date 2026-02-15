# Manual refund override

### Xử lý hoàn tiền cho đơn hàng đã quá thời hạn bảo hành hoặc đổi trả

Thông thường, hệ thống tự động sẽ chặn nút hoàn tiền nếu đơn hàng đã vượt quá 7 hoặc 30 ngày kể từ khi giao hàng thành công. Tuy nhiên, trong một số trường hợp đặc biệt như sản phẩm bị lỗi kỹ thuật hàng loạt hoặc do thỏa thuận riêng với khách hàng thân thiết, Admin cần có quyền ghi đè cơ chế kiểm tra thời gian này. Hệ thống phải cho phép Admin nhập lý do ngoại lệ và thực hiện lệnh hoàn tiền ngay cả khi trạng thái đơn hàng đã đóng vĩnh viễn trên luồng tự động.

### Hoàn tiền một phần số tiền tùy chỉnh không theo giá trị sản phẩm

Quy trình tự động thường chỉ cho phép hoàn tiền theo giá trị của từng món hàng cụ thể trong đơn. Bài toán thực tế phát sinh khi khách hàng chỉ yêu cầu bồi thường một khoản phí nhỏ do sản phẩm bị trầy xước nhẹ hoặc giao hàng chậm, thay vì trả lại toàn bộ hàng. Admin cần một giao diện để nhập một con số bất kỳ, miễn là nhỏ hơn hoặc bằng tổng số tiền khách đã thanh toán, và hệ thống phải hạch toán chính xác số dư còn lại của đơn hàng đó.

### Thay đổi phương thức hoàn tiền so với nguồn thanh toán ban đầu

Theo quy định mặc định, tiền phải được hoàn về đúng thẻ hoặc ví điện tử mà khách đã dùng để mua hàng. Tuy nhiên, nếu thẻ của khách hàng đã bị khóa, hết hạn hoặc khách hàng muốn nhận tiền vào tài khoản ngân hàng khác, quy trình tự động sẽ thất bại. Admin cần can thiệp để chuyển đổi trạng thái hoàn tiền từ hệ thống cổng thanh toán sang hình thức chuyển khoản thủ công hoặc cộng tiền vào ví nội bộ của khách trên hệ thống.

### Hoàn tiền bù cho các loại chi phí phát sinh ngoài hóa đơn

Trong trường hợp khách hàng phải tự bỏ tiền túi để gửi trả hàng về kho do lỗi của người bán, doanh nghiệp có thể muốn hoàn lại cả tiền hàng lẫn phí vận chuyển phát sinh này. Vì phí vận chuyển trả hàng không nằm trong hóa đơn gốc, Admin cần chức năng tạo một lệnh chi trả thủ công gắn liền với mã đơn hàng đó. Hệ thống cần ghi nhận đây là khoản chi phí vận chuyển bổ sung để bộ phận kế toán có thể đối soát vào cuối tháng.

### Can thiệp hoàn tiền khi cổng thanh toán trực tuyến gặp sự cố kỹ thuật

Khi cổng thanh toán bên thứ ba gặp lỗi kết nối hoặc bị sập trong thời gian dài, các lệnh hoàn tiền tự động từ hệ thống sẽ bị treo hoặc báo lỗi liên tục. Để xử lý gấp cho khách hàng, Admin sẽ thực hiện hoàn tiền bằng tiền mặt hoặc chuyển khoản ngoài hệ thống. Sau đó, Admin cần quyền cập nhật trạng thái đơn hàng sang đã hoàn tiền thủ công để đồng bộ hóa dữ liệu, tránh việc khi cổng thanh toán hoạt động trở lại hệ thống lại thực hiện hoàn tiền thêm một lần nữa.

### Phê duyệt lệnh hoàn tiền qua nhiều cấp bậc quản lý

Đối với các giao dịch có giá trị lớn vượt quá một ngưỡng nhất định, nhân viên chăm sóc khách hàng không được phép tự ý thực hiện hoàn tiền. Bài toán đặt ra là thiết kế một luồng ghi đè thủ công yêu cầu phê duyệt. Khi nhân viên nhấn nút hoàn tiền, lệnh này sẽ rơi vào trạng thái chờ duyệt. Admin cấp cao hoặc Quản lý tài chính phải vào kiểm tra hồ sơ, bằng chứng và nhấn nút xác nhận cuối cùng thì dòng tiền mới được kích hoạt và dữ liệu mới được cập nhật.

### Hoàn trả lượt sử dụng mã giảm giá và điểm thưởng sau khi hoàn tiền thủ công

Khi một đơn hàng được hoàn tiền thủ công, các thực thể liên quan như mã giảm giá (coupon) đã dùng hoặc điểm tích lũy (loyalty points) nhận được từ đơn đó cần được xử lý lại. Hệ thống phải cho phép Admin chọn lựa giữa việc chỉ hoàn tiền mặt hay hoàn cả lượt dùng mã giảm giá cho khách. Nếu không thiết kế kỹ, database sẽ bị lệch chuẩn khi tiền đã trả nhưng khách vẫn giữ lại điểm thưởng hoặc lượt dùng ưu đãi của đơn hàng đó.

### Truy vết và lưu trữ minh chứng cho các lệnh hoàn tiền ngoại lệ

Vì đây là hành động can thiệp trực tiếp vào dòng tiền, mọi thao tác Manual Override đều tiềm ẩn rủi ro gian lận nội bộ. Hệ thống cần yêu cầu Admin phải tải lên các tệp tin minh chứng như ảnh chụp biên lai chuyển khoản, ảnh chụp màn hình tin nhắn thỏa thuận với khách hoặc biên bản kiểm định hàng lỗi. Database phải thiết kế các bảng Audit Log chi tiết để lưu lại ai là người thực hiện, thời gian nào, lý do là gì và các tài liệu đính kèm để phục vụ công tác hậu kiểm.
