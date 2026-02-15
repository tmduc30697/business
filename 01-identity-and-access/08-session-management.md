# Session management

### Hệ thống đăng nhập đa thiết bị và quản lý phiên hoạt động

Hệ thống cho phép người dùng đăng nhập trên nhiều thiết bị như điện thoại, máy tính bảng và trình duyệt web cùng lúc. Bài toán yêu cầu bạn phải lưu trữ thông tin chi tiết về từng phiên làm việc bao gồm địa chỉ IP, loại thiết bị, trình duyệt sử dụng và thời gian tương tác cuối cùng. Người dùng cần có khả năng xem danh sách các thiết bị đang đăng nhập và có quyền đăng xuất từ xa một thiết bị cụ thể hoặc đăng xuất khỏi tất cả các thiết bị ngoại trừ thiết bị hiện tại.

### Cơ chế Refresh Token và xoay vòng khóa bảo mật

Thay vì bắt người dùng đăng nhập lại liên tục, hệ thống sử dụng cặp Access Token ngắn hạn và Refresh Token dài hạn. Bài toán đặt ra là khi Access Token hết hạn, ứng dụng phải tự động dùng Refresh Token để lấy cặp token mới mà không làm gián đoạn trải nghiệm người dùng. Bạn cần giải quyết vấn đề kiểm soát vòng đời của Refresh Token, ngăn chặn việc sử dụng lại các token cũ đã bị thu hồi và cơ chế phát hiện nếu một Refresh Token bị đánh cắp thông qua kỹ thuật xoay vòng token.

### Kiểm soát phiên làm việc dựa trên giới hạn địa lý và rủi ro

Hệ thống cần theo dõi vị trí đăng nhập của người dùng dựa trên IP hoặc GPS. Nếu một phiên làm việc mới được khởi tạo ở một vị trí địa lý cách quá xa vị trí của phiên làm việc trước đó trong một khoảng thời gian ngắn bất thường, hệ thống sẽ đánh dấu phiên đó là nghi vấn. Bài toán yêu cầu thiết kế cách lưu trữ lịch sử đăng nhập và trạng thái xác thực để có thể yêu cầu người dùng xác minh thêm yếu tố thứ hai hoặc tạm khóa phiên làm việc nếu phát hiện dấu hiệu xâm nhập.

### Thu hồi Token tức thì trong kiến trúc Microservices

Trong hệ thống phân tán, các dịch vụ thường xác thực qua JWT một cách độc lập mà không truy vấn cơ sở dữ liệu trung tâm để giảm độ trễ. Thách thức xảy ra khi một người dùng bị đổi mật khẩu, bị khóa tài khoản hoặc đăng xuất, nhưng các Access Token cũ vẫn còn hiệu lực. Bạn cần thiết kế một cơ chế danh sách đen lưu trữ các token bị hủy bỏ trong bộ nhớ đệm tốc độ cao như Redis và cách các microservices đồng bộ hóa danh sách này để từ chối các yêu cầu không còn hợp lệ.

### Quản lý phiên làm việc cho tài khoản doanh nghiệp có nhiều cấp bậc

Trong môi trường doanh nghiệp, một tài khoản có thể thuộc về nhiều tổ chức hoặc dự án khác nhau với các vai trò khác nhau. Khi người dùng chuyển đổi giữa các ngữ cảnh làm việc, phiên đăng nhập cần cập nhật lại quyền hạn mà không nhất thiết phải đăng nhập lại từ đầu. Bài toán yêu cầu thiết kế cấu trúc session chứa thông tin về ngữ cảnh hiện tại và cơ chế để hệ thống kiểm tra quyền hạn tương ứng với từng hành động cụ thể trong phiên đó.

### Giới hạn số lượng phiên đăng nhập đồng thời trên mỗi tài khoản

Để ngăn chặn việc chia sẻ tài khoản trái phép hoặc bảo vệ tài nguyên hệ thống, dịch vụ chỉ cho phép một số lượng thiết bị nhất định hoạt động cùng lúc cho mỗi người dùng. Khi người dùng đăng nhập vượt quá giới hạn này, hệ thống phải quyết định sẽ ngăn chặn lần đăng nhập mới hay tự động ngắt phiên cũ nhất. Bạn cần thiết kế logic kiểm đếm số phiên đang hoạt động theo thời gian thực và cập nhật trạng thái của chúng trong cơ sở dữ liệu.

### Tự động gia hạn phiên dựa trên hoạt động của người dùng

Để cân bằng giữa bảo mật và sự tiện dụng, hệ thống áp dụng cơ chế thời gian chờ không hoạt động. Nếu người dùng liên tục tương tác với ứng dụng, phiên làm việc sẽ tự động được kéo dài thêm một khoảng thời gian nhất định. Ngược lại, nếu không có yêu cầu nào gửi lên máy chủ sau một khoảng thời gian quy định, phiên sẽ tự động bị hủy. Bài toán yêu cầu bạn thiết kế cách cập nhật thời gian hết hạn một cách tối ưu để tránh gây tải cho cơ sở dữ liệu trong mỗi lần gửi request.

### Quản lý phiên làm việc cho ứng dụng Single Page và di động

Ứng dụng web chạy trên trình duyệt có các rủi ro bảo mật khác với ứng dụng di động chạy trên iOS hoặc Android. Bài toán yêu cầu thiết kế các phương thức lưu trữ phiên khác nhau như sử dụng Cookie với thuộc tính bảo mật cao cho web và Secure Storage cho di động. Bạn cần xây dựng API xử lý việc tạo session sao cho phù hợp với cả hai nền tảng, đảm bảo rằng thông tin phiên không bị lộ qua các cuộc tấn công phổ biến.
