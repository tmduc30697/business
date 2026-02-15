# Webhook system

### Quản lý đăng ký Webhook cho nhiều sự kiện khác nhau

Một nền tảng thương mại điện tử cho phép các đối tác bên thứ ba đăng ký nhận thông báo khi có thay đổi trên hệ thống. Đối tác có thể chọn đăng ký nhận tin cho một hoặc nhiều loại sự kiện cụ thể như khi có đơn hàng mới được tạo, khi trạng thái đơn hàng chuyển sang đã giao, hoặc khi thông tin sản phẩm bị thay đổi. Hệ thống cần lưu trữ thông tin về URL nhận tin của đối tác, các loại sự kiện mà họ quan tâm và một mã bí mật để xác thực gói tin. Bài toán này tập trung vào việc thiết kế cấu trúc dữ liệu để quản lý cấu hình đăng ký linh hoạt cho hàng ngàn đối tác khác nhau.

### Cơ chế gửi lại thông báo khi hệ thống bên nhận gặp sự cố

Khi một sự kiện thanh toán thành công xảy ra, hệ thống gửi Webhook đến máy chủ của đối tác nhưng máy chủ đó đang bảo trì hoặc gặp lỗi mạng và trả về mã lỗi. Hệ thống Webhook không được phép bỏ qua gói tin này mà phải có cơ chế tự động gửi lại sau một khoảng thời gian nhất định theo quy tắc tăng dần thời gian chờ giữa các lần thử. Bạn cần thiết kế một bảng để theo dõi lịch sử gửi tin, trạng thái của từng lần thử và số lần đã gửi lại để quyết định khi nào nên ngừng gửi và đánh dấu thông báo đó là thất bại hoàn toàn.

### Bảo mật và xác thực gói tin Webhook bằng chữ ký số

Để đảm bảo rằng các thông báo gửi đến máy chủ của đối tác thực sự đến từ hệ thống của bạn chứ không phải từ một kẻ tấn công giả mạo, hệ thống cần đính kèm một chữ ký số vào tiêu đề của mỗi yêu cầu HTTP. Chữ ký này được tạo ra bằng cách băm nội dung gói tin kết hợp với một mã bí mật mà chỉ hai bên biết. Bài toán này yêu cầu thiết kế quy trình xử lý dữ liệu trước khi gửi và cung cấp tài liệu hoặc API để đối tác có thể kiểm tra tính toàn vẹn của dữ liệu họ nhận được.

### Kiểm soát lưu lượng gửi Webhook để tránh làm sập máy chủ đối tác

Một đối tác lớn có thể phát sinh hàng vạn sự kiện mỗi phút, dẫn đến việc hệ thống của bạn gửi liên tiếp hàng vạn yêu cầu HTTP đến máy chủ của họ trong thời gian ngắn. Nếu không kiểm soát, hành động này có thể vô tình trở thành một cuộc tấn công từ chối dịch vụ. Hệ thống Webhook cần có cơ chế giới hạn tốc độ gửi tin dựa trên cấu hình cho từng đối tác cụ thể. Việc này đòi hỏi tư duy về thiết kế hàng đợi và các dịch vụ điều phối luồng gửi tin để đảm bảo tính ổn định cho cả hai bên.

### Hệ thống bảng điều khiển theo dõi trạng thái Webhook cho người dùng

Khách hàng sử dụng Webhook cần một giao diện để tự theo dõi xem các thông báo từ hệ thống của bạn gửi đi có thành công hay không. Họ cần xem được danh sách các sự kiện đã xảy ra, nội dung gói tin đã gửi, phản hồi từ máy chủ của họ và thời gian phản hồi là bao lâu. Bài toán này yêu cầu thiết kế cơ sở dữ liệu cho phép truy vấn nhanh chóng lịch sử gửi tin khổng lồ và cung cấp các API để người dùng có thể yêu cầu gửi lại một gói tin cụ thể bằng tay thông qua giao diện quản lý.

### Xử lý trùng lặp gói tin Webhook tại bên nhận

Trong môi trường mạng không ổn định, đôi khi hệ thống của bạn gửi Webhook đi, đối tác đã nhận được và xử lý thành công nhưng phản hồi xác nhận lại bị thất lạc. Khi đó, hệ thống của bạn sẽ gửi lại gói tin đó một lần nữa. Để bên nhận không xử lý một đơn hàng hai lần, mỗi gói tin Webhook cần có một mã định danh duy nhất không thay đổi giữa các lần gửi lại. Bài toán này giúp bạn rèn luyện tư duy thiết kế cấu trúc dữ liệu gói tin và logic xử lý đảm bảo tính nhất quán dữ liệu cho cả bên gửi lẫn bên nhận.

### Lọc và tùy chỉnh nội dung dữ liệu Webhook theo yêu cầu đối tác

Mỗi đối tác có nhu cầu nhận dữ liệu khác nhau; có bên chỉ cần ID đơn hàng, có bên lại cần toàn bộ chi tiết sản phẩm và thông tin khách hàng. Thay vì gửi một gói tin khổng lồ chứa tất cả thông tin cho mọi người, hệ thống cho phép đối tác cấu hình các trường dữ liệu mà họ muốn nhận. Điều này đòi hỏi thiết kế database cho phép lưu trữ cấu hình mẫu dữ liệu và một bộ máy xử lý logic để trích xuất đúng các thành phần dữ liệu cần thiết từ đối tượng gốc trước khi chuyển đổi thành định dạng JSON để gửi đi.

### Tạm ngừng và vô hiệu hóa các địa chỉ Webhook không hoạt động

Nếu một URL nhận tin của đối tác liên tục trả về lỗi trong một thời gian dài hoặc địa chỉ đó không còn tồn tại, việc tiếp tục gửi tin sẽ gây lãng phí tài nguyên hệ thống. Hệ thống cần một cơ chế thông minh để tự động theo dõi tỷ lệ lỗi của từng đăng ký. Nếu tỷ lệ lỗi vượt quá ngưỡng cho phép, hệ thống sẽ tự động chuyển trạng thái của Webhook đó sang tạm dừng và gửi cảnh báo qua email cho đối tác để họ kiểm tra lại cấu hình. Bài toán này tập trung vào việc quản lý vòng đời và trạng thái của các bản ghi đăng ký Webhook.
