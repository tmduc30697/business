# Email verification

### Xác thực tài khoản khi đăng ký ứng dụng SaaS

Người dùng đăng ký tài khoản mới trên một nền tảng quản lý công việc. Hệ thống cần lưu trữ thông tin đăng ký ở trạng thái chờ kích hoạt và gửi một email chứa mã xác nhận gồm sáu chữ số. Người dùng phải nhập mã này trong vòng mười lăm phút trước khi mã hết hạn. Bài toán này yêu cầu bạn xử lý trạng thái tài khoản, thời gian sống của mã xác thực và logic kiểm tra tính hợp lệ của mã để chuyển đổi trạng thái người dùng sang đã xác thực.

### Xác minh thay đổi địa chỉ email chính của tài khoản

Một người dùng đã có tài khoản muốn thay đổi email liên lạc hiện tại sang một email mới. Để đảm bảo an ninh, hệ thống không được cập nhật ngay lập tức mà phải gửi một liên kết xác nhận đến địa chỉ email mới đó. Chỉ khi người dùng nhấn vào liên kết, hệ thống mới chính thức cập nhật email mới vào hồ sơ và vô hiệu hóa email cũ. Bạn cần giải quyết việc lưu trữ tạm thời email mới và đảm bảo liên kết xác nhận chỉ có hiệu lực duy nhất một lần.

### Hệ thống khôi phục mật khẩu qua email

Khi người dùng quên mật khẩu, họ yêu cầu một liên kết đặt lại mật khẩu gửi qua email. Liên kết này chứa một token bảo mật dài và có thời gian hết hạn ngắn. Nếu người dùng yêu cầu khôi phục mật khẩu nhiều lần liên tiếp, các token cũ phải bị vô hiệu hóa và chỉ token mới nhất mới có hiệu lực. Bài toán này tập trung vào quản lý token, bảo mật và logic ghi đè các yêu cầu khôi phục đang chờ xử lý.

### Xác thực đa yếu tố khi đăng nhập từ thiết bị lạ

Hệ thống phát hiện người dùng đăng nhập từ một địa chỉ IP hoặc trình duyệt chưa từng được sử dụng trước đây. Để bảo vệ tài khoản, hệ thống tạm dừng quá trình đăng nhập và gửi một mã OTP qua email. Người dùng cần nhập mã này để chứng minh quyền sở hữu tài khoản trước khi được phép truy cập vào bên trong. Bạn cần thiết kế cách lưu trữ nhật ký thiết bị và liên kết phiên đăng nhập đang chờ với mã xác thực email.

### Mời thành viên vào tổ chức trong hệ thống doanh nghiệp

Quản trị viên của một công ty gửi lời mời cho nhân viên mới tham gia vào hệ thống qua email. Email chứa một liên kết mời có đính kèm mã định danh của tổ chức và vai trò được chỉ định. Khi người dùng nhấn vào, hệ thống cần kiểm tra xem email đó đã có tài khoản chưa để dẫn hướng đến trang đăng ký hoặc trang chấp nhận lời mời. Bài toán này giúp bạn thực hành thiết kế quan hệ giữa lời mời, tổ chức và người dùng.

### Quản lý đăng ký nhận tin bản tin định kỳ

Một trang tin tức cho phép người dùng đăng ký nhận bản tin qua email mà không cần tạo tài khoản đầy đủ. Sau khi nhập email, người dùng nhận được thư xác nhận để tránh việc bị người khác dùng email của mình để đăng ký rác. Hệ thống cần quản lý danh sách email chờ xác nhận và danh sách email đã hoạt động, kèm theo khả năng hủy đăng ký bất cứ lúc nào thông qua một liên kết duy nhất ở cuối mỗi email.

### Giới hạn tốc độ gửi email xác thực để chống spam

Trong thực tế, hệ thống cần ngăn chặn việc một kẻ tấn công yêu cầu gửi hàng nghìn email xác thực đến một địa chỉ nhằm quấy rối hoặc làm cạn kiệt tài nguyên. Bạn cần thiết kế cơ chế lưu trữ số lần yêu cầu gửi email trong một khoảng thời gian nhất định cho mỗi địa chỉ email hoặc mỗi địa chỉ IP. Nếu vượt quá giới hạn, hệ thống sẽ từ chối gửi thêm và yêu cầu người dùng đợi thêm một khoảng thời gian cụ thể.

### Xác thực email cho đơn hàng khách vãng lai

Một trang thương mại điện tử cho phép mua hàng mà không cần đăng ký tài khoản. Tuy nhiên, để xem trạng thái đơn hàng hoặc thực hiện hoàn trả, người dùng phải xác thực email được dùng khi mua hàng. Hệ thống sẽ gửi một liên kết truy cập nhanh vào email đó. Bài toán này yêu cầu bạn thiết kế cách liên kết dữ liệu đơn hàng với một phiên truy cập tạm thời dựa trên token email mà không cần thông tin mật khẩu truyền thống.

### Hệ thống nhắc nhở xác thực tài khoản định kỳ

Đối với các hệ thống yêu cầu tính bảo mật cao, sau một khoảng thời gian như sáu tháng, hệ thống yêu cầu người dùng xác nhận lại rằng họ vẫn còn quyền truy cập vào email đã đăng ký. Nếu không xác nhận sau một số lần nhắc nhở, tài khoản sẽ bị hạn chế một số tính năng. Bạn cần thiết kế các tiến trình chạy ngầm để quét cơ sở dữ liệu, gửi email nhắc nhở và cập nhật mức độ tin cậy của tài khoản.

### Tích hợp nhà cung cấp dịch vụ email bên thứ ba

Hệ thống của bạn không tự gửi email mà sử dụng các dịch vụ như SendGrid hoặc Mailgun. Bạn cần thiết kế cơ chế lưu trữ lịch sử gửi email, trạng thái email đã được gửi đi thành công hay bị trả về và xử lý các sự kiện phản hồi từ phía nhà cung cấp thông qua webhook. Bài toán này tập trung vào việc thiết kế API nhận dữ liệu từ bên ngoài và cập nhật trạng thái tương ứng trong cơ sở dữ liệu nội bộ.
