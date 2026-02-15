# Backup system

### Quản lý lập lịch sao lưu đa dạng cho nhiều dự án

Một công ty công nghệ cung cấp dịch vụ quản lý dữ liệu cho nhiều khách hàng khác nhau. Mỗi khách hàng có nhu cầu sao lưu riêng biệt như sao lưu hàng giờ, hàng ngày hoặc chỉ vào cuối tuần. Hệ thống cần một cơ chế để định nghĩa các loại chu kỳ này và tự động kích hoạt tiến trình sao lưu đúng thời điểm. Bạn cần thiết kế bảng dữ liệu để lưu trữ cấu hình lịch trình, trạng thái kích hoạt và liên kết với các đối tượng cần sao lưu tương ứng.

### Theo dõi trạng thái và lịch sử chi tiết các phiên sao lưu

Khi hệ thống thực hiện sao lưu tự động, việc ghi lại nhật ký là cực kỳ quan trọng để quản trị viên kiểm soát. Mỗi phiên sao lưu cần được lưu trữ các thông tin như thời gian bắt đầu, thời gian kết thúc, tổng dung lượng dữ liệu, loại sao lưu là toàn phần hay phần bù, và quan trọng nhất là trạng thái thành công hay thất bại. Nếu thất bại, hệ thống phải lưu lại mã lỗi hoặc thông báo chi tiết để phục vụ việc tra cứu và xử lý sự cố sau này.

### Quản lý lưu trữ tệp tin sao lưu trên nhiều môi trường vật lý

Sau khi dữ liệu được đóng gói, chúng có thể được đẩy lên nhiều nơi khác nhau như máy chủ lưu trữ tại chỗ, các dịch vụ lưu trữ đám mây hoặc các ổ đĩa mạng. Bài toán đặt ra là phải quản lý được đường dẫn vật lý hoặc địa chỉ liên kết của từng bản sao lưu. Database cần thiết kế để biết được một bản sao lưu cụ thể đang nằm ở đâu, thuộc nhà cung cấp dịch vụ nào và có dung lượng thực tế là bao nhiêu để phục vụ việc tải về khi cần phục hồi.

### Cơ chế tự động dọn dẹp và quản lý vòng đời bản sao lưu

Lưu trữ dữ liệu tốn kém rất nhiều chi phí, vì vậy không thể giữ lại tất cả các bản sao lưu từ trước đến nay. Hệ thống cần một chính sách giữ lại dữ liệu, ví dụ như chỉ giữ các bản sao lưu trong vòng 30 ngày gần nhất, hoặc giữ 1 bản mỗi tháng trong vòng 1 năm. Bạn cần thiết kế logic để hệ thống tự động nhận diện các bản sao lưu đã hết hạn dựa trên cấu hình của người dùng và thực hiện lệnh xóa vật lý để giải phóng không gian lưu trữ.

### Phân quyền và bảo mật truy cập vào kho dữ liệu dự phòng

Bản sao lưu chứa toàn bộ dữ liệu nhạy cảm của doanh nghiệp, do đó việc ai có quyền tạo, xem hoặc tải bản sao lưu là một vấn đề bảo mật sống còn. Bài toán yêu cầu thiết kế hệ thống phân quyền chi tiết, nơi quản trị viên có thể chỉ định nhân viên nào được phép quản lý dự án nào. Mọi hành động truy cập hoặc tải tệp sao lưu xuống đều phải được ghi lại trong nhật ký hệ thống để phục vụ mục đích kiểm toán bảo mật.

### Kiểm tra tính toàn vẹn và xác thực bản sao lưu sau khi tạo

Một bản sao lưu thành công về mặt tiến trình không có nghĩa là dữ liệu bên trong có thể sử dụng được. Hệ thống cần một cơ chế để lưu trữ mã băm xác thực cho mỗi tệp tin sau khi được tạo ra. Khi cần phục hồi, hệ thống sẽ tính toán lại mã băm của tệp hiện tại và so sánh với mã băm đã lưu trong database. Nếu hai mã này khác nhau, hệ thống phải cảnh báo dữ liệu đã bị hỏng hoặc bị can thiệp trái phép.

### Quản lý quy trình phục hồi dữ liệu từ các phiên bản cũ

Phục hồi dữ liệu là mục đích cuối cùng của hệ thống sao lưu. Bài toán ở đây là thiết kế quy trình để người dùng có thể chọn một thời điểm cụ thể trong quá khứ và ra lệnh phục hồi. Hệ thống cần ghi lại lịch sử các lần phục hồi, ai là người thực hiện, phục hồi vào môi trường nào và kết quả của việc phục hồi đó. Điều này giúp tránh việc ghi đè nhầm dữ liệu đang hoạt động bằng một bản sao lưu quá cũ.

### Hệ thống cảnh báo và thông báo sự cố sao lưu thời gian thực

Trong trường hợp tiến trình sao lưu bị gián đoạn do mất kết nối mạng hoặc hết dung lượng đĩa, quản trị viên cần được biết ngay lập tức. Bài toán này yêu cầu thiết kế một module thông báo kết nối với database sao lưu. Khi một bản ghi phiên sao lưu được cập nhật trạng thái thất bại, hệ thống sẽ dựa vào cấu hình thông báo để gửi tin nhắn qua email hoặc các ứng dụng chat cho những người có trách nhiệm xử lý.
