# Account lock

### Chống tấn công dò mật khẩu tự động cho hệ thống ngân hàng số

Hệ thống cần theo dõi các lần đăng nhập thất bại liên tiếp trong một khoảng thời gian ngắn từ một địa chỉ IP hoặc một tài khoản cụ thể. Nếu người dùng nhập sai mật khẩu quá năm lần trong vòng mười phút, tài khoản sẽ bị khóa tạm thời trong ba mươi phút. Sau thời gian này, tài khoản tự động mở lại nhưng nếu tiếp tục sai lần thứ sáu, hệ thống sẽ yêu cầu người dùng phải thực hiện xác thực qua mã OTP được gửi về số điện thoại đã đăng ký để gỡ khóa. Việc này đòi hỏi lưu trữ lịch sử các lần thử, thời điểm bắt đầu khóa và trạng thái hiện tại của tài khoản.

### Quản lý truy cập nội bộ và khóa tài khoản thủ công cho nhân viên doanh nghiệp

Trong môi trường doanh nghiệp, quản trị viên hệ thống cần có khả năng khóa tài khoản của nhân viên ngay lập tức khi họ nghỉ việc hoặc khi phát hiện dấu hiệu rò rỉ dữ liệu từ máy tính của nhân viên đó. Hệ thống quản lý cần một giao diện cho phép admin tra cứu danh sách nhân viên, xem trạng thái hoạt động và nhấn nút khóa thủ công kèm theo lý do cụ thể. Khi bị khóa thủ công, nhân viên không thể tự mở khóa thông qua các phương thức thông thường mà phải liên hệ bộ phận hỗ trợ kỹ thuật để xác minh danh tính trực tiếp.

### Bảo vệ tài khoản thương mại điện tử dựa trên hành vi vị trí địa lý bất thường

Hệ thống giám sát vị trí đăng nhập của người dùng dựa trên tọa độ GPS hoặc dải địa chỉ IP thường dùng. Nếu một tài khoản đang được sử dụng ở Việt Nam nhưng đột ngột có yêu cầu đăng nhập thành công từ một quốc gia khác sau đó chỉ vài phút, hệ thống sẽ đánh dấu đây là hành vi bất thường và tự động khóa các chức năng thanh toán. Người dùng vẫn có thể xem sản phẩm nhưng không thể đặt hàng cho đến khi họ xác nhận danh tính qua email chính chủ. Bài toán này tập trung vào việc lưu trữ nhật ký đăng nhập và các quy tắc kiểm tra điều kiện logic giữa các phiên làm việc.

### Cơ chế khóa tài khoản theo cấp độ tăng dần cho ứng dụng mạng xã hội

Để tránh làm phiền người dùng quên mật khẩu nhưng vẫn đảm bảo an ninh, hệ thống áp dụng hình thức khóa bậc thang. Lần đầu vi phạm sẽ khóa trong năm phút, lần tiếp theo là một tiếng, và sau ba lần tái diễn sẽ khóa vĩnh viễn cho đến khi có sự can thiệp của con người. Điều này yêu cầu cơ sở dữ liệu phải ghi lại số lần bị khóa trong quá khứ và cấp độ khóa hiện tại để tính toán thời gian mở khóa tương ứng.

### Hệ thống quản lý thẻ thành viên phòng tập gym qua mã QR

Thành viên sử dụng mã QR trên ứng dụng di động để quét tại cửa ra vào. Nếu một mã QR được quét liên tục tại các chi nhánh khác nhau trong cùng một thời điểm hoặc quét sai quá nhiều lần tại cổng thanh toán, hệ thống sẽ tự động khóa thẻ thành viên đó để ngăn chặn việc chia sẻ tài khoản cho người khác dùng chung. Nhân viên lễ tân cần một API để kiểm tra trạng thái thẻ và có quyền mở khóa sau khi đã đối chiếu ảnh đại diện của khách hàng trên hệ thống với người thực tế.

### Khóa quyền truy cập API cho đối tác phát triển phần mềm

Một nền tảng cung cấp dữ liệu qua API cho các đối tác thứ ba cần kiểm soát lưu lượng và bảo mật. Nếu một API Key được sử dụng để truy cập các tài nguyên không được phép hoặc gửi số lượng yêu cầu vượt quá hạn mức quy định trong một giây, hệ thống sẽ tự động vô hiệu hóa key đó. Thông báo sẽ được gửi về hệ thống giám sát của bên cung cấp để kiểm tra xem đó là lỗi lập trình hay một cuộc tấn công mạng. Database cần thiết kế để quản lý các hạn mức và trạng thái của từng khóa truy cập.

### Kiểm soát truy cập máy chủ từ xa qua giao thức SSH

Trên các máy chủ quản lý dữ liệu nhạy cảm, việc đăng nhập qua dòng lệnh cần được bảo vệ nghiêm ngặt. Nếu một tài khoản quản trị bị nhập sai mã khóa bí mật hoặc mật khẩu quá số lần quy định từ một thiết bị lạ, hệ thống sẽ không chỉ khóa tài khoản đó mà còn đưa địa chỉ IP của kẻ tấn công vào danh sách đen. Bài toán này yêu cầu sự phối hợp giữa bảng quản lý người dùng và bảng chặn các định danh thiết bị hoặc địa chỉ mạng từ bên ngoài.

### Quy trình phê duyệt mở khóa tài khoản cho hệ thống tài chính

Khi một tài khoản bị khóa do nghi ngờ gian lận, quy trình mở khóa không được thực hiện bởi một người duy nhất để tránh tiêu cực. Một nhân viên cấp dưới sẽ tạo yêu cầu mở khóa sau khi kiểm tra hồ sơ khách hàng, sau đó một quản lý cấp cao hơn phải vào hệ thống để phê duyệt yêu cầu đó thì tài khoản mới trở lại trạng thái hoạt động. Điều này giúp bạn luyện tập thiết kế các bảng lưu trữ quy trình công việc và lịch sử phê duyệt trong hệ thống.
