# Refund status tracking

### Quản lý vòng đời trạng thái hoàn tiền đa kênh

Bài toán này tập trung vào việc thiết kế một State Machine để kiểm soát luồng đi của một yêu cầu hoàn tiền. Bạn cần xử lý các trạng thái từ lúc khách hàng khởi tạo yêu cầu, qua các bước kiểm tra của bộ phận chăm sóc khách hàng, phê duyệt của bộ phận kế toán, và cuối cùng là xác nhận từ phía cổng thanh toán. Hệ thống phải ghi lại lịch sử thay đổi trạng thái kèm theo mốc thời gian và người thực hiện để phục vụ mục đích kiểm toán sau này.

### Xử lý hoàn tiền cho đơn hàng gồm nhiều sản phẩm

Trong thực tế, khách hàng thường chỉ muốn hoàn tiền cho một hoặc một vài sản phẩm trong một đơn hàng lớn có nhiều mặt hàng. Bài toán yêu cầu bạn thiết kế cấu trúc dữ liệu sao cho có thể tách nhỏ giá trị hoàn tiền, tính toán lại các khoản giảm giá hoặc mã khuyến mãi đã áp dụng cho từng sản phẩm riêng lẻ. Việc theo dõi trạng thái lúc này không chỉ nằm ở cấp độ đơn hàng mà phải chi tiết đến từng dòng sản phẩm trong yêu cầu hoàn tiền đó.

### Tích hợp và đối soát dữ liệu với cổng thanh toán bên thứ ba

Khi thực hiện hoàn tiền, hệ thống của bạn phải giao tiếp với các bên như Stripe, PayPal hoặc các ngân hàng nội địa. Bài toán đặt ra là làm thế nào để lưu trữ và cập nhật các mã giao dịch từ phía đối tác, xử lý các trường hợp hoàn tiền bị từ chối do thẻ hết hạn hoặc tài khoản bị khóa. Bạn cần thiết kế cơ chế webhook để nhận phản hồi tự động và cập nhật tiến độ hoàn tiền ngay lập tức cho người dùng mà không cần họ phải tải lại trang.

### Quy trình kiểm kho và hoàn tiền sau khi thu hồi hàng hóa

Đây là mô hình hoàn tiền phổ biến trong thương mại điện tử nơi việc trả tiền chỉ xảy ra sau khi hàng được trả về kho và kiểm tra chất lượng. Bạn cần thiết kế sự phối hợp giữa hệ thống quản lý kho và hệ thống tài chính. Trạng thái hoàn tiền sẽ bị phụ thuộc vào kết quả kiểm định hàng hóa tại kho, ví dụ hàng còn nguyên tem mác thì hoàn 100%, hàng đã bóc seal thì chỉ hoàn 80% hoặc từ chối hoàn tiền.

### Quản lý hoàn tiền vào ví điện tử nội bộ và điểm thưởng

Thay vì trả tiền mặt, nhiều hệ thống cho phép hoàn tiền vào ví tích lũy của ứng dụng hoặc trả lại điểm thưởng thành viên. Bài toán yêu cầu thiết kế logic chuyển đổi giá trị và theo dõi số dư. Bạn phải xử lý kịch bản phức tạp khi một đơn hàng được thanh toán bằng cả tiền mặt và điểm thưởng, dẫn đến việc khi hoàn tiền cũng phải trả về đúng tỷ lệ tương ứng vào các nguồn tiền khác nhau.

### Hệ thống thông báo và tương tác thời gian thực cho người dùng

Người dùng thường rất lo lắng về số tiền của mình, vì vậy việc cập nhật tiến độ là cực kỳ quan trọng. Bài toán này tập trung vào việc thiết kế hệ thống gửi thông báo qua email, tin nhắn hoặc thông báo ứng dụng mỗi khi yêu cầu hoàn tiền chuyển sang bước mới. Bạn cần thiết kế các mẫu thông báo động dựa trên trạng thái hiện tại và cung cấp một giao diện tra cứu tiến độ trực quan với các mốc thời gian dự kiến tiền sẽ về tài khoản.

### Xử lý tranh chấp và khiếu nại trong quá trình hoàn tiền

Không phải yêu cầu hoàn tiền nào cũng diễn ra suôn sẻ. Bài toán đặt ra là thiết kế các bảng dữ liệu để lưu trữ bằng chứng hình ảnh, video và các đoạn hội thoại trao đổi giữa người mua và người bán khi có tranh chấp xảy ra. Hệ thống cần hỗ trợ chức năng tạm dừng tiến trình hoàn tiền để chuyển sang trạng thái chờ xử lý tranh chấp và cho phép quản trị viên can thiệp để đưa ra quyết định cuối cùng.

### Báo cáo phân tích và dự báo dòng tiền hoàn trả

Đối với doanh nghiệp, việc theo dõi tổng số tiền đang nằm trong trạng thái chờ hoàn là rất quan trọng để quản lý dòng tiền. Bài toán yêu cầu bạn thiết kế hệ thống báo cáo có thể trích xuất dữ liệu theo thời gian, theo lý do hoàn tiền phổ biến nhất, và tính toán thời gian xử lý trung bình của mỗi giai đoạn. Dữ liệu này giúp doanh nghiệp tối ưu hóa quy trình vận hành và nhận diện các vấn đề về chất lượng sản phẩm.
