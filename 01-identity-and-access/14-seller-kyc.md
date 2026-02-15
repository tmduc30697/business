# Seller KYC

### Quản lý đa dạng loại hình thực thể người bán

Hệ thống cần phân biệt rõ ràng giữa cá nhân kinh doanh, hộ kinh doanh và doanh nghiệp lớn. Mỗi loại hình sẽ yêu cầu một bộ hồ sơ khác nhau như căn cước công dân cho cá nhân hoặc giấy phép kinh doanh kèm mã số thuế cho doanh nghiệp. Việc thiết kế cần đảm bảo tính linh hoạt để khi người bán thay đổi mô hình kinh doanh, hệ thống vẫn lưu vết được lịch sử chuyển đổi mà không làm mất dữ liệu cũ.

### Quy trình phê duyệt hồ sơ nhiều bước

Một bộ hồ sơ KYC không phải lúc nào cũng được duyệt ngay lập tức bởi một người. Bài toán đặt ra là xây dựng luồng công việc nơi hồ sơ đi qua các trạng thái từ chờ xử lý, đang thẩm định, yêu cầu bổ sung đến đã phê duyệt hoặc bị từ chối. Bạn cần xử lý việc phân công hồ sơ cho nhân viên kiểm duyệt sao cho không bị trùng lặp và đảm bảo tính công bằng về khối lượng công việc giữa các kiểm duyệt viên.

### Lưu trữ và bảo mật tài liệu minh chứng

Người bán sẽ tải lên nhiều tệp tin nhạy cảm như ảnh chụp hai mặt giấy tờ tùy thân hoặc video xác thực khuôn mặt. Bài toán này tập trung vào cách tổ chức cấu trúc lưu trữ tệp tin, quản lý quyền truy cập có thời hạn để đảm bảo chỉ những người có thẩm quyền mới xem được ảnh. Ngoài ra, hệ thống phải xử lý được việc thay đổi hoặc cập nhật lại các giấy tờ đã hết hạn mà vẫn giữ được bằng chứng cho các giao dịch trong quá khứ.

### Kiểm tra trùng lặp và ngăn chặn gian lận

Hệ thống cần có cơ chế phát hiện xem một cá nhân hoặc một doanh nghiệp có đang cố tình mở nhiều gian hàng khác nhau bằng cùng một bộ giấy tờ hay không. Bài toán này yêu cầu xử lý dữ liệu để đối soát các thông tin như số định danh cá nhân, mã số thuế hoặc số điện thoại trong cơ sở dữ liệu khổng lồ nhằm đưa ra cảnh báo sớm về các hành vi có dấu hiệu trục lợi chính sách.

### Tích hợp dịch vụ định danh bên thứ ba

Thay vì kiểm tra thủ công, hệ thống cần kết nối với các API của chính phủ hoặc các đơn vị cung cấp giải pháp eKYC để tự động trích xuất thông tin từ ảnh chụp và đối chiếu độ khớp của khuôn mặt. Bạn cần thiết kế cách hệ thống gửi dữ liệu đi, nhận kết quả trả về và xử lý các tình huống dịch vụ bên thứ ba gặp sự cố hoặc trả về kết quả nghi vấn cần con người can thiệp lại.

### Quản lý lý do từ chối và tương tác với người bán

Khi một hồ sơ bị từ chối, hệ thống phải chỉ rõ lý do cụ thể cho từng loại giấy tờ như ảnh bị mờ, thông tin không khớp hoặc giấy tờ giả mạo. Bài toán này đòi hỏi việc thiết kế hệ thống thông báo thời gian thực và cho phép người bán chỉnh sửa chính xác phần thông tin bị sai mà không cần phải nộp lại toàn bộ hồ sơ từ đầu, giúp giảm thiểu thời gian chờ đợi cho cả hai bên.

### Theo dõi lịch sử thay đổi và kiểm soát tuân thủ

Các quy định về pháp lý có thể thay đổi theo thời gian, dẫn đến việc người bán đã được duyệt trước đó có thể cần bổ sung thêm giấy tờ mới. Hệ thống cần lưu lại toàn bộ lịch sử các phiên bản hồ sơ đã từng nộp, ai là người phê duyệt vào thời điểm nào và lý do tại sao. Đây là cơ sở quan trọng để phục vụ công tác hậu kiểm và báo cáo cho các cơ quan quản lý nhà nước khi có yêu cầu.

### Quản lý hạn mức bán hàng dựa trên mức độ xác minh

Hệ thống có thể cho phép người bán bắt đầu đăng sản phẩm ngay khi hoàn thành xác minh cơ bản, nhưng sẽ giới hạn doanh số hoặc số lượng đơn hàng cho đến khi hoàn tất KYC nâng cao. Bài toán này yêu cầu sự phối hợp giữa module KYC và module quản lý gian hàng để tự động mở khóa các tính năng cao cấp hoặc nâng hạn mức rút tiền ngay khi trạng thái xác minh của người bán đạt yêu cầu.
