# Monitoring & alerting

### Theo dõi chỉ số hạ tầng và ngưỡng cảnh báo tĩnh

Hệ thống cần thu thập các thông số cơ bản từ hàng trăm máy chủ khác nhau như tỷ lệ sử dụng CPU, dung lượng bộ nhớ RAM còn trống và dung lượng đĩa cứng. Quản trị viên muốn thiết lập các ngưỡng cố định, ví dụ nếu CPU vượt quá tám mươi phần trăm trong vòng năm phút liên tục thì phải gửi thông báo. Bài toán này yêu cầu thiết kế database để lưu trữ chỉ số theo thời gian và một bộ máy kiểm tra điều kiện định kỳ để so khớp dữ liệu thực tế với ngưỡng cấu hình đã đặt trước.

### Giám sát tỷ lệ lỗi HTTP và mã phản hồi từ API Gateway

Trong một hệ thống microservices, việc theo dõi sức khỏe của các luồng API là cực kỳ quan trọng. Bài toán đặt ra là phải thống kê số lượng yêu cầu thành công và thất bại dựa trên mã trạng thái trả về. Nếu tỷ lệ lỗi năm trăm (Internal Server Error) tăng đột biến vượt quá năm phần trăm tổng lưu lượng trong một khoảng thời gian ngắn, hệ thống phải kích hoạt cảnh báo đỏ. Bạn cần thiết kế cách gom nhóm dữ liệu theo endpoint và tính toán tỷ lệ phần trăm theo thời gian thực.

### Đo lường độ trễ của các dịch vụ quan trọng theo phân vị

Chỉ theo dõi độ trễ trung bình thường không phản ánh đúng trải nghiệm của người dùng thực tế vì các giá trị ngoại lai có thể bị che lấp. Bài toán yêu cầu hệ thống phải tính toán được độ trễ ở các mức phân vị như chín mươi lăm hoặc chín mươi chín. Nếu chín mươi lăm phần trăm người dùng phản hồi chậm hơn hai giây, hệ thống cần gửi cảnh báo cho đội tối ưu hóa hiệu năng. Điều này đòi hỏi thiết kế hệ thống lưu trữ có khả năng tính toán thống kê nhanh trên tập dữ liệu lớn.

### Quản lý thông báo đa kênh và phân cấp mức độ nghiêm trọng

Khi sự cố xảy ra, không phải cảnh báo nào cũng có mức độ ưu tiên như nhau. Hệ thống cần phân loại cảnh báo thành các mức như thông tin, cảnh báo nhẹ hoặc lỗi nghiêm trọng. Tùy vào mức độ, thông báo sẽ được gửi qua các kênh khác nhau như tin nhắn nội bộ, email hoặc gọi điện trực tiếp cho kỹ sư đang trực. Bài toán này tập trung vào thiết kế API và Database để quản lý cấu hình người nhận, lịch trực (on-call) và đảm bảo thông báo không bị lặp lại quá nhiều gây nhiễu.

### Phát hiện sự bất thường dựa trên dữ liệu lịch sử

Thay vì dùng ngưỡng cố định, hệ thống cần so sánh dữ liệu hiện tại với dữ liệu cùng kỳ tuần trước hoặc tháng trước. Ví dụ, nếu lưu lượng truy cập vào lúc hai giờ sáng hôm nay cao gấp mười lần so với trung bình các ngày thứ Hai khác, đó có thể là một cuộc tấn công từ chối dịch vụ hoặc lỗi logic. Bài toán yêu cầu bạn thiết kế cách truy vấn dữ liệu quá khứ một cách hiệu quả và thuật toán so sánh đơn giản để phát hiện các biến động bất thường mà ngưỡng tĩnh không bắt được.

### Giám sát thời hạn chứng chỉ số và tài nguyên bên ngoài

Ngoài các thông số nội bộ, hệ thống cần theo dõi các yếu tố bên ngoài như ngày hết hạn của chứng chỉ bảo mật SSL hoặc số dư trong tài khoản API của bên thứ ba. Nếu chứng chỉ SSL còn dưới ba mươi ngày là hết hạn, hệ thống phải nhắc nhở mỗi ngày một lần. Nếu tài khoản thanh toán sắp hết tiền, cảnh báo phải gửi đến bộ phận tài chính. Bài toán này giúp bạn luyện tập về việc lập lịch các tác vụ kiểm tra (cron jobs) và quản lý trạng thái của các thực thể phi kỹ thuật.

### Cơ chế dập tắt cảnh báo và gom nhóm sự cố trùng lặp

Trong một sự cố dây chuyền, hàng nghìn cảnh báo có thể đổ về cùng một lúc khiến đội ngũ kỹ thuật bị quá tải thông tin. Hệ thống cần có khả năng gom nhóm các cảnh báo có cùng nguyên nhân gốc vào một sự cố duy nhất. Đồng thời, kỹ sư phải có khả năng tạm dừng (silence) một cảnh báo trong một khoảng thời gian nhất định khi họ đang trong quá trình xử lý. Đây là bài toán về thiết kế logic xử lý trạng thái cảnh báo và quan hệ giữa các sự kiện trong database.

### Theo dõi hành trình người dùng và tỷ lệ chuyển đổi đơn hàng

Đây là bài toán giám sát ở mức độ nghiệp vụ thay vì mức hạ tầng. Hệ thống theo dõi số lượng người dùng thêm hàng vào giỏ nhưng không thể tiến hành thanh toán do lỗi hệ thống. Nếu tỷ lệ chuyển đổi từ bước chọn hàng sang bước thanh toán giảm đột ngột xuống mức thấp bất thường so với cấu hình mong đợi, một cảnh báo kinh doanh sẽ được phát ra. Bài toán này yêu cầu sự kết hợp dữ liệu giữa log hành vi người dùng và trạng thái hoạt động của hệ thống.
