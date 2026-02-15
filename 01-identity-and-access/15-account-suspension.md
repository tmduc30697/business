# Account suspension

### Quản lý vi phạm đa cấp độ cho sàn thương mại điện tử

Hệ thống cần quản lý việc tạm ngưng tài khoản của người bán dựa trên điểm uy tín. Khi một người bán có tỷ lệ đơn hàng ảo hoặc khiếu nại hàng giả cao, hệ thống sẽ tự động chuyển trạng thái tài khoản sang tạm ngưng. Bài toán yêu cầu lưu trữ lịch sử các lần vi phạm, phân loại mức độ nghiêm trọng và thời gian tạm ngưng tương ứng (ví dụ: 3 ngày, 7 ngày hoặc vô hạn). Bạn cần xử lý việc tự động mở khóa khi hết hạn và ngăn chặn người dùng này tạo tài khoản mới bằng cùng một thông tin định danh hoặc số điện thoại.

### Kiểm soát gian lận khuyến mãi trong ứng dụng giao đồ ăn

Trong các chiến dịch marketing lớn, nhiều người dùng tạo hàng loạt tài khoản để lạm dụng mã giảm giá. Hệ thống cần phát hiện các nhóm tài khoản có chung địa chỉ IP, cùng thiết bị hoặc cùng phương thức thanh toán để tạm ngưng hàng loạt. Bài toán đặt ra thách thức về việc thiết kế cơ sở dữ liệu để liên kết các thuộc tính định danh thiết bị và xử lý logic truy vấn nhanh nhằm ngăn chặn giao dịch ngay tại thời điểm thanh toán nếu phát hiện dấu hiệu gian lận.

### Hệ thống kiểm duyệt nội dung tự động trên mạng xã hội

Khi người dùng đăng tải nội dung vi phạm tiêu chuẩn cộng đồng như ngôn từ thù ghét hoặc hình ảnh nhạy cảm, tài khoản của họ sẽ bị tạm ngưng các tính năng cụ thể thay vì toàn bộ hệ thống. Ví dụ, người dùng vẫn có thể xem bài viết nhưng bị cấm bình luận và đăng bài trong 48 giờ. Bài toán yêu cầu thiết kế phân quyền linh hoạt (Permissions/Scopes) trong cơ sở dữ liệu và API để kiểm tra trạng thái quyền hạn của người dùng theo thời gian thực trước mỗi hành động.

### Kháng cáo và quy trình phê duyệt hoàn tác tạm ngưng

Sau khi tài khoản bị tạm ngưng, người dùng có quyền gửi đơn kháng cáo kèm theo bằng chứng hình ảnh hoặc văn bản giải trình. Bài toán này tập trung vào quy trình nghiệp vụ (Workflow) giữa người dùng và nhân viên quản trị. Bạn cần thiết kế hệ thống lưu trữ các yêu cầu kháng cáo, trạng thái phê duyệt (đang chờ, đã chấp nhận, đã từ chối) và nhật ký thao tác của nhân viên để đảm bảo tính minh bạch. Nếu kháng cáo thành công, hệ thống phải khôi phục trạng thái tài khoản và xóa bỏ các hạn chế hiện tại.

### Giới hạn truy cập do nghi ngờ tài khoản bị xâm nhập

Khi phát hiện hành vi đăng nhập bất thường từ một quốc gia xa lạ hoặc nhập sai mật khẩu quá nhiều lần, hệ thống sẽ tạm ngưng tài khoản để bảo vệ chủ sở hữu. Bài toán này yêu cầu thiết kế hệ thống ghi nhận lịch sử đăng nhập (Audit Log) với các thông tin về thiết bị và vị trí địa lý. API cần có cơ chế gửi mã xác thực qua email hoặc tin nhắn để người dùng tự mở khóa tài khoản, đồng thời vô hiệu hóa tất cả các phiên đăng nhập (Sessions) đang hoạt động trên các thiết bị khác.

### Quản lý thanh toán quá hạn cho dịch vụ phần mềm thuê bao

Đối với các dịch vụ SaaS, nếu khách hàng không thanh toán hóa đơn đúng hạn sau nhiều lần thông báo, tài khoản doanh nghiệp sẽ bị chuyển sang trạng thái tạm ngưng. Bài toán yêu cầu thiết kế sự liên kết giữa bảng hóa đơn, gói dịch vụ và trạng thái tài khoản. Khi ở trạng thái này, người dùng chỉ có thể truy cập vào trang thanh toán và không thể sử dụng các tính năng chuyên môn. Hệ thống cần cơ chế thông báo (Notification) định kỳ trước và sau khi thực hiện lệnh tạm ngưng.

### Hệ thống Shadow Ban và hạn chế hiển thị công khai

Trong một số trường hợp đặc biệt, hệ thống không thông báo trực tiếp việc tạm ngưng mà sử dụng hình thức hạn chế hiển thị. Người dùng vẫn thấy mình hoạt động bình thường nhưng nội dung họ tạo ra không hiển thị với bất kỳ ai khác. Bài toán này đòi hỏi việc thiết kế các cờ trạng thái (Flags) trong database sao cho các câu lệnh truy vấn dữ liệu (Query) phía người xem khác phải tự động lọc bỏ nội dung từ những tài khoản đang bị đánh dấu này mà không làm giảm hiệu năng hệ thống.
