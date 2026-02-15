# GDPR data export

### Xuất dữ liệu từ kiến trúc Microservices đa nền tảng

Trong một hệ thống thương mại điện tử lớn, thông tin người dùng bị phân tán ở nhiều dịch vụ khác nhau như dịch vụ đơn hàng, dịch vụ thanh toán, dịch vụ hồ sơ cá nhân và dịch vụ đánh giá sản phẩm. Thử thách là phải thiết kế một cơ chế điều phối để thu thập dữ liệu từ tất cả các cơ sở dữ liệu riêng biệt này, đảm bảo tính nhất quán của dữ liệu tại thời điểm xuất và đóng gói chúng thành một tệp tin duy nhất mà không làm treo hệ thống do truy vấn quá nhiều.

### Quản lý hàng đợi và xử lý tác vụ nền cho tệp tin dung lượng lớn

Khi người dùng có lịch sử hoạt động kéo dài nhiều năm, tệp dữ liệu xuất ra có thể lên đến hàng Gigabyte. Hệ thống không thể xử lý yêu cầu này ngay lập tức trong luồng HTTP request thông thường. Bạn cần thiết kế một hệ thống hàng đợi để tiếp nhận yêu cầu, một worker để xử lý việc nén dữ liệu và cơ chế thông báo cho người dùng qua email hoặc notification khi tệp tin đã sẵn sàng để tải xuống.

### Phân quyền và bảo mật tệp tin sau khi trích xuất

Tệp dữ liệu xuất ra chứa những thông tin nhạy cảm nhất của người dùng. Bài toán đặt ra là làm thế nào để lưu trữ tệp tin này trên các kho lưu trữ đám mây một cách an toàn, thiết lập thời gian hết hạn cho đường dẫn tải xuống và đảm bảo rằng chỉ chính người dùng đó mới có thể truy cập được tệp tin, ngay cả khi đường dẫn bị lộ ra ngoài.

### Theo dõi trạng thái và giới hạn tần suất yêu cầu

Để tránh việc bị tấn công từ chối dịch vụ hoặc lạm dụng tài nguyên, hệ thống cần ghi lại lịch sử các lần yêu cầu xuất dữ liệu. Bạn cần thiết kế bảng lưu trữ trạng thái của từng yêu cầu (đang chờ, đang xử lý, hoàn thành, thất bại) và áp dụng quy tắc kinh doanh như mỗi người dùng chỉ được phép yêu cầu xuất dữ liệu tối đa một lần trong vòng ba mươi ngày.

### Định dạng dữ liệu chuẩn hóa và khả năng tương thích

Dữ liệu trong cơ sở dữ liệu thường ở dạng quan hệ phức tạp với nhiều khóa ngoại và cấu trúc lồng nhau. Bài toán yêu cầu bạn phải chuyển đổi các bảng dữ liệu thô này sang các định dạng máy có thể đọc được như JSON hoặc CSV theo một lược đồ chuẩn hóa. Cấu trúc này phải đủ rõ ràng để người dùng có thể hiểu được hoặc dễ dàng nhập vào một hệ thống khác mà không làm mất đi ý nghĩa của thông tin.

### Xử lý dữ liệu đa phương tiện đính kèm

Người dùng trên các nền tảng mạng xã hội không chỉ có dữ liệu văn bản mà còn có hàng nghìn hình ảnh và video. Khi thực hiện xuất dữ liệu, hệ thống phải thu thập các tệp tin vật lý này từ các server lưu trữ khác nhau, tổ chức chúng vào các thư mục logic và nén lại cùng với các tệp dữ liệu văn bản mà vẫn đảm bảo hiệu suất đường truyền và không vượt quá giới hạn bộ nhớ đệm của server xử lý.

### Xóa dữ liệu tạm thời và dọn dẹp tài nguyên

Sau khi người dùng đã tải xuống tệp dữ liệu hoặc sau khi liên kết tải xuống hết hạn, hệ thống cần một cơ chế tự động để xóa bỏ các tệp tin nén này trên server hoặc cloud storage để tiết kiệm chi phí và đảm bảo an toàn thông tin. Việc thiết kế các tiến trình chạy ngầm để quét và dọn dẹp các tài nguyên rác này là một phần quan trọng trong quản trị hệ thống.

### Ghi nhật ký kiểm soát tuân thủ

Theo yêu cầu của GDPR, tổ chức phải chứng minh được rằng họ đã phản hồi yêu cầu của người dùng trong thời hạn quy định. Bạn cần thiết kế một hệ thống logging không thể thay đổi để ghi lại toàn bộ vòng đời của một yêu cầu xuất dữ liệu, từ lúc tiếp nhận, danh sách các loại dữ liệu đã được trích xuất, cho đến khi tệp tin được bàn giao thành công cho người dùng.
