# Wallet withdraw

### Quản lý số dư khả dụng và số dư đóng băng

Trong thực tế, khi người dùng tạo lệnh rút tiền, hệ thống không nên trừ thẳng tiền trong ví ngay lập tức mà cần cơ chế đóng băng. Bài toán yêu cầu thiết kế cách quản lý số dư sao cho khi lệnh rút đang chờ xử lý, người dùng không thể dùng số tiền đó để mua sắm hay rút thêm lần nữa. Bạn cần giải quyết việc cập nhật trạng thái số dư qua các giai đoạn: khởi tạo, đang xử lý tại ngân hàng, thành công hoặc thất bại để hoàn tiền lại cho người dùng.

### Liên kết đa phương thức và xác thực tài khoản chính chủ

Một ví điện tử thường cho phép rút về nhiều ngân hàng hoặc ví điện tử liên kết khác nhau. Bài toán này tập trung vào việc lưu trữ thông tin các phương thức thanh toán của người dùng, bao gồm số tài khoản, tên ngân hàng, chi nhánh và trạng thái xác thực. Hệ thống cần đảm bảo rằng tên chủ tài khoản ngân hàng phải khớp với tên đã định danh trên ví để tránh rửa tiền hoặc gian lận, đồng thời quản lý được phương thức nào là mặc định.

### Xử lý giao dịch bất đồng bộ với phía Ngân hàng

Việc rút tiền không diễn ra tức thì trong database của bạn mà phụ thuộc vào API của bên thứ ba hoặc cổng thanh toán. Bài toán đặt ra tình huống hệ thống phải gửi yêu cầu đi, sau đó nhận kết quả trả về qua Webhook hoặc phải chủ động chạy các tiến trình quét lại trạng thái giao dịch (Reconciliation). Bạn cần thiết kế cấu trúc bảng giao dịch để lưu vết các mã tham chiếu từ ngân hàng và các mốc thời gian phản hồi nhằm đối soát dữ liệu sau này.

### Phân cấp phí rút tiền và hạn mức theo cấp độ tài khoản

Các hệ thống tài chính thường áp dụng phí rút tiền dựa trên số lần rút trong tháng hoặc tổng số tiền rút. Ví dụ: 3 lần đầu miễn phí, từ lần thứ 4 tính phí 1%. Ngoài ra, tùy vào cấp độ xác thực tài khoản (KYC) mà người dùng sẽ có hạn mức rút tối đa trong ngày hoặc tối đa mỗi giao dịch khác nhau. Bài toán yêu cầu thiết kế logic kiểm tra các điều kiện này trước khi cho phép tạo lệnh rút.

### Quy trình phê duyệt thủ công cho các giao dịch lớn

Để đảm bảo an toàn, các giao dịch rút tiền vượt quá một ngưỡng nhất định cần có sự can thiệp và phê duyệt từ nhân viên vận hành (Admin). Bài toán này yêu cầu thiết kế quy trình nghiệp vụ (Workflow) với các trạng thái như: Chờ duyệt, Đã duyệt, Từ chối kèm lý do. Hệ thống cần lưu lại lịch sử người phê duyệt và các ghi chú liên quan để phục vụ mục đích kiểm toán sau này.

### Quản lý hàng đợi và xử lý giao dịch song song

Khi có hàng ngàn người cùng rút tiền tại một thời điểm, hệ thống cần đảm bảo tính toàn vẹn dữ liệu và tránh tình trạng Race Condition (hai yêu cầu xử lý cùng lúc dẫn đến trừ tiền sai). Bài toán này hướng tới việc thiết kế hệ thống sử dụng hàng đợi (Message Queue) để xử lý tuần tự các lệnh rút tiền, đảm bảo mỗi giao dịch đều được ghi nhận chính xác vào sổ cái và không làm treo hệ thống khi tải cao.

### Đối soát dữ liệu định kỳ với các đối tác tài chính

Cuối mỗi ngày, dữ liệu rút tiền trên hệ thống ví có thể lệch so với sao kê từ phía ngân hàng do lỗi mạng hoặc độ trễ hệ thống. Bài toán yêu cầu thiết kế một module đối soát (Reconciliation) để so sánh các bản ghi giao dịch giữa hai bên. Bạn cần thiết kế các bảng lưu trữ file sao kê, các trạng thái đối soát như Khớp, Lệch số tiền, hoặc Chỉ có ở một bên để kế toán có thể xử lý thủ công.

### Hệ thống thông báo và lịch sử giao dịch chi tiết

Người dùng cần biết chính xác tiền của họ đang ở đâu trong quá trình rút. Bài toán yêu cầu thiết kế cấu trúc lưu trữ lịch sử giao dịch đủ chi tiết để hiển thị dòng thời gian (Timeline) cho người dùng, từ lúc yêu cầu được tiếp nhận, ngân hàng đang xử lý, cho đến khi tiền về tài khoản. Đồng thời, hệ thống phải tích hợp gửi thông báo qua App hoặc SMS tương ứng với mỗi thay đổi trạng thái của lệnh rút.
