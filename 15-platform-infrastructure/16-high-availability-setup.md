# High availability setup

### Điều phối lưu lượng truy cập qua nhiều máy chủ ứng dụng

Một trang tin tức điện tử có lượng truy cập thay đổi đột ngột khi có sự kiện nóng. Để đảm bảo hệ thống không bị sập khi một máy chủ gặp sự cố hoặc quá tải, bạn cần thiết lập một bộ cân bằng tải đứng trước một nhóm gồm nhiều máy chủ ứng dụng giống hệt nhau. Bài toán đặt ra là làm thế nào để bộ cân bằng tải biết được máy chủ nào đang sống hay đã chết để chuyển hướng yêu cầu, đồng thời đảm bảo rằng nếu người dùng đang đăng nhập ở máy chủ này mà bị chuyển sang máy chủ khác thì họ không bị đăng xuất đột ngột.

### Đồng bộ hóa dữ liệu giữa các trung tâm dữ liệu khác vùng địa lý

Một ứng dụng tài chính yêu cầu hoạt động liên tục ngay cả khi toàn bộ một trung tâm dữ liệu tại một thành phố bị mất điện hoặc gặp thiên tai. Hệ thống cần được thiết kế để chạy song song tại hai vùng địa lý khác nhau. Thử thách ở đây là việc đồng bộ hóa cơ sở dữ liệu giữa hai miền sao cho độ trễ thấp nhất có thể và đảm bảo tính nhất quán của số dư tài khoản. Khi một vùng gặp sự cố, hệ thống điều hướng tên miền phải tự động nhận biết và trỏ toàn bộ người dùng về vùng còn lại mà không gây gián đoạn dịch vụ.

### Thiết lập cơ chế chuyển đổi dự phòng tự động cho cơ sở dữ liệu

Trong một hệ thống thương mại điện tử, cơ sở dữ liệu là thành phần quan trọng nhất. Nếu máy chủ cơ sở dữ liệu chính bị hỏng, toàn bộ việc đặt hàng sẽ dừng lại. Bạn cần thiết lập mô hình gồm một máy chủ chính cho phép đọc viết và các máy chủ phụ chỉ cho phép đọc. Bài toán yêu cầu thiết kế một cơ chế giám sát giúp phát hiện ngay lập tức khi máy chủ chính gặp lỗi, sau đó tự động bầu chọn một máy chủ phụ lên làm máy chủ chính mới và cập nhật cấu hình kết nối của các ứng dụng phía trên mà không cần sự can thiệp thủ công của con người.

### Quản lý phiên làm việc tập trung trong môi trường đa máy chủ

Khi triển khai hệ thống trên nhiều server để đảm bảo tính sẵn sàng cao, việc lưu trữ thông tin phiên làm việc của người dùng trực tiếp trên bộ nhớ của từng máy chủ sẽ gây ra lỗi khi bộ cân bằng tải chuyển người dùng sang máy chủ khác. Bài toán đặt ra là thiết kế một lớp lưu trữ dữ liệu phiên làm việc dùng chung, có tốc độ truy xuất cực nhanh và bản thân lớp lưu trữ này cũng phải có khả năng dự phòng. Nếu lớp lưu trữ này chết, toàn bộ người dùng sẽ bị văng ra khỏi hệ thống, do đó nó cũng cần một mô hình cụm máy chủ hoạt động song song.

### Hệ thống lưu trữ tệp tin phân tán và dự phòng

Một ứng dụng mạng xã hội cho phép người dùng đăng tải hình ảnh và video với dung lượng lớn. Nếu chỉ lưu trữ trên một ổ cứng của một máy chủ duy nhất, dữ liệu sẽ mất trắng nếu ổ cứng hỏng. Bạn cần thiết lập một hệ thống lưu trữ tệp tin sao cho mỗi khi một tệp được tải lên, nó sẽ được tự động nhân bản ra ít nhất ba vị trí vật lý khác nhau. Khi người dùng truy cập tệp, hệ thống phải thông minh để lấy tệp từ vị trí gần nhất hoặc vị trí đang có tốc độ phản hồi tốt nhất, đảm bảo tính sẵn sàng của nội dung đa phương tiện.

### Kiểm soát trạng thái và tự động thay thế các máy chủ lỗi

Trong các hệ thống hiện đại sử dụng điện toán đám mây, các máy chủ ảo có thể bị tắt hoặc gặp lỗi bất cứ lúc nào. Bài toán yêu cầu thiết kế một hệ thống quản lý nhóm máy chủ có khả năng tự phục hồi. Nếu bạn cấu hình hệ thống luôn cần tối thiểu 5 máy chủ hoạt động, thì khi có 2 máy chủ bị lỗi phần cứng, hệ thống quản lý phải tự động phát hiện, hủy bỏ các máy chủ lỗi và khởi tạo 2 máy chủ mới thay thế ngay lập tức để duy trì đúng năng lực xử lý đã cam kết ban đầu.

### Thiết kế hệ thống hàng đợi tin nhắn có khả năng chịu lỗi cao

Để giảm tải cho các tác vụ nặng như gửi email hàng loạt hoặc xử lý video, hệ thống sử dụng các hàng đợi tin nhắn. Tuy nhiên, nếu máy chủ chứa hàng đợi này bị sập, toàn bộ các yêu cầu chưa xử lý sẽ bị mất. Bài toán này yêu cầu thiết lập một cụm các máy chủ hàng đợi hoạt động theo mô hình phân tán. Các tin nhắn khi gửi vào hàng đợi phải được xác nhận đã lưu trữ an toàn trên nhiều nút trước khi phản hồi cho ứng dụng, đảm bảo rằng ngay cả khi một nút trong cụm bị hỏng, các tiến trình xử lý ngầm vẫn tiếp tục chạy bình thường.

### Cập nhật hệ thống không gây gián đoạn dịch vụ

Một hệ thống có độ sẵn sàng cao không được phép dừng hoạt động để bảo trì hoặc cập nhật phiên bản phần mềm mới. Bài toán đặt ra là thiết kế quy trình triển khai sao cho phiên bản mới được cài đặt dần dần lên từng máy chủ trong khi các máy chủ còn lại vẫn phục vụ khách hàng. Hệ thống cân bằng tải phải phối hợp nhịp nhàng để tạm dừng gửi yêu cầu đến máy chủ đang cập nhật và chỉ mở lại khi máy chủ đó đã sẵn sàng với phiên bản mới, đảm bảo người dùng không bao giờ nhìn thấy trang báo lỗi bảo trì.
