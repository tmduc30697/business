# Push campaign

### Gửi thông báo đẩy hàng loạt theo phân khúc nhân khẩu học

Bộ phận vận hành muốn gửi một thông báo khuyến mãi đến tất cả người dùng nữ, độ tuổi từ 18 đến 25, hiện đang sinh sống tại thành phố Hồ Chí Minh. Bài toán này yêu cầu thiết kế cơ sở dữ liệu người dùng với các trường thông tin chi tiết và khả năng truy vấn nhanh chóng để trích xuất danh sách hàng triệu thiết bị mục tiêu. Hệ thống cần quản lý được danh sách các Device Token tương ứng với từng tài khoản trên nhiều nền tảng như Android, iOS và Web Browser.

### Tự động gửi thông báo nhắc nhở giỏ hàng bị bỏ quên

Hệ thống cần theo dõi hành vi người dùng trong thời gian thực. Khi một khách hàng thêm sản phẩm vào giỏ hàng nhưng không tiến hành thanh toán trong vòng 2 giờ, một thông báo đẩy cá nhân hóa sẽ được gửi đi để nhắc nhở họ. Bài toán này đòi hỏi thiết kế một cơ chế hàng đợi hoặc lập lịch kiểm tra trạng thái đơn hàng và hành vi người dùng để kích hoạt thông báo đúng thời điểm, tránh gửi sai đối tượng đã hoàn tất thanh toán trước đó.

### Chiến dịch gửi thông báo dựa trên vị trí địa lý thời gian thực

Một ứng dụng đồ ăn muốn gửi mã giảm giá cho người dùng khi họ đi vào bán kính 500 mét quanh một cửa hàng cụ thể đang có chương trình ưu đãi. Hệ thống cần lưu trữ tọa độ của các cửa hàng và xử lý luồng dữ liệu vị trí liên tục từ thiết bị người dùng gửi lên. Thách thức ở đây là thiết kế API nhận dữ liệu vị trí và logic so khớp không gian để quyết định có đẩy thông báo hay không mà không làm tiêu tốn quá nhiều pin điện thoại.

### Cá nhân hóa nội dung thông báo theo lịch sử xem sản phẩm

Thay vì gửi nội dung giống nhau, hệ thống sẽ gửi thông báo đẩy chứa tên sản phẩm và hình ảnh của món hàng mà người dùng đã xem nhiều nhất trong 7 ngày qua nhưng chưa mua. Bài toán này tập trung vào việc thiết kế bảng lưu trữ log hành vi (Activity Log) và cách liên kết dữ liệu này với nội dung của chiến dịch thông báo để tạo ra các biến nội dung động cho từng người nhận khác nhau.

### Quản lý tần suất và khung giờ gửi thông báo tránh gây phiền hà

Để tránh việc người dùng gỡ ứng dụng do bị làm phiền quá nhiều, hệ thống cần thiết lập giới hạn số lượng thông báo đẩy tối đa một người có thể nhận trong một ngày. Ngoài ra, hệ thống phải tự động tránh gửi thông báo vào khung giờ nghỉ đêm của người dùng dựa trên múi giờ địa phương của họ. Điều này yêu cầu thiết kế database quản lý cấu hình cấu hình thông báo (Notification Settings) và bộ đếm số lượng thông báo đã gửi trong ngày cho mỗi thiết bị.

### Gửi thông báo đẩy theo tiến độ của một sự kiện trực tiếp

Trong một trận bóng đá hoặc một phiên đấu giá trực tiếp, thông báo cần được gửi đến hàng triệu người dùng cùng lúc ngay khi có bàn thắng hoặc có người trả giá cao hơn. Bài toán này tập trung vào thiết kế hệ thống có khả năng chịu tải cao, sử dụng các cơ chế hàng đợi tin nhắn (Message Queue) để phân tán và đẩy tin nhắn đi với độ trễ thấp nhất có thể, đảm bảo tính thời sự của thông tin.

### Theo dõi hiệu quả chiến dịch qua tỷ lệ mở và chuyển đổi

Sau khi gửi thông báo, doanh nghiệp cần biết có bao nhiêu người đã nhận được, bao nhiêu người đã nhấn vào thông báo và bao nhiêu người thực hiện hành vi mua hàng từ thông báo đó. Bài toán này yêu cầu thiết kế các bảng lưu trữ sự kiện (Event Tracking) với dung lượng lớn và API để ghi nhận lại các hành động click từ thiết bị. Dữ liệu này sau đó phải được tổng hợp để báo cáo hiệu quả của từng chiến dịch cụ thể.

### Phân loại và ưu tiên mức độ quan trọng của thông báo

Hệ thống cần phân loại thông báo thành nhiều cấp độ như thông báo hệ thống (mất tiền, đổi mật khẩu), thông báo tương tác (có người thích ảnh) và thông báo quảng cáo. Thông báo hệ thống phải được ưu tiên gửi đi ngay lập tức, trong khi thông báo quảng cáo có thể được gửi chậm hơn trong các đợt xử lý nền. Bài toán này đòi hỏi thiết kế kiến trúc Priority Queue và logic điều phối thông điệp để đảm bảo các tin nhắn quan trọng không bị kẹt sau các chiến dịch marketing lớn.
