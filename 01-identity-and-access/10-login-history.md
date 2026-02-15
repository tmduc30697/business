# Login history

### Phát hiện đăng nhập từ vị trí địa lý lạ

Bài toán này tập trung vào việc bảo vệ tài khoản khi có sự thay đổi đột ngột về khoảng cách di chuyển. Hệ thống cần lưu trữ tọa độ hoặc mã quốc gia của mỗi lần đăng nhập thành công. Khi một người dùng vừa đăng nhập tại Hà Nội nhưng chỉ 10 phút sau lại có yêu cầu đăng nhập từ New York, hệ thống phải nhận diện được sự phi lý về mặt vật lý này để tạm khóa tài khoản hoặc yêu cầu xác thực hai lớp. Việc này đòi hỏi cơ sở dữ liệu phải truy vấn nhanh lịch sử gần nhất và so sánh với dữ liệu thời gian thực.

### Quản lý phiên hoạt động và đăng xuất từ xa

Người dùng thường có thói quen đăng nhập tài khoản trên nhiều thiết bị như điện thoại cá nhân, máy tính công ty và máy tính bảng. Bài toán đặt ra là hiển thị danh sách tất cả các thiết bị đang có phiên làm việc (session) còn hiệu lực. Người dùng có thể xem tên thiết bị, trình duyệt đang dùng và thời gian hoạt động cuối cùng. Quan trọng hơn, họ phải có quyền nhấn nút để hủy bỏ một phiên làm việc cụ thể từ xa, buộc thiết bị đó phải đăng nhập lại vào lần truy cập tới.

### Giới hạn số lượng thiết bị đăng nhập đồng thời

Đối với các dịch vụ trả phí như xem phim trực tuyến hoặc học online, việc chia sẻ tài khoản quá mức sẽ gây thất thu. Bài toán yêu cầu hệ thống kiểm tra lịch sử đăng nhập để xác định có bao nhiêu thiết bị đang hoạt động cùng lúc. Nếu vượt quá số lượng cho phép, ví dụ là 3 thiết bị, hệ thống sẽ ngăn chặn lần đăng nhập thứ 4 hoặc tự động đẩy thiết bị cũ nhất ra khỏi hệ thống. Điều này đòi hỏi thiết kế bảng dữ liệu có sự kết nối chặt chẽ giữa trạng thái phiên và lịch sử truy cập.

### Nhận diện thiết bị tin cậy để bỏ qua xác thực hai lớp

Để tối ưu trải nghiệm người dùng, hệ thống cần phân biệt giữa thiết bị lạ và thiết bị quen thuộc. Khi người dùng đăng nhập thành công, hệ thống sẽ lưu lại các thông tin định danh phần cứng (fingerprint) hoặc mã định danh trình duyệt. Trong những lần tiếp theo, nếu thông tin thiết bị trùng khớp với lịch sử thiết bị tin cậy, người dùng sẽ không cần nhập mã OTP. Nếu có sự thay đổi về trình duyệt hoặc thiết bị mới, hệ thống sẽ kích hoạt quy trình bảo mật bổ sung.

### Thống kê và phân tích hành vi người dùng theo thời gian

Đây là bài toán dành cho bộ phận quản trị và marketing. Hệ thống cần tổng hợp dữ liệu từ lịch sử đăng nhập để vẽ biểu đồ về lượng người dùng hoạt động theo từng khung giờ trong ngày hoặc từng ngày trong tuần. Dữ liệu này giúp doanh nghiệp biết được thời điểm nào hệ thống chịu tải cao nhất hoặc xác định những người dùng đã lâu không quay lại ứng dụng để gửi email thông báo khuyến mãi nhằm giữ chân họ.

### Theo dõi và ngăn chặn tấn công dò mật khẩu theo diện rộng

Bài toán này yêu cầu ghi lại cả những lần đăng nhập thất bại. Khi một địa chỉ IP thực hiện hàng trăm lần đăng nhập sai với nhiều tài khoản khác nhau trong một khoảng thời gian ngắn, hệ thống phải nhận diện đây là một cuộc tấn công dò mật khẩu (Brute Force). Dữ liệu lịch sử lúc này đóng vai trò là bằng chứng để hệ thống tự động đưa địa chỉ IP đó vào danh sách đen hoặc yêu cầu giải mã captcha đối với mọi yêu cầu từ nguồn đó.

### Gửi thông báo bảo mật khi có thay đổi trình duyệt hoặc IP

Mỗi khi có một lần đăng nhập thành công từ một địa chỉ IP hoặc một loại trình duyệt mà người dùng chưa từng sử dụng trước đây, hệ thống sẽ tự động gửi một email hoặc thông báo đẩy về điện thoại. Nội dung thông báo sẽ liệt kê chi tiết thời gian, loại thiết bị và vị trí ước tính. Điều này giúp người dùng chủ động kiểm soát bảo mật và kịp thời đổi mật khẩu nếu đó không phải là hành động của họ.

### Truy vết lịch sử thay đổi quyền hạn và trạng thái tài khoản

Trong các hệ thống quản trị nội bộ, việc đăng nhập thường đi kèm với các hành động thay đổi dữ liệu nhạy cảm. Bài toán yêu cầu kết nối lịch sử đăng nhập với các hành động cụ thể của người dùng. Nếu một nhân viên thực hiện xóa dữ liệu quan trọng, người quản trị có thể truy xuất ngược lại phiên đăng nhập đó được thực hiện từ IP nào, thiết bị nào và vào thời điểm nào để xác định trách nhiệm hoặc phát hiện tài khoản của nhân viên đó đang bị chiếm đoạt.

### Tự động dọn dẹp dữ liệu lịch sử cũ để tối ưu lưu trữ

Với các hệ thống có hàng triệu người dùng, bảng lưu trữ lịch sử đăng nhập sẽ phình to rất nhanh theo thời gian, gây chậm trễ cho việc truy vấn. Bài toán đặt ra là thiết kế một quy trình tự động sao lưu các bản ghi cũ hơn 6 tháng vào một kho lưu trữ lạnh (Cold Storage) và xóa dữ liệu gốc để giữ cho bảng làm việc luôn nhẹ nhàng. Tuy nhiên, hệ thống vẫn phải đảm bảo khi cần thiết, người quản trị vẫn có thể tra cứu lại các dữ liệu cũ này cho mục đích điều tra.

### Phân tích điểm uy tín của địa chỉ IP

Hệ thống sẽ xây dựng một bảng điểm uy tín dựa trên lịch sử đăng nhập. Nếu một địa chỉ IP có lịch sử đăng nhập thành công cho nhiều tài khoản hợp lệ và không có hành vi vi phạm, nó sẽ được coi là IP sạch. Ngược lại, nếu một IP thường xuyên liên quan đến các lần đăng nhập thất bại hoặc đến từ các dải IP của các dịch vụ proxy/VPN không rõ nguồn gốc, hệ thống sẽ đánh dấu cảnh báo cao. Khi đó, mọi yêu cầu từ IP này sẽ bị kiểm soát chặt chẽ hơn bình thường.
