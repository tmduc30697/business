# Return request

### Quy trình phê duyệt yêu cầu trả hàng nhiều bước

Trong kịch bản này, hệ thống cần ghi lại trạng thái của một yêu cầu trả hàng từ lúc người mua khởi tạo, chờ người bán xác nhận, cho đến khi đơn vị vận chuyển lấy hàng thành công. Bài toán đặt ra là làm sao để lưu trữ lịch sử thay đổi trạng thái và các điều kiện chuyển trạng thái, ví dụ như người bán chỉ được bấm chấp nhận trả hàng nếu đơn hàng gốc đã ở trạng thái giao hàng thành công và chưa quá thời hạn bảy ngày.

### Phân loại lý do trả hàng và bằng chứng đính kèm

Người mua có thể trả hàng vì nhiều lý do khác nhau như hàng lỗi, giao sai mẫu, hoặc không còn nhu cầu. Mỗi lý do này sẽ yêu cầu các loại bằng chứng khác nhau như hình ảnh sản phẩm thực tế hoặc video quay cảnh mở hộp hàng. Hệ thống cần quản lý việc lưu trữ các tệp tin đa phương tiện này và liên kết chúng với mã yêu cầu trả hàng để nhân viên chăm sóc khách hàng có căn cứ đối soát và ra quyết định.

### Hoàn tiền một phần cho đơn hàng có nhiều sản phẩm

Một đơn hàng có thể chứa năm sản phẩm khác nhau nhưng người mua chỉ muốn trả lại hai sản phẩm trong số đó. Bài toán yêu cầu thiết kế hệ thống sao cho có thể bóc tách giá trị của từng sản phẩm, tính toán lại số tiền hoàn trả thực tế sau khi đã trừ đi các mã giảm giá hoặc chi phí vận chuyển đã áp dụng cho toàn bộ đơn hàng ban đầu. Điều này ảnh hưởng trực tiếp đến việc thiết kế bảng chi tiết yêu cầu trả hàng.

### Quản lý Logistics thu hồi và mã vận đơn ngược

Sau khi yêu cầu trả hàng được chấp nhận, hệ thống cần sinh ra một mã vận đơn mới để đơn vị vận chuyển đến nhà người mua lấy hàng mang về kho của người bán. Bạn cần giải quyết vấn đề đồng bộ thông tin giữa hệ thống của mình với các đơn vị giao hàng thứ ba, theo dõi lộ trình của gói hàng trả về và tự động cập nhật trạng thái khi kho xác nhận đã nhận được kiện hàng đó.

### Kiểm định chất lượng hàng trả về tại kho

Khi hàng về đến kho, nhân viên kho cần thực hiện bước kiểm tra xem hàng còn nguyên tem mác hay có hỏng hóc gì do người dùng gây ra hay không. Kết quả kiểm định này sẽ quyết định việc hoàn tiền toàn bộ, hoàn tiền một phần hoặc từ chối hoàn tiền và gửi trả lại hàng cho người mua. Hệ thống cần có các biểu mẫu ghi nhận tình trạng hàng hóa và cho phép đính kèm biên bản kiểm kho.

### Xử lý hoàn tiền qua nhiều phương thức thanh toán

Người mua có thể đã thanh toán đơn hàng bằng sự kết hợp giữa ví điện tử, thẻ ngân hàng và điểm thưởng hệ thống. Khi thực hiện hoàn tiền, hệ thống phải có logic để ưu tiên hoàn lại điểm thưởng trước, sau đó mới đến tiền mặt vào ví hoặc thẻ. Việc thiết kế database phải đảm bảo tính toàn vẹn dữ liệu để không xảy ra tình trạng hoàn tiền nhầm hoặc hoàn quá số tiền khách đã trả.

### Đối soát tài chính giữa người mua và người bán

Trong mô hình sàn giao dịch, tiền của đơn hàng thường do sàn giữ trung gian. Khi có yêu cầu trả hàng, sàn phải treo khoản thanh toán đó lại và không được chuyển cho người bán. Nếu yêu cầu trả hàng thành công, hệ thống phải thực hiện các bút toán ngược để trừ doanh thu của người bán, cộng lại phí sàn và hoàn tiền cho người mua, đảm bảo báo cáo tài chính cuối tháng luôn khớp.

### Hệ thống thông báo và trao đổi giữa các bên

Trong quá trình xử lý trả hàng, người mua và người bán thường có nhu cầu nhắn tin trao đổi hoặc gửi thêm bằng chứng bổ sung. Ngoài ra, mỗi khi trạng thái yêu cầu thay đổi, hệ thống cần gửi thông báo đẩy hoặc email cho các bên liên quan. Bài toán này yêu cầu thiết kế các bảng lưu trữ tin nhắn theo ngữ cảnh của từng yêu cầu trả hàng và hệ thống hàng đợi gửi thông báo thời gian thực.
