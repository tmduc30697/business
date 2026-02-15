# SLA monitoring

### Theo dõi thời gian phản hồi đầu tiên của nhân viên hỗ trợ

Trong hệ thống chăm sóc khách hàng, mỗi khi có một yêu cầu mới được gửi đến, hệ thống cần ghi nhận thời điểm bắt đầu. Cam kết dịch vụ quy định nhân viên phải có phản hồi đầu tiên trong vòng 30 phút kể từ khi khách hàng tạo phiếu hỗ trợ. Bài toán đặt ra là làm sao để lưu trữ trạng thái phản hồi, xác định thời điểm chính xác nhân viên gửi tin nhắn đầu tiên và tính toán xem khoảng thời gian đó có nằm trong hạn mức cho phép hay không để đánh giá hiệu suất nhân viên.

### Tính toán thời hạn xử lý đơn hàng theo giờ làm việc hành chính

Một doanh nghiệp cam kết xử lý đơn hàng trong vòng 8 tiếng làm việc. Tuy nhiên, thời gian này không tính các ngày cuối tuần và các khung giờ ngoài giờ hành chính (từ 18h tối đến 8h sáng hôm sau). Nếu đơn hàng đặt vào lúc 17h chiều thứ Sáu, hệ thống phải tự động tính toán chính xác thời điểm hết hạn (deadline) rơi vào sáng thứ Hai tuần tới thay vì tính cộng dồn 8 tiếng liên tục. Điều này yêu cầu thiết kế database phải quản lý được lịch làm việc và ngày nghỉ lễ của công ty.

### Hệ thống cảnh báo nhiều cấp độ khi sắp vi phạm thời gian xử lý

Để ngăn chặn việc vi phạm cam kết, hệ thống cần một cơ chế theo dõi và đưa ra các cảnh báo sớm. Ví dụ, nếu một khiếu nại chưa được xử lý sau 50% thời gian quy định, hệ thống gửi thông báo nhắc nhở cho nhân viên. Nếu đạt mức 75% thời gian mà vẫn chưa xong, hệ thống gửi cảnh báo cho quản lý cấp cao. Bài toán này đòi hỏi thiết kế một bảng ghi nhận các ngưỡng cảnh báo và trạng thái gửi thông báo để tránh việc gửi trùng lặp hoặc bỏ sót các mốc thời gian quan trọng.

### Quản lý trạng thái tạm dừng SLA khi chờ khách hàng phản hồi

Trong quá trình xử lý sự cố, nhân viên hỗ trợ thường phải yêu cầu khách hàng cung cấp thêm thông tin. Trong thời gian chờ khách hàng trả lời, đồng hồ tính thời gian SLA cần được tạm dừng và chỉ tiếp tục chạy lại khi khách hàng phản hồi. Hệ thống cần lưu trữ các khoảng thời gian bắt đầu tạm dừng và thời điểm tiếp tục để tính toán tổng thời gian xử lý thực tế mà nhân viên đã bỏ ra, loại bỏ thời gian chờ khách quan.

### Theo dõi cam kết về tỷ lệ khả dụng của dịch vụ hệ thống

Một nhà cung cấp dịch vụ máy chủ cam kết tỷ lệ hoạt động của hệ thống phải đạt mức 99,9% mỗi tháng. Điều này yêu cầu hệ thống giám sát phải ghi lại chính xác từng thời điểm hệ thống gặp sự cố (downtime) và thời điểm hoạt động trở lại bình thường (uptime). Bài toán thiết kế ở đây là làm sao để tổng hợp dữ liệu từ các bản ghi sự cố lẻ tẻ thành một báo cáo tỷ lệ phần trăm theo tháng cho từng khách hàng cụ thể dựa trên hợp đồng của họ.

### Phân cấp độ ưu tiên của khách hàng để áp dụng các gói SLA khác nhau

Một công ty cung cấp phần mềm có nhiều gói dịch vụ như Đồng, Bạc và Vàng. Khách hàng gói Vàng được cam kết xử lý sự cố trong 2 tiếng, trong khi gói Đồng là 24 tiếng. Khi một yêu cầu được gửi lên, hệ thống phải tự động truy vấn phân hạng của khách hàng đó để gán thời hạn xử lý tương ứng. Điều này yêu cầu cấu trúc database phải có sự liên kết chặt chẽ giữa thông tin tài khoản, gói dịch vụ và các cấu hình quy tắc thời gian xử lý.

### Ghi nhận và báo cáo lý do vi phạm SLA để cải thiện quy trình

Khi một chỉ số cam kết dịch vụ bị vi phạm, hệ thống không chỉ ghi nhận việc vi phạm mà còn yêu cầu nhân viên hoặc quản lý nhập vào lý do cụ thể từ một danh mục có sẵn. Việc thiết kế database cần hỗ trợ lưu trữ các thông tin hậu kiểm này để phục vụ việc trích xuất báo cáo phân tích cuối tháng, giúp doanh nghiệp nhận diện được các khâu yếu kém thường xuyên gây ra chậm trễ trong quy trình vận hành.

### Tự động chuyển cấp xử lý khi vượt quá thời gian cam kết

Để đảm bảo mọi vấn đề của khách hàng đều được giải quyết, hệ thống cần tính năng tự động chuyển yêu cầu lên cấp cao hơn nếu nhân viên hiện tại không hoàn thành đúng thời hạn. Ví dụ, nếu sau 4 tiếng mà một sự cố kỹ thuật chưa được xác nhận, hệ thống sẽ tự động thay đổi người phụ trách sang cấp trưởng phòng. Bài toán này yêu cầu thiết kế logic xử lý ngầm (background job) và cập nhật lịch sử chuyển giao công việc một cách minh bạch trong cơ sở dữ liệu.
