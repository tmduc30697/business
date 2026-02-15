# Order confirmation

### Quản lý trạng thái xác nhận đa kênh theo ưu tiên

Bài toán yêu cầu hệ thống phải gửi xác nhận đơn hàng qua nhiều kênh khác nhau nhưng theo một thứ tự ưu tiên nhất định để tối ưu chi phí. Ví dụ, hệ thống sẽ ưu tiên gửi thông báo qua ứng dụng trước, nếu sau một khoảng thời gian người dùng không đọc hoặc không nhận được thì mới tiếp tục gửi qua tin nhắn văn bản và cuối cùng là thư điện tử. Bạn cần thiết kế cách lưu trữ trạng thái của từng loại thông báo, thời gian chờ giữa các bước và đảm bảo người dùng không bị làm phiền bởi cùng một nội dung trên tất cả các kênh nếu họ đã xác nhận đơn hàng ở kênh đầu tiên.

### Hệ thống mẫu nội dung linh hoạt cho từng loại sản phẩm

Trong thực tế, nội dung xác nhận đơn hàng của một món đồ điện tử sẽ khác hoàn toàn với một đơn hàng dịch vụ như đặt phòng khách sạn hay vé máy bay. Bài toán đặt ra là làm thế nào để quản lý các mẫu nội dung xác nhận khác nhau trong cơ sở dữ liệu, hỗ trợ đa ngôn ngữ và cho phép chèn các thông tin động như tên khách hàng, mã đơn hàng, danh sách sản phẩm. Bạn phải tính toán cách tổ chức dữ liệu để khi có một đơn hàng mới, hệ thống có thể truy xuất đúng mẫu tương ứng dựa trên loại sản phẩm và ngôn ngữ của người dùng.

### Đảm bảo tính nhất quán của dữ liệu khi đơn hàng bị chỉnh sửa

Một vấn đề thường gặp là khách hàng hoặc nhân viên vận hành thay đổi thông tin đơn hàng ngay sau khi đơn hàng vừa được tạo nhưng thông báo xác nhận đầu tiên đã được gửi đi. Bài toán yêu cầu thiết kế logic xử lý để hệ thống biết khi nào cần gửi một thông báo cập nhật, làm thế nào để liên kết thông báo mới với thông báo cũ và đảm bảo thông tin trong email hay tin nhắn luôn khớp với trạng thái thực tế trong cơ sở dữ liệu đơn hàng tại thời điểm gửi.

### Xử lý lưu lượng lớn và cơ chế hàng đợi thông báo

Khi có các chương trình khuyến mãi lớn, hàng nghìn đơn hàng được tạo ra trong mỗi giây dẫn đến việc hệ thống gửi thông báo bị quá tải. Bài toán này tập trung vào việc thiết kế hệ thống trung gian để tiếp nhận yêu cầu gửi xác nhận, phân loại mức độ khẩn cấp và đẩy vào các hàng đợi xử lý riêng biệt. Bạn cần giải quyết vấn đề làm sao để việc gửi thông báo không làm chậm quá trình thanh toán của khách hàng và cách xử lý nếu các dịch vụ bên thứ ba như nhà cung cấp dịch vụ tin nhắn hoặc email gặp sự cố.

### Theo dõi tương tác và tỷ lệ gửi thành công

Để đánh giá hiệu quả, doanh nghiệp cần biết chính xác liệu khách hàng đã nhận được xác nhận đơn hàng hay chưa và họ có nhấn vào các liên kết bên trong hay không. Bài toán yêu cầu bạn thiết kế các bảng lưu trữ lịch sử tương tác, ghi lại các sự kiện như đã gửi, đã nhận, đã mở hoặc lỗi từ phía nhà mạng. Điều này đòi hỏi thiết kế API để tiếp nhận các phản hồi ngược từ nhà cung cấp dịch vụ và cập nhật lại trạng thái thông báo trong hệ thống của bạn một cách chính xác.

### Quản lý chính sách bảo mật và quyền riêng tư trong thông báo

Xác nhận đơn hàng thường chứa các thông tin nhạy cảm như địa chỉ nhà, số điện thoại và chi tiết thanh toán. Bài toán đặt ra là làm thế nào để thiết kế hệ thống xác nhận đơn hàng tuân thủ các quy định về bảo mật thông tin. Bạn cần cân nhắc việc mã hóa dữ liệu trong database, quy định thời gian tồn tại của các liên kết xem đơn hàng trực tuyến và cách ẩn bớt các thông tin nhạy cảm trên các kênh không bảo mật như tin nhắn văn bản mà vẫn đảm bảo khách hàng nhận diện được đơn hàng của mình.

### Tích hợp mã giảm giá và khảo sát vào thông báo xác nhận

Nhiều doanh nghiệp muốn tận dụng email xác nhận đơn hàng để thực hiện các chiến dịch marketing như tặng mã giảm giá cho đơn hàng sau hoặc mời khách hàng tham gia khảo sát. Bài toán yêu cầu bạn thiết kế cấu trúc dữ liệu sao cho các chiến dịch này có thể được cấu hình linh hoạt cho từng nhóm khách hàng hoặc từng giá trị đơn hàng cụ thể. Hệ thống cần ghi nhận được mã giảm giá nào đã được đính kèm vào thông báo nào để tránh việc gửi trùng lặp hoặc gian lận.

### Hệ thống đối soát và báo cáo chi phí gửi thông báo

Mỗi tin nhắn hay email gửi đi đều tốn một khoản chi phí nhất định. Bài toán thực tế là thiết kế một module quản lý ngân sách và đối soát, nơi hệ thống tự động tính toán chi phí dự kiến dựa trên số lượng thông báo đã gửi qua từng kênh. Bạn cần thiết kế database để lưu trữ đơn giá của từng nhà cung cấp theo từng thời điểm và tạo ra các báo cáo tổng hợp để bộ phận tài chính có thể đối chiếu với hóa đơn thực tế từ các đối tác viễn thông.
