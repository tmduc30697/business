# Reset password

### Hệ thống đặt đồ ăn với mã OTP qua tin nhắn SMS

Bài toán này tập trung vào trải nghiệm người dùng trên di động, nơi người dùng thường quên mật khẩu và muốn khôi phục nhanh qua số điện thoại. Bạn cần xử lý việc lưu trữ mã OTP có thời hạn cực ngắn, giới hạn số lần gửi lại mã để tránh tốn chi phí nhà mạng và cơ chế vô hiệu hóa mã cũ khi mã mới được yêu cầu. Hệ thống cũng cần ghi nhận thiết bị đang yêu cầu để đảm bảo tính chính danh.

### Nền tảng học trực tuyến với link xác thực gửi qua Email

Đây là mô hình kinh điển nhất nơi người dùng nhận được một đường dẫn chứa mã token dài qua email. Bài toán yêu cầu bạn thiết kế cấu trúc token sao cho không thể đoán trước, trạng thái của token đã sử dụng hay chưa và xử lý trường hợp token hết hạn sau 24 giờ. Bạn cũng cần xem xét việc tự động đăng xuất người dùng khỏi tất cả các thiết bị khác sau khi mật khẩu được đổi thành công để tăng cường bảo mật.

### Hệ thống quản lý nhân sự nội bộ với câu hỏi bảo mật bổ sung

Trong môi trường doanh nghiệp có tính bảo mật cao, việc chỉ có truy cập email là chưa đủ. Sau khi click vào link reset, hệ thống yêu cầu người dùng trả lời chính xác các câu hỏi bảo mật đã thiết lập từ trước hoặc nhập mã nhân viên. Bài toán này giúp bạn luyện tập cách thiết kế bảng lưu trữ các cặp câu hỏi-trả lời và logic kiểm tra đa lớp trước khi cho phép ghi đè mật khẩu mới.

### Ứng dụng ví điện tử với yêu cầu xác thực sinh trắc học

Khi người dùng yêu cầu đặt lại mật khẩu hoặc mã PIN cho ví điện tử, hệ thống không chỉ gửi mã xác minh mà còn yêu cầu xác thực bằng khuôn mặt hoặc vân tay trên thiết bị đã tin tưởng. Bài toán này đòi hỏi thiết kế hệ thống có khả năng liên kết giữa khóa công khai của thiết bị với phiên làm việc của yêu cầu reset mật khẩu, đảm bảo rằng việc đổi mật khẩu chỉ diễn ra trên đúng thiết bị chính chủ.

### Cổng dịch vụ công với quy trình phê duyệt từ quản trị viên

Đối với các tài khoản cấp cao hoặc tài khoản tổ chức, việc reset mật khẩu không diễn ra tự động. Sau khi người dùng gửi yêu cầu và xác minh danh tính cơ bản, yêu cầu này sẽ rơi vào một hàng đợi phê duyệt của quản trị viên hệ thống. Bạn cần thiết kế một quy trình workflow với các trạng thái như chờ duyệt, đã duyệt, bị từ chối và ghi lại nhật ký chi tiết ai là người đã phê duyệt thay đổi đó.

### Mạng xã hội với tính năng bảo vệ chống chiếm đoạt tài khoản

Trong trường hợp một tài khoản bị hacker tấn công và đổi email nhận tin, bài toán đặt ra là cho phép người dùng khôi phục mật khẩu thông qua các liên hệ tin cậy hoặc sử dụng lại mật khẩu cũ trong vòng 48 giờ để hủy bỏ lệnh thay đổi. Điều này đòi hỏi cơ sở dữ liệu phải lưu trữ lịch sử các mật khẩu gần nhất và các mối quan hệ bạn bè được chỉ định làm người bảo lãnh.

### Hệ thống quản lý đại lý bán sỉ với mã khôi phục dự phòng

Nhiều hệ thống cung cấp cho người dùng một danh sách các mã khôi phục cố định khi họ đăng ký tài khoản. Khi mất cả điện thoại và email, người dùng có thể nhập một trong các mã này để đặt lại mật khẩu. Bài toán này tập trung vào việc quản lý danh sách mã dùng một lần, cách mã hóa chúng trong cơ sở dữ liệu để ngay cả khi lộ bảng dữ liệu, hacker cũng không thể sử dụng các mã này.

### Nền tảng thương mại điện tử đa quốc gia với đa phương thức xác thực

Người dùng có thể chọn nhận mã reset qua Telegram, Zalo, WhatsApp hoặc Email tùy theo vùng lãnh thổ. Hệ thống cần một kiến trúc linh hoạt để quản lý các nhà cung cấp dịch vụ gửi tin khác nhau và lưu trữ trạng thái gửi tin để kiểm soát lưu lượng. Bạn sẽ cần thiết kế bảng cấu hình phương thức thông báo và logic để hệ thống biết phải ưu tiên gửi qua kênh nào trước.
