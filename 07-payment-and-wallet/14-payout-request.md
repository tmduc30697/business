# Payout request

### Quản lý số dư khả dụng và phong tỏa tiền khi có yêu cầu

Bài toán này tập trung vào việc đảm bảo tính toàn vẹn của dữ liệu tài chính. Khi một người bán tạo yêu cầu rút tiền, hệ thống cần kiểm tra xem số dư hiện tại có đủ hay không. Nếu đủ, hệ thống không được trừ tiền ngay lập tức mà phải chuyển số tiền đó vào trạng thái phong tỏa hoặc chờ xử lý. Điều này ngăn chặn việc người bán thực hiện nhiều yêu cầu rút tiền cùng lúc vượt quá số dư thực tế họ có. Bạn cần thiết kế cơ chế để cập nhật đồng thời số dư khả dụng và số dư đóng băng một cách chính xác.

### Quy trình phê duyệt yêu cầu rút tiền nhiều cấp

Trong các hệ thống doanh nghiệp hoặc sàn thương mại điện tử lớn, không phải yêu cầu rút tiền nào cũng được thực hiện tự động. Bài toán yêu cầu thiết lập một luồng trạng thái cho lệnh rút tiền từ lúc khởi tạo, chờ quản trị viên duyệt, đến khi kế toán xác nhận chuyển khoản thành công. Mỗi bước thay đổi trạng thái cần lưu lại dấu vết ai là người thực hiện và thời gian cụ thể. Việc thiết kế bảng lưu trữ lịch sử trạng thái là yếu tố then chốt để phục vụ mục đích đối soát và kiểm toán sau này.

### Tích hợp đa phương thức nhận tiền và thông tin định danh

Người bán có nhu cầu nhận tiền qua nhiều kênh khác nhau như tài khoản ngân hàng, ví điện tử hoặc các cổng thanh toán quốc tế. Bài toán đặt ra là làm thế nào để lưu trữ thông tin thanh toán của người bán một cách linh hoạt vì mỗi phương thức lại có các trường thông tin khác nhau. Ví dụ, rút về ngân hàng cần số tài khoản và chi nhánh, trong khi ví điện tử chỉ cần số điện thoại. Hệ thống cần quản lý danh sách các phương thức này và cho phép người bán chọn phương thức mặc định khi tạo yêu cầu.

### Xử lý phí rút tiền và hạn mức theo cấp bậc người dùng

Mỗi giao dịch rút tiền thường đi kèm với chi phí vận hành hoặc phí sàn. Bài toán yêu cầu tính toán số tiền thực nhận của người bán sau khi trừ đi các loại phí cố định hoặc phí theo phần trăm. Ngoài ra, hệ thống cần áp dụng các quy tắc về hạn mức như số tiền tối thiểu cho một lần rút, số tiền tối đa trong một ngày hoặc số lượt rút tối đa trong một tháng dựa trên cấp độ uy tín của người bán. Việc này đòi hỏi một thiết kế database có khả năng lưu trữ cấu hình quy tắc linh hoạt.

### Đối soát và xử lý lỗi khi giao dịch ngân hàng thất bại

Thực tế quá trình chuyển tiền từ hệ thống ra ngân hàng có thể gặp lỗi như sai thông tin tài khoản, ngân hàng bảo trì hoặc lỗi mạng. Bài toán yêu cầu thiết kế hệ thống có khả năng tiếp nhận phản hồi từ API ngân hàng để cập nhật trạng thái lệnh rút. Nếu lệnh thất bại, hệ thống phải thực hiện hoàn trả số tiền đã phong tỏa về lại số dư khả dụng cho người bán một cách tự động và gửi thông báo lý do chi tiết để họ có thể chỉnh sửa thông tin.

### Lịch trình rút tiền tự động định kỳ cho người bán

Thay vì phải tạo lệnh thủ công, nhiều người bán có nhu cầu nhận tiền định kỳ vào một ngày cố định trong tuần hoặc khi số dư đạt tới một ngưỡng nhất định. Bài toán này yêu cầu thiết kế logic để hệ thống tự động quét các tài khoản đủ điều kiện và tự tạo yêu cầu rút tiền vào danh sách chờ xử lý. Bạn cần cân nhắc cách lưu trữ các cấu hình lịch trình này sao cho hệ thống có thể truy vấn và thực thi hàng loạt hiệu quả mà không gây quá tải cho cơ sở dữ liệu.

### Quản lý chứng từ và mã tham chiếu giao dịch

Để phục vụ việc kế toán và minh bạch hóa, mỗi yêu cầu rút tiền cần được gắn với một mã tham chiếu duy nhất từ phía ngân hàng hoặc cổng thanh toán. Bài toán yêu cầu lưu trữ các bằng chứng thanh toán như ảnh chụp biên lai hoặc tệp PDF ủy nhiệm chi. Khi người bán thắc mắc về một khoản tiền, bộ phận hỗ trợ phải dễ dàng truy xuất được mã giao dịch liên quan để kiểm tra trên hệ thống của ngân hàng. Điều này giúp đồng bộ dữ liệu giữa hệ thống nội bộ và thế giới bên ngoài.

### Phân tích xu hướng và báo cáo dòng tiền đầu ra

Bài toán này hướng tới việc khai thác dữ liệu để phục vụ quản trị. Chủ sàn cần biết tổng lượng tiền được rút ra theo từng ngày, từng tháng và phương thức thanh toán nào đang được ưa chuộng nhất. Dữ liệu từ các yêu cầu rút tiền cần được tổ chức sao cho việc truy vấn báo cáo tổng hợp không làm ảnh hưởng đến hiệu năng của các giao dịch đang diễn ra. Bạn sẽ cần tư duy về việc thiết kế các bảng lưu trữ dữ liệu tinh gọn hoặc sử dụng các kỹ thuật tổng hợp dữ liệu định kỳ.
