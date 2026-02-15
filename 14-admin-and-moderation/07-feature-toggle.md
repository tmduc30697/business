# Feature toggle

### Triển khai tính năng mới theo cơ chế Canary Release

Một ứng dụng thương mại điện tử muốn ra mắt giao diện trang thanh toán mới nhưng lo ngại các lỗi tiềm ẩn có thể làm gián đoạn việc mua hàng. Thay vì bật cho tất cả người dùng, hệ thống cần một cơ chế để chỉ cho phép 5% lưu lượng truy cập ngẫu nhiên nhìn thấy giao diện mới, trong khi 95% còn lại vẫn dùng giao diện cũ. Hệ thống phải ghi nhận được người dùng nào đã rơi vào nhóm 5% đó để đảm bảo trải nghiệm của họ đồng nhất trong suốt phiên làm việc và có thể tắt ngay lập tức nếu tỷ lệ lỗi tăng cao.

### Bật tắt tính năng dựa trên gói dịch vụ của người dùng

Một nền tảng phần mềm quản lý doanh nghiệp cung cấp các gói dịch vụ bao gồm Gói Cơ bản, Gói Nâng cao và Gói Chuyên nghiệp. Các tính năng như Xuất báo cáo chuyên sâu hay Tích hợp AI chỉ dành cho người dùng trả phí Gói Chuyên nghiệp. Thay vì viết nhiều câu lệnh điều kiện phức tạp trong mã nguồn, hệ thống cần một bảng cấu hình tập trung để định nghĩa tính năng nào đang được bật cho nhóm khách hàng nào dựa trên định danh gói dịch vụ mà họ đã mua.

### Chế độ bảo trì riêng biệt cho từng phân vùng hệ thống

Trong quá trình nâng cấp cơ sở dữ liệu cho module quản lý kho hàng, hệ thống cần tạm thời khóa tính năng nhập kho để tránh sai lệch dữ liệu, nhưng các tính năng khác như xem danh sách sản phẩm hay đặt hàng vẫn phải hoạt động bình thường. Bài toán yêu cầu thiết kế một cơ chế bật tắt trạng thái bảo trì cho từng module hoặc từng API cụ thể thay vì đánh sập toàn bộ ứng dụng, giúp giảm thiểu tối đa sự bất tiện cho người dùng cuối.

### Thử nghiệm A/B Testing cho chiến dịch marketing

Phòng sản phẩm muốn kiểm tra xem việc thay đổi vị trí nút Đăng ký từ bên trái sang bên phải có giúp tăng tỷ lệ chuyển đổi hay không. Hệ thống cần hỗ trợ chia người dùng thành hai nhóm A và B dựa trên ID người dùng hoặc địa chỉ IP. Mỗi nhóm sẽ được gán một biến cấu hình khác nhau cho cùng một tính năng. Kết quả sau đó sẽ được thu thập để so sánh hiệu quả, đòi hỏi database phải lưu trữ được lịch sử phân bổ người dùng vào các biến thể khác nhau của feature toggle.

### Quản lý tính năng theo môi trường phát triển và thực thi

Hệ thống có nhiều môi trường khác nhau như Phát triển, Kiểm thử, Tiền phát hành và Môi trường thực tế. Có những tính năng như Gửi email hàng loạt hoặc Thanh toán thật chỉ được phép hoạt động trên môi trường thực tế, trong khi các tính năng Debug hay Giả lập thanh toán chỉ được bật ở môi trường kiểm thử. Bài toán đặt ra là làm thế nào để quản lý các flag này một cách tập trung sao cho cùng một bộ mã nguồn khi deploy lên các môi trường khác nhau sẽ tự động kích hoạt đúng các tính năng tương ứng.

### Giới hạn tính năng theo vị trí địa lý của người dùng

Do quy định pháp lý về quyền riêng tư dữ liệu, một mạng xã hội chỉ được phép bật tính năng Định vị vị trí chính xác cho người dùng ở khu vực Đông Nam Á, trong khi người dùng tại Châu Âu sẽ bị tắt tính năng này để tuân thủ luật bảo vệ dữ liệu. Hệ thống cần một cơ chế toggle thông minh có khả năng kiểm tra thông tin quốc gia của người dùng từ hồ sơ hoặc địa chỉ IP để quyết định việc hiển thị hoặc ẩn tính năng đó một cách tự động và chính xác.

### Cho phép người dùng nội bộ dùng thử tính năng sớm

Trước khi ra mắt tính năng nhắn tin video cho cộng đồng, công ty muốn tất cả nhân viên của mình được trải nghiệm trước để tìm lỗi. Hệ thống cần hỗ trợ việc bật tính năng dựa trên danh sách trắng các địa chỉ email có đuôi công ty hoặc dựa trên một thuộc tính định danh nhân viên trong cơ sở dữ liệu. Điều này giúp đội ngũ phát triển nhận được phản hồi thực tế từ môi trường thật mà không làm ảnh hưởng đến tệp khách hàng bên ngoài.

### Tự động tắt tính năng khi hệ thống quá tải

Khi máy chủ đạt đến ngưỡng sử dụng tài nguyên quá cao như CPU vượt quá 90% hoặc bộ nhớ đầy, hệ thống cần một công tắc an toàn tự động tắt bỏ các tính năng phụ tốn tài nguyên như Gợi ý sản phẩm thông minh hay Thống kê thời gian thực. Việc này nhằm ưu tiên tài nguyên cho các tính năng cốt lõi là Tìm kiếm và Đặt hàng. Bài toán này đòi hỏi thiết kế một cơ chế API có thể cập nhật trạng thái toggle cực nhanh để các dịch vụ khác phản ứng kịp thời với sự cố hệ thống.
