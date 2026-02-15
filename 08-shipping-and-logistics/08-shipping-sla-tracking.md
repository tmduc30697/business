# Shipping SLA tracking

### Quản lý cấu hình SLA linh hoạt theo vùng địa lý và loại dịch vụ

Bài toán đặt ra là hệ thống cần cho phép thiết lập các cam kết thời gian giao hàng khác nhau dựa trên điểm đi, điểm đến và phương thức vận chuyển. Ví dụ, giao hàng nội thành bằng xe máy có SLA là 4 giờ, trong khi giao hàng liên tỉnh bằng xe tải có SLA là 3 ngày. Bạn cần thiết kế cách lưu trữ các quy tắc này sao cho khi một đơn hàng được tạo, hệ thống tự động tính toán được thời gian "hết hạn" dự kiến. Thách thức nằm ở việc quản lý các ngoại lệ như ngày lễ, ngày nghỉ cuối tuần hoặc các khu vực vùng sâu vùng xa có thời gian xử lý đặc thù.

### Theo dõi trạng thái đơn hàng và cảnh báo vi phạm theo thời gian thực

Khi đơn hàng lưu thông qua các trạm trung chuyển, hệ thống phải liên tục cập nhật trạng thái và so sánh với mốc thời gian cam kết. Bài toán yêu cầu thiết kế cơ chế để phát hiện ngay lập tức các đơn hàng có nguy cơ chậm trễ (at-risk) hoặc đã chính thức quá hạn (breached). Điều này đòi hỏi một kiến trúc xử lý sự kiện hiệu quả để không chỉ cập nhật database mà còn có thể kích hoạt các dịch vụ thông báo hoặc đẩy dữ liệu lên bảng điều khiển giám sát trực tuyến cho bộ phận vận hành.

### Xử lý logic dừng đếm ngược SLA khi có lỗi từ phía khách hàng

Trong thực tế, không phải mọi sự chậm trễ đều do đơn vị vận chuyển. Bài toán này tập trung vào việc quản lý các trạng thái "tạm dừng" SLA. Ví dụ, khi shipper không liên lạc được với người mua, hoặc khách hàng hẹn lại lịch giao vào ngày khác, đồng hồ tính SLA phải được tạm dừng hoặc điều chỉnh lại mốc kết thúc. Bạn cần thiết kế database để lưu vết các khoảng thời gian gián đoạn này nhằm đảm bảo kết quả đánh giá hiệu suất cuối cùng cho nhân viên giao hàng là công bằng và chính xác.

### Phân tích hiệu suất đối tác vận chuyển thứ ba (3PL)

Nhiều doanh nghiệp không tự giao hàng mà sử dụng các đơn vị vận chuyển trung gian. Bài toán ở đây là tích hợp dữ liệu từ nhiều API khác nhau của các đối tác để đồng bộ trạng thái về hệ thống quản trị tập trung. Bạn cần thiết kế một mô hình dữ liệu chung có khả năng chuẩn hóa các trạng thái vận chuyển khác nhau từ nhiều nhà cung cấp về một chuẩn nội bộ, từ đó tính toán xem đối tác nào thường xuyên vi phạm SLA nhất và ở chặng vận chuyển nào.

### Hệ thống báo cáo tổng hợp và chấm điểm chất lượng vận hành

Dữ liệu SLA sau khi thu thập cần được tổng hợp thành các chỉ số như tỷ lệ đơn hàng đúng hạn, thời gian trễ trung bình, hoặc tỷ lệ hoàn thành chặng đầu. Bài toán này yêu cầu thiết kế các truy vấn hoặc cấu trúc kho dữ liệu sao cho việc trích xuất báo cáo theo tuần, tháng, quý cho hàng triệu đơn hàng diễn ra nhanh chóng. Việc lưu trữ dữ liệu lịch sử và kết quả tính toán sẵn (pre-aggregation) là yếu tố then chốt để phục vụ các dashboard phân tích xu hướng hiệu suất.

### Quản lý quy trình khiếu nại và điều chỉnh SLA thủ công

Đôi khi có những sự cố bất khả kháng như thiên tai, bão lũ khiến toàn bộ các đơn hàng trong một khu vực bị chậm trễ. Bài toán đặt ra là thiết kế tính năng cho phép quản trị viên điều chỉnh hàng loạt mốc cam kết SLA hoặc đánh dấu ngoại lệ cho các đơn hàng cụ thể. Hệ thống cần lưu lại lịch sử thay đổi (audit log) chi tiết bao gồm người thực hiện, lý do thay đổi và giá trị trước/sau khi điều chỉnh để đảm bảo tính minh bạch trong việc đánh giá KPI.

### Dự báo nguy cơ muộn đơn hàng dựa trên dữ liệu vận hành lịch sử

Dựa trên dữ liệu SLA của quá khứ, bài toán này hướng đến việc thiết kế một module thông minh có khả năng cảnh báo sớm. Ví dụ, nếu một kho hàng đang có lượng đơn tồn đọng vượt quá mức xử lý bình thường, hệ thống cần tính toán được xác suất các đơn hàng mới tạo sẽ bị vi phạm SLA trong tương lai gần. Việc này đòi hỏi cấu trúc dữ liệu phải hỗ trợ tốt cho việc truy vấn các thông số về tải trọng kho và năng suất xử lý tại từng nút trong mạng lưới giao nhận.

### Tối ưu hóa phân bổ đơn hàng dựa trên cam kết SLA còn lại

Khi có nhiều đơn hàng cần xử lý cùng lúc tại kho, việc quyết định đơn hàng nào được đóng gói và vận chuyển trước là rất quan trọng. Bài toán yêu cầu thiết kế logic ưu tiên dựa trên thời gian SLA còn lại (Remaining Time). Những đơn hàng sắp chạm mốc hết hạn phải được đẩy lên đầu hàng đợi xử lý. Hệ thống API và cơ sở dữ liệu phải hỗ trợ việc sắp xếp và lọc dữ liệu động theo thời gian thực để nhân viên kho luôn biết chính xác danh sách các đơn hàng ưu tiên cao nhất.
