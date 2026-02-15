# Timezone handling

### Hiển thị thời gian nhắn tin thời gian thực trong ứng dụng Chat toàn cầu

Một ứng dụng nhắn tin có người dùng ở Việt Nam (UTC+7) và New York (UTC-5) đang trò chuyện với nhau. Khi người dùng ở Việt Nam gửi tin nhắn lúc 8 giờ sáng, hệ thống phải lưu trữ thời gian đó sao cho khi người dùng ở New York nhận được, ứng dụng của họ phải hiển thị đúng thời điểm tương ứng tại địa phương của họ là 8 giờ tối ngày hôm trước. Bài toán này yêu cầu bạn thiết kế cách lưu trữ thời gian đồng nhất ở phía server nhưng vẫn đảm bảo khả năng chuyển đổi linh hoạt ở phía giao diện người dùng.

### Xuất báo cáo doanh thu theo ngày quyết toán của từng chi nhánh

một chuỗi cửa hàng tiện lợi có chi nhánh tại nhiều quốc gia khác nhau. Chủ đầu tư muốn xem báo cáo doanh thu của ngày hôm qua cho tất cả các chi nhánh. Tuy nhiên, khái niệm ngày hôm qua ở chi nhánh Tokyo sẽ kết thúc sớm hơn so với chi nhánh Paris vài tiếng đồng hồ. Hệ thống cần tính toán doanh thu dựa trên múi giờ riêng biệt của từng chi nhánh để đảm bảo con số khớp với thực tế vận hành tại địa phương đó chứ không phải dựa trên giờ của máy chủ đặt tại Mỹ.

### Thiết lập lịch phát sóng livestream và thông báo nhắc hẹn

Một nền tảng học trực tuyến cho phép giáo viên đặt lịch livestream giảng dạy. Giáo viên ở London đặt lịch lúc 10 giờ sáng theo giờ địa phương của họ. Hệ thống phải tính toán và gửi thông báo nhắc hẹn cho hàng ngàn học sinh ở nhiều múi giờ khác nhau sao cho tất cả đều vào học đúng lúc buổi livestream bắt đầu. Bài toán này đòi hỏi việc quản lý lịch trình trong tương lai và xử lý việc thay đổi giờ mùa hè hoặc giờ mùa đông tại một số quốc gia.

### Ghi nhận lịch sử log hệ thống và điều tra sự cố kỹ thuật

Khi một hệ thống phân tán với nhiều máy chủ đặt tại Singapore, Mỹ và Đức cùng ghi nhận lỗi vào một tệp log chung, các mốc thời gian ghi lỗi có thể bị xáo trộn nếu mỗi máy chủ dùng múi giờ địa phương. Điều này khiến kỹ sư phần mềm gặp khó khăn khi truy vết trình tự các sự kiện xảy ra. Bạn cần thiết kế cơ chế ghi log sao cho mọi sự kiện từ các vùng địa lý khác nhau đều có thể được sắp xếp theo một trục thời gian tuyến tính duy nhất để phục vụ việc đối soát.

### Quản lý thời hạn thanh toán đơn hàng và hủy đơn tự động

Một sàn thương mại điện tử quy định đơn hàng sẽ bị hủy nếu không thanh toán trong vòng 24 giờ kể từ khi đặt. Khách hàng đặt hàng khi đang đi du lịch và di chuyển qua các múi giờ khác nhau. Hệ thống phải đảm bảo rằng thời hạn 24 giờ này là một khoảng thời gian tuyệt đối, không bị kéo dài ra hay rút ngắn lại do việc thay đổi múi giờ trên thiết bị của người dùng hoặc do máy chủ xử lý tác vụ ngầm chạy ở một múi giờ khác.

### Tính toán ngày hết hạn của thẻ thành viên hoặc gói dịch vụ phần mềm

Một người dùng đăng ký gói xem phim trực tuyến có thời hạn 30 ngày. Hệ thống cần xác định chính xác thời điểm gói này hết hiệu lực. Nếu người dùng đăng ký vào lúc sát nửa đêm tại múi giờ của họ, việc tính toán ngày hết hạn nếu không cẩn thận có thể dẫn đến việc người dùng bị mất đi một ngày sử dụng hoặc được dùng thêm một ngày so với quy định. Bài toán này yêu cầu sự nhất quán trong việc định nghĩa ngày bắt đầu và ngày kết thúc trên quy mô toàn cầu.

### Đồng bộ dữ liệu sức khỏe từ thiết bị đeo thông minh

Người dùng sử dụng đồng hồ thông minh để theo dõi giấc ngủ và số bước chân. Khi người dùng bay từ Việt Nam sang Mỹ, dữ liệu ghi nhận lúc họ đang trên máy bay hoặc khi vừa hạ cánh cần được xử lý để không bị chồng chéo hoặc tạo ra những khoảng trống thời gian phi lý trong biểu đồ sức khỏe. Hệ thống cần lưu trữ cả thời gian chuẩn quốc tế và thông tin múi giờ tại thời điểm phát sinh dữ liệu để có thể vẽ lại biểu đồ chính xác theo hành trình của người dùng.

### Kiểm tra điều kiện áp dụng khuyến mãi trong khung giờ vàng

Một chương trình giảm giá chỉ diễn ra từ 12 giờ trưa đến 1 giờ chiều theo giờ địa phương của khách hàng để kích thích mua sắm bữa trưa. Hệ thống backend khi nhận được yêu cầu áp mã giảm giá phải xác định được khách hàng đó đang ở đâu và giờ hiện tại ở vị trí đó có nằm trong khung giờ vàng hay không. Điều này yêu cầu thiết kế API và Database phải đi kèm với thông tin vị trí hoặc múi giờ hiện hành của người dùng thay vì chỉ tin tưởng vào giờ hệ thống của server.
