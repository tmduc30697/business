# System audit log

### Theo dõi hành động thay đổi cấu hình quan trọng của quản trị viên

Trong một hệ thống quản lý nội bộ, khi một quản trị viên thay đổi các thiết lập quan trọng như bật tắt cổng thanh toán hoặc thay đổi tỷ giá hối đoái, hệ thống cần ghi lại chi tiết ai đã thực hiện, vào lúc nào, địa chỉ IP thực hiện và quan trọng nhất là giá trị trước và sau khi thay đổi. Bài toán này yêu cầu bạn thiết kế cấu trúc dữ liệu sao cho có thể so sánh được sự khác biệt giữa hai phiên bản dữ liệu một cách trực quan khi truy xuất lại để phục vụ công tác hậu kiểm.

### Truy vết đăng nhập và phát hiện hành vi xâm nhập trái phép

Hệ thống cần ghi lại mọi nỗ lực đăng nhập của người dùng bao gồm cả đăng nhập thành công và thất bại. Thông tin lưu trữ cần có loại thiết bị, trình duyệt, vị trí địa lý ước tính và trạng thái lỗi nếu đăng nhập thất bại. Đây là cơ sở để thiết kế các thuật toán cảnh báo nếu một tài khoản có hàng chục lần đăng nhập sai trong một phút hoặc đăng nhập từ hai vị trí địa lý cách xa nhau trong thời gian ngắn.

### Nhật ký thay đổi trạng thái đơn hàng trong thương mại điện tử

Một đơn hàng từ lúc đặt đến lúc giao thành công trải qua rất nhiều bước và có thể do nhiều bên tác động như khách hàng, nhân viên kho, shipper hoặc hệ thống tự động hủy do hết hạn thanh toán. Hệ thống audit log cần ghi lại dòng chảy trạng thái này để khi có khiếu nại, người quản lý có thể biết chính xác tại thời điểm đó bên nào đã chuyển trạng thái đơn hàng và lý do cụ thể là gì.

### Ghi lại các thao tác nhạy cảm liên quan đến số dư tài khoản

Đối với các hệ thống tài chính hoặc ví điện tử, bất kỳ hành động nào làm thay đổi số dư của người dùng đều phải được ghi log một cách nghiêm ngặt. Log này không chỉ lưu số tiền thay đổi mà còn phải liên kết với mã giao dịch, loại giao dịch và mã tham chiếu từ đối tác ngân hàng. Bài toán này đòi hỏi tính toàn vẹn dữ liệu cực cao, đảm bảo log không thể bị chỉnh sửa hoặc xóa bỏ bởi bất kỳ ai, kể cả lập trình viên có quyền truy cập vào database.

### Hệ thống lưu trữ và quản lý log tập trung cho kiến trúc Microservices

Khi hệ thống được chia thành nhiều dịch vụ nhỏ chạy độc lập, việc mỗi dịch vụ tự lưu log vào database riêng sẽ gây khó khăn cho việc tra cứu tổng thể một luồng nghiệp vụ. Bài toán đặt ra là thiết kế một hệ thống thu gom log tập trung, nơi tất cả các dịch vụ gửi hành động về một đầu mối duy nhất. Bạn cần giải quyết vấn đề định danh duy nhất cho mỗi yêu cầu của người dùng xuyên suốt qua tất cả các dịch vụ để có thể xâu chuỗi hành động lại với nhau.

### Tự động ghi nhật ký các thay đổi từ hệ thống và tiến trình chạy ngầm

Ngoài hành động của con người, hệ thống còn có các tiến trình chạy tự động như cập nhật giá hàng loạt, quét đơn hàng quá hạn hoặc sao lưu dữ liệu định kỳ. Nếu các tiến trình này gặp lỗi hoặc thực hiện sai logic, hậu quả sẽ rất lớn. Việc thiết kế audit log cho system events giúp kỹ sư vận hành biết được tiến trình nào đã chạy, thời gian thực hiện bao lâu, bao nhiêu bản ghi đã được xử lý thành công và chi tiết các bản ghi bị lỗi.

### Phân quyền truy cập và kiểm soát người xem nhật ký hệ thống

Dữ liệu log đôi khi chứa các thông tin nhạy cảm, vì vậy chính việc truy cập vào xem log cũng cần được ghi log lại. Bài toán này yêu cầu thiết kế một hệ thống phân quyền phức tạp, nơi chỉ những người có vai trò kiểm toán mới được xem log, và mỗi lần họ truy vấn log thì hệ thống sẽ ghi lại họ đã xem những thông tin nào. Điều này đảm bảo tính minh bạch tối đa và ngăn chặn việc lạm dụng quyền hạn để soi mói dữ liệu người dùng.

### Cơ chế lưu trữ log lâu dài và dọn dẹp dữ liệu cũ theo định kỳ

Dữ liệu audit log tăng trưởng rất nhanh theo thời gian và có thể làm tràn dung lượng ổ cứng hoặc làm chậm hệ thống nếu lưu chung với bảng dữ liệu nghiệp vụ. Bạn cần thiết kế giải pháp phân tách dữ liệu log cũ ra các kho lưu trữ rẻ tiền hơn hoặc thực hiện nén dữ liệu nhưng vẫn phải đảm bảo khi cần thiết có thể khôi phục và truy vấn lại nhanh chóng để phục vụ các cuộc thanh tra định kỳ của cơ quan chức năng.
