# Auto reply

### Quản lý kịch bản phản hồi theo khung giờ làm việc

Chủ cửa hàng muốn thiết lập các mẫu tin nhắn khác nhau dựa trên thời gian thực tế. Ví dụ, trong giờ hành chính sẽ gửi lời chào kèm thời gian chờ dự kiến, còn ngoài giờ hành chính hoặc ngày lễ sẽ gửi thông báo tạm nghỉ và hẹn quay lại sau. Hệ thống cần lưu trữ cấu hình múi giờ, danh sách các ngày nghỉ lễ cố định và các khung giờ hoạt động linh hoạt cho từng ngày trong tuần để đối chiếu thời gian thực khi có tin nhắn đến.

### Phân loại phản hồi tự động theo nền tảng bán hàng

Một người bán có thể kinh doanh trên nhiều sàn thương mại điện tử và mạng xã hội khác nhau như Shopee, Lazada, Facebook hay TikTok. Bài toán đặt ra là mỗi nền tảng sẽ có quy định về định dạng tin nhắn và giới hạn ký tự khác nhau. Hệ thống cần quản lý việc kết nối các tài khoản cửa hàng, lưu trữ cấu hình phản hồi riêng biệt cho từng kênh và đảm bảo tin nhắn tự động được gửi đi đúng địa chỉ nguồn mà khách hàng đã liên hệ.

### Phản hồi dựa trên từ khóa và ý định của khách hàng

Thay vì chỉ gửi một tin nhắn chào hỏi chung chung, hệ thống cần nhận diện các từ khóa phổ biến trong tin nhắn khách hàng như giá cả, bảo hành, địa chỉ hoặc tình trạng đơn hàng. Mỗi từ khóa hoặc nhóm từ khóa sẽ kích hoạt một câu trả lời tương ứng đã được thiết lập sẵn. Điều này đòi hỏi việc thiết kế cơ sở dữ liệu có khả năng truy vấn nhanh các quy tắc khớp từ khóa và ưu tiên các phản hồi có độ chính xác cao nhất.

### Giới hạn tần suất gửi tin nhắn tự động để tránh spam

Để tránh việc gửi quá nhiều tin nhắn tự động cho cùng một khách hàng trong một khoảng thời gian ngắn, chủ cửa hàng cần một cơ chế giới hạn. Ví dụ, nếu khách hàng nhắn liên tục 5 tin nhắn trong 1 phút, hệ thống chỉ được phép gửi phản hồi tự động một lần duy nhất. Bài toán này tập trung vào việc lưu vết lịch sử tương tác gần nhất, tính toán thời gian trễ và trạng thái phiên hội thoại để quyết định có kích hoạt trình tự động hay không.

### Tự động trả lời kèm thông tin trạng thái đơn hàng

Khi khách hàng nhắn tin hỏi về việc hàng đã đi đến đâu, hệ thống tự động cần có khả năng truy xuất dữ liệu từ phân hệ quản lý đơn hàng. Nếu tìm thấy đơn hàng gần nhất của khách dựa trên số điện thoại hoặc ID người dùng, tin nhắn phản hồi sẽ bao gồm mã vận đơn và tình trạng vận chuyển hiện tại. Đây là bài toán điển hình về tích hợp dữ liệu giữa các module và thiết kế API nội bộ để lấy thông tin thời gian thực.

### Điều hướng khách hàng đến nhân viên hỗ trợ chuyên trách

Trong trường hợp tin nhắn tự động không giải quyết được vấn đề, hệ thống cần có cơ chế nút bấm hoặc lệnh để khách hàng yêu cầu gặp nhân viên trực tiếp. Bài toán yêu cầu quản lý trạng thái của hội thoại từ tự động sang thủ công và ngược lại. Khi nhân viên đã vào tiếp quản, các tính năng tự động phải tạm dừng cho đến khi hội thoại được đánh dấu là đã hoàn thành để tránh gây nhiễu cho quá trình tư vấn.

### Theo dõi và báo cáo hiệu quả của tin nhắn tự động

Chủ cửa hàng cần biết có bao nhiêu tin nhắn đã được gửi đi, tỷ lệ khách hàng tiếp tục mua hàng sau khi nhận phản hồi tự động là bao nhiêu và những mẫu tin nhắn nào đang hoạt động hiệu quả nhất. Hệ thống cần ghi lại log chi tiết cho mỗi lần kích hoạt tự động, bao gồm thời gian, nội dung gửi, ID khách hàng và hành động tiếp theo của họ để phục vụ cho việc thống kê và hiển thị biểu đồ báo cáo.

### Quản lý tệp tin đính kèm và hình ảnh trong phản hồi tự động

Nhiều trường hợp phản hồi tự động cần gửi kèm hình ảnh bảng giá, sơ đồ chỉ đường hoặc video hướng dẫn sử dụng sản phẩm. Hệ thống cần quản lý kho tài nguyên đa phương tiện, lưu trữ đường dẫn tệp và đảm bảo khi gửi qua các API của bên thứ ba, các định dạng này được chuyển đổi hoặc truyền tải đúng cách. Việc thiết kế database phải tính đến cách lưu trữ metadata của tệp để tối ưu hóa tốc độ tải và gửi tin.
