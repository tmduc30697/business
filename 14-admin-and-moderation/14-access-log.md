# Access log

### Truy vết hành động người dùng để hỗ trợ kỹ thuật

Khi một khách hàng báo cáo rằng họ gặp lỗi mất dữ liệu hoặc không thể thực hiện giao dịch, nhân viên hỗ trợ cần biết chính xác khách hàng đó đã nhấn vào những đâu, sử dụng thiết bị gì và thực hiện các bước nào trước khi lỗi xảy ra. Hệ thống cần khả năng lọc toàn bộ lịch sử truy cập theo mã định danh người dùng trong một khoảng thời gian cụ thể, sắp xếp theo thứ tự thời gian để tái hiện lại hành trình của họ trên ứng dụng hoặc website.

### Phát hiện và ngăn chặn đăng nhập trái phép từ vị trí lạ

Hệ thống cần theo dõi địa chỉ IP và vị trí địa lý của mỗi lần đăng nhập thành công. Nếu một tài khoản thường xuyên đăng nhập tại Hà Nội nhưng đột ngột có một truy cập từ một quốc gia khác trong thời gian ngắn, hệ thống phải ghi nhận sự bất thường này dựa trên lịch sử log. Bài toán này yêu cầu bạn thiết kế cơ sở dữ liệu sao cho có thể so sánh nhanh chóng thông tin truy cập hiện tại với các bản ghi lịch sử gần nhất của cùng một tài khoản.

### Thống kê lưu lượng truy cập theo thiết bị để tối ưu hóa giao diện

Bộ phận phát triển sản phẩm cần biết tỷ lệ người dùng truy cập bằng điện thoại so với máy tính, cũng như các phiên bản hệ điều hành phổ biến đang được sử dụng. Bằng cách phân tích thông tin thiết bị trong Access Log, hệ thống phải xuất được báo cáo về số lượng người dùng theo từng loại trình duyệt hoặc đời máy. Dữ liệu này giúp đội ngũ thiết kế quyết định nên ưu tiên tối ưu hóa giao diện cho kích thước màn hình nào để mang lại trải nghiệm tốt nhất.

### Xây dựng hệ thống cảnh báo tấn công từ chối dịch vụ

Một dấu hiệu phổ biến của các cuộc tấn công mạng là một địa chỉ IP gửi hàng nghìn yêu cầu truy cập đến hệ thống trong một vài giây. Access Log đóng vai trò là nguồn dữ liệu đầu vào để hệ thống đếm số lượng hành động từ mỗi IP theo thời gian thực. Nếu một IP vượt quá ngưỡng cho phép, hệ thống sẽ tự động đưa IP đó vào danh sách đen. Bài toán này đòi hỏi thiết kế hệ thống có khả năng ghi log cực nhanh mà không làm chậm tốc độ phản hồi của ứng dụng chính.

### Quản lý phiên làm việc và đăng xuất từ xa

Nhiều ứng dụng hiện đại cho phép người dùng xem danh sách các thiết bị đang đăng nhập vào tài khoản của họ và thực hiện đăng xuất từ xa nếu thấy nghi ngờ. Để làm được điều này, Access Log phải lưu giữ trạng thái của các phiên làm việc đang hoạt động, bao gồm lần cuối cùng thiết bị đó tương tác với hệ thống là khi nào. Khi người dùng nhấn nút đăng xuất một thiết bị, hệ thống sẽ dựa vào thông tin log để vô hiệu hóa token tương ứng của thiết bị đó.

### Phân tích hiệu năng hệ thống dựa trên thời gian phản hồi

Ngoài các thông tin về danh tính, Access Log thường ghi lại thời gian cần thiết để hệ thống xử lý xong một yêu cầu từ phía người dùng. Bằng cách tổng hợp dữ liệu này, đội ngũ vận hành có thể xác định được những đường dẫn API nào đang phản hồi chậm hoặc những khung giờ nào hệ thống đang bị quá tải. Đây là bài toán về xử lý dữ liệu tổng hợp từ hàng triệu dòng log để tìm ra các điểm nghẽn về hiệu năng.

### Kiểm toán dữ liệu và tuân thủ quy định pháp luật

Trong các hệ thống tài chính hoặc y tế, việc ghi lại ai đã xem hoặc chỉnh sửa thông tin nhạy cảm là bắt buộc theo quy định pháp luật. Access Log cần lưu trữ chi tiết hành động xem dữ liệu kèm theo định danh người thực hiện để phục vụ công tác thanh tra sau này. Đặc điểm của bài toán này là dữ liệu log phải được đảm bảo tính toàn vẹn, không thể bị xóa hoặc sửa đổi bởi bất kỳ ai, kể cả quản trị viên hệ thống.

### Phân tích tỷ lệ chuyển đổi và hành vi người dùng trong phễu bán hàng

Doanh nghiệp muốn biết có bao nhiêu người dùng nhấn vào xem sản phẩm nhưng sau đó không nhấn vào nút thanh toán. Bằng cách phân tích Access Log theo chuỗi hành động, hệ thống có thể xây dựng biểu đồ hình phễu để chỉ ra bước nào người dùng rời bỏ ứng dụng nhiều nhất. Điều này yêu cầu thiết kế database có khả năng liên kết các hành động rời rạc của cùng một phiên truy cập thành một chuỗi sự kiện có ý nghĩa.
