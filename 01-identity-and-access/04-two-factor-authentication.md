# Two-factor authentication

### Hệ thống quản lý tin nhắn OTP tập trung cho doanh nghiệp

Bài toán này yêu cầu thiết kế một dịch vụ trung gian kết nối giữa các ứng dụng nội bộ và các nhà cung cấp dịch vụ viễn thông. Hệ thống cần lưu trữ thông tin về các yêu cầu gửi mã, trạng thái gửi tin, thời gian mã hết hạn và giới hạn số lượng tin nhắn tối đa mà một số điện thoại có thể nhận trong ngày để tránh lãng phí chi phí và ngăn chặn tấn công spam.

### Nền tảng ngân hàng số với xác thực giao dịch đa tầng

Trong kịch bản này, người dùng không chỉ dùng 2FA để đăng nhập mà còn phải xác thực cho từng giao dịch chuyển tiền cụ thể. Bạn cần thiết kế cách liên kết mã OTP với một mã giao dịch duy nhất để đảm bảo mã đó không thể bị sử dụng lại cho một giao dịch khác, đồng thời quản lý lịch sử xác thực để phục vụ mục đích tra soát sau này.

### Hệ thống đăng nhập bằng mã QR và ứng dụng Authenticator

Thay vì sử dụng SMS, hệ thống này tập trung vào việc tạo và quản lý các khóa bí mật dùng chung giữa máy chủ và ứng dụng di động. Bài toán đặt ra là làm thế nào để lưu trữ an toàn các chuỗi ký tự khởi tạo, cách xử lý khi người dùng làm mất điện thoại và quy trình tạo ra các mã khôi phục dự phòng để người dùng tự cứu lấy tài khoản của mình.

### Quản lý phiên làm việc và tin cậy thiết bị ngoại vi

Sau khi người dùng vượt qua bước 2FA, hệ thống có thể cung cấp tùy chọn ghi nhớ trình duyệt này trong ba mươi ngày. Bạn cần thiết kế cấu trúc để lưu trữ thông tin định danh thiết bị, địa chỉ IP và thời điểm xác thực cuối cùng, giúp người dùng không phải nhập OTP liên tục trên các thiết bị quen thuộc nhưng vẫn đảm bảo an toàn nếu truy cập từ một thiết bị lạ.

### Hệ thống phân cấp bảo mật cho quản trị viên hệ thống

Đối với các tài khoản có quyền hạn cao, việc chỉ dùng mật khẩu và OTP là chưa đủ. Bài toán yêu cầu thiết lập các quy tắc bắt buộc sử dụng khóa bảo mật vật lý hoặc yêu cầu phê duyệt từ một quản trị viên khác thông qua thông báo đẩy trên ứng dụng di động. Việc thiết kế database ở đây cần chú trọng vào việc phân quyền và lưu trữ các chứng chỉ bảo mật phần cứng.

### Dịch vụ xác thực đa kênh tùy chọn theo hành vi người dùng

Hệ thống cho phép người dùng tự lựa chọn phương thức nhận mã xác thực ưu tiên như qua ứng dụng Telegram, Email hoặc cuộc gọi thoại. Bạn cần thiết kế logic để hệ thống tự động chuyển đổi sang phương thức dự phòng nếu phương thức chính gặp sự cố, đồng thời quản lý cấu hình ưu tiên này trong hồ sơ cá nhân của mỗi người dùng.

### Hệ thống giới hạn tốc độ và ngăn chặn tấn công dò mã xác thực

Đây là bài toán thiên về thiết kế hệ thống và bảo mật nhằm chống lại các cuộc tấn công thử sai liên tục. Bạn cần thiết kế cơ chế lưu trữ số lần nhập sai cho mỗi phiên xác thực, các trạng thái tạm khóa tài khoản khi vượt quá ngưỡng cho phép và cách thức tự động mở khóa sau một khoảng thời gian nhất định hoặc thông qua sự can thiệp của bộ phận hỗ trợ.

### Quy trình khôi phục tài khoản khi mất yếu tố xác thực thứ hai

Khi người dùng mất cả điện thoại lẫn mã dự phòng, hệ thống cần một quy trình xác minh thay thế nghiêm ngặt. Bài toán này tập trung vào việc lưu trữ các câu hỏi bảo mật, thông tin giấy tờ tùy thân đã được mã hóa hoặc danh sách các liên hệ tin cậy có thể giúp xác nhận danh tính, từ đó cho phép thiết lập lại phương thức 2FA mới.

### Hệ thống thông báo bảo mật và giám sát đăng nhập thời gian thực

Mỗi khi có một yêu cầu mã OTP hoặc một lần đăng nhập thành công từ địa điểm lạ, hệ thống phải ghi nhận và gửi cảnh báo ngay lập tức. Bạn cần thiết kế bảng lưu trữ nhật ký truy cập chi tiết bao gồm vị trí địa lý, loại thiết bị và kết quả xác thực để cung cấp cho người dùng một bảng điều khiển giúp họ theo dõi và đăng xuất từ xa khỏi các phiên làm việc nghi ngờ.

### Tích hợp 2FA vào hệ thống đăng nhập đơn lẻ cho doanh nghiệp

Trong môi trường công ty, một tài khoản được dùng để đăng nhập vào nhiều ứng dụng khác nhau. Bài toán yêu cầu thiết kế một trung tâm xác thực nơi mà sau khi xác thực 2FA một lần, người dùng sẽ nhận được một thẻ xác thực dùng chung cho các dịch vụ nội bộ khác mà không cần phải nhập lại mã OTP cho đến khi thẻ đó hết hạn.
