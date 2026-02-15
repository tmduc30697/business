# Ban account

### Khóa tài khoản tạm thời do nhập sai mật khẩu quá nhiều lần

Để bảo vệ người dùng khỏi các cuộc tấn công dò mật khẩu, hệ thống cần theo dõi số lần đăng nhập thất bại liên tiếp trong một khoảng thời gian ngắn. Khi số lần vi phạm vượt quá ngưỡng cho phép, ví dụ như 5 lần trong 10 phút, tài khoản sẽ tự động chuyển sang trạng thái khóa tạm thời. Sau một khoảng thời gian nhất định như 30 phút, hệ thống phải tự động mở khóa hoặc yêu cầu người dùng thực hiện một bước xác minh bổ sung qua email để có thể tiếp tục sử dụng.

### Khóa tài khoản vĩnh viễn do vi phạm điều khoản cộng đồng nghiêm trọng

Khi một người dùng bị quản trị viên xác nhận là có hành vi phát tán nội dung độc hại hoặc lừa đảo, tài khoản đó cần bị vô hiệu hóa ngay lập tức và vĩnh viễn. Bài toán này yêu cầu hệ thống không chỉ đổi trạng thái tài khoản mà còn phải lưu trữ bằng chứng vi phạm, danh tính người thực hiện lệnh khóa, và lý do chi tiết để phục vụ việc đối soát hoặc giải quyết khiếu nại về sau. Mọi phiên đăng nhập hiện tại của người dùng này trên các thiết bị khác cũng phải bị thu hồi quyền truy cập ngay lập tức.

### Cơ chế cảnh cáo và khóa tài khoản theo lộ trình tăng dần

Thay vì khóa ngay lập tức, hệ thống áp dụng hình thức kỷ luật theo từng cấp độ đối với các hành vi vi phạm nhẹ như spam bình luận. Lần vi phạm thứ nhất sẽ bị khóa tính năng bình luận trong 24 giờ, lần thứ hai là 7 ngày, và lần thứ ba sẽ bị khóa toàn bộ tài khoản trong 30 ngày. Hệ thống cần một cấu trúc dữ liệu để theo dõi lịch sử vi phạm, tính toán cấp độ hiện tại của người dùng và tự động thực thi hình thức phạt tương ứng với từng giai đoạn.

### Khóa tài khoản dựa trên hành vi gian lận thanh toán

Trong các hệ thống thương mại điện tử, khi bộ phận rủi ro phát hiện một thẻ tín dụng bị đánh cắp đang được dùng để thanh toán trên nhiều tài khoản khác nhau, hệ thống cần thực hiện lệnh khóa hàng loạt các tài khoản liên quan. Bài toán này yêu cầu thiết kế database có khả năng truy vết mối liên hệ giữa tài khoản, phương thức thanh toán và địa chỉ IP để có thể đóng băng các giao dịch đáng ngờ và ngăn chặn thiệt hại về tài chính một cách nhanh nhất.

### Tự động vô hiệu hóa tài khoản không hoạt động trong thời gian dài

Để tối ưu tài nguyên và đảm bảo an toàn dữ liệu theo các quy định về quyền riêng tư, hệ thống cần định kỳ rà soát các tài khoản không có bất kỳ hoạt động đăng nhập nào trong vòng hai năm. Trước khi chính thức vô hiệu hóa, hệ thống sẽ gửi một loạt thông báo nhắc nhở qua email hoặc tin nhắn. Nếu người dùng không phản hồi hoặc không đăng nhập lại trong thời hạn thông báo, tài khoản sẽ được chuyển sang trạng thái lưu trữ hoặc xóa bỏ dữ liệu cá nhân theo quy trình bảo mật.

### Quy trình khiếu nại và mở khóa tài khoản bởi quản trị viên

Sau khi một tài khoản bị khóa, người dùng có quyền gửi đơn khiếu nại để giải trình về hành vi của mình. Bài toán này tập trung vào luồng công việc của nhân viên hỗ trợ khách hàng. Hệ thống cần ghi lại toàn bộ nhật ký thay đổi trạng thái tài khoản từ lúc bị khóa đến khi được mở lại, bao gồm các ghi chú nội bộ giữa các bộ phận xử lý. Việc thiết kế API phải đảm bảo chỉ những người có thẩm quyền cụ thể mới được phép thay đổi trạng thái tài khoản từ khóa sang hoạt động.

### Khóa tài khoản hàng loạt theo chiến dịch chống tài khoản ảo

Trong các đợt đăng ký nhận quà tặng, hệ thống có thể bị tấn công bởi hàng nghìn tài khoản ảo được tạo tự động bởi robot. Sau khi quét và nhận diện dựa trên các dấu hiệu bất thường, quản trị viên cần thực hiện một lệnh khóa hàng loạt cho danh sách hàng nghìn ID tài khoản cùng một lúc. Hệ thống cần xử lý tác vụ này dưới nền để tránh gây nghẽn mạch hoặc làm chậm các hoạt động khác của người dùng bình thường, đồng thời phải đảm bảo tính toàn vẹn dữ liệu khi thực hiện cập nhật quy mô lớn.

### Hạn chế quyền truy cập thay vì khóa hoàn toàn tài khoản

Một số trường hợp vi phạm về nợ phí dịch vụ hoặc vi phạm bản quyền nhẹ có thể dẫn đến việc tài khoản bị chuyển sang chế độ chỉ đọc. Người dùng vẫn có thể đăng nhập để xem dữ liệu cũ của họ nhưng không thể tạo mới nội dung, không thể thanh toán hoặc không thể tương tác với người dùng khác. Bài toán này yêu cầu thiết kế hệ thống phân quyền linh hoạt, nơi trạng thái của tài khoản trực tiếp ảnh hưởng đến việc cho phép hoặc từ chối các hành động cụ thể thông qua Middleware hoặc các lớp kiểm tra quyền của API.
