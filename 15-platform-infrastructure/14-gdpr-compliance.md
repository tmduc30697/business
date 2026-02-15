# GDPR compliance

### Quản lý sự đồng thuận và lịch sử thay đổi Consent

Hệ thống cần lưu trữ các loại đồng thuận khác nhau từ người dùng như đồng thuận nhận email marketing, đồng thuận chia sẻ dữ liệu cho bên thứ ba, hoặc đồng thuận thu thập cookie hành vi. Mỗi khi người dùng thay đổi trạng thái đồng thuận từ bật sang tắt hoặc ngược lại, hệ thống phải ghi lại nhật ký chi tiết bao gồm thời điểm thay đổi và phiên bản điều khoản tại thời điểm đó. Bài toán này yêu cầu thiết kế database sao cho có thể truy xuất nhanh chóng trạng thái hiện tại của người dùng để các dịch vụ khác như gửi mail hay phân tích dữ liệu có thể kiểm tra trước khi thực hiện hành động.

### Thực hiện quyền được quên thông qua xóa dữ liệu phân tầng

Khi người dùng yêu cầu xóa tài khoản và dữ liệu cá nhân, hệ thống không chỉ xóa bản ghi trong bảng người dùng mà còn phải xử lý dữ liệu ở các bảng liên quan như địa chỉ, số điện thoại, và lịch sử giao dịch. Tuy nhiên, một số dữ liệu như hóa đơn tài chính phải được giữ lại theo quy định thuế nhưng cần phải được ẩn danh hóa để không còn liên kết với danh tính người dùng. Bạn cần thiết kế một quy trình xóa hoặc ẩn danh hóa dữ liệu có tính chất bắc cầu để đảm bảo không còn dấu vết định danh nào sót lại trong hệ thống sau khi quá trình hoàn tất.

### Xuất dữ liệu cá nhân dưới định dạng máy có thể đọc được

Theo quyền về tính di động của dữ liệu, người dùng có quyền yêu cầu hệ thống xuất toàn bộ dữ liệu cá nhân mà họ đã cung cấp. Hệ thống cần một dịch vụ có khả năng thu thập dữ liệu từ nhiều bảng khác nhau, từ thông tin hồ sơ đến lịch sử hoạt động và phản hồi hỗ trợ, sau đó đóng gói chúng thành một tệp tin nén chứa các định dạng tiêu chuẩn như JSON hoặc CSV. Bài toán này đặt ra thách thức về thiết kế API và xử lý bất đồng bộ để tránh làm treo hệ thống khi dữ liệu của người dùng quá lớn.

### Quản lý thời gian lưu trữ dữ liệu tự động

Mỗi loại dữ liệu cá nhân đều có một vòng đời nhất định và không được phép lưu trữ vô thời hạn nếu không còn mục đích sử dụng. Ví dụ, dữ liệu định vị người dùng chỉ được giữ trong 6 tháng, hoặc hồ sơ ứng viên không trúng tuyển chỉ được giữ trong 2 năm. Hệ thống cần một cơ chế tự động quét và dọn dẹp hoặc ẩn danh hóa các bản ghi đã quá hạn dựa trên các quy tắc cấu hình linh hoạt. Điều này yêu cầu thiết kế database có các trường đánh dấu thời gian rõ ràng và logic hệ thống có thể cấu hình thời hạn cho từng loại thực thể dữ liệu.

### Lưu vết truy cập dữ liệu cá nhân của quản trị viên

Để đảm bảo tính minh bạch, hệ thống cần ghi lại mọi hành động truy cập hoặc chỉnh sửa dữ liệu cá nhân của người dùng từ phía nhân viên vận hành hoặc quản trị viên hệ thống. Nhật ký này phải bao gồm thông tin ai đã xem dữ liệu của ai, xem vào lúc nào và xem những trường thông tin cụ thể nào. Đây là bài toán về thiết kế Audit Log quy mô lớn, nơi dữ liệu nhật ký có thể tăng trưởng rất nhanh và cần được bảo vệ để không bị chỉnh sửa bởi chính những người quản trị đó.

### Quản lý quyền truy cập dữ liệu theo nguyên tắc tối thiểu

Hệ thống cần phân quyền chi tiết để nhân viên ở các bộ phận khác nhau chỉ có thể xem những phần dữ liệu cá nhân cần thiết cho công việc của họ. Ví dụ, nhân viên giao hàng chỉ thấy số điện thoại và địa chỉ, trong khi nhân viên kỹ thuật chỉ thấy ID người dùng và log hệ thống mà không thấy email cá nhân. Bài toán này yêu cầu thiết kế một hệ thống phân quyền dựa trên vai trò kết hợp với chính sách bảo mật ở cấp độ trường thông tin trong cơ sở dữ liệu để đảm bảo dữ liệu nhạy cảm luôn được che giấu mặc định.

### Xử lý yêu cầu hạn chế xử lý dữ liệu

Trong một số trường hợp tranh chấp, người dùng có thể yêu cầu hệ thống tạm dừng việc xử lý dữ liệu của họ nhưng không xóa bỏ. Khi đó, dữ liệu vẫn tồn tại trong cơ sở dữ liệu nhưng các dịch vụ như gửi thông báo, phân tích hành vi hoặc đề xuất sản phẩm phải bỏ qua người dùng này. Bạn cần thiết kế một cơ chế đánh dấu trạng thái đặc biệt cho tài khoản để các logic nghiệp vụ trên toàn hệ thống có thể nhận diện và tạm dừng các tiến trình xử lý tự động liên quan đến người dùng đó một cách nhất quán.

### Phân loại và gán nhãn dữ liệu nhạy cảm trong toàn hệ thống

Hệ thống cần một bản đồ dữ liệu để xác định rõ trường thông tin nào là dữ liệu cá nhân thông thường và trường nào là dữ liệu nhạy cảm như thông tin y tế, tôn giáo hoặc sinh trắc học. Việc gán nhãn này giúp hệ thống áp dụng các biện pháp bảo vệ tăng cường như mã hóa dữ liệu ở cấp độ lưu trữ hoặc yêu cầu xác thực hai lớp khi truy cập. Bài toán thiết kế ở đây là làm sao để tích hợp các siêu dữ liệu bảo mật vào cấu trúc database hiện tại mà không làm phức tạp hóa quá trình truy vấn dữ liệu của các ứng dụng.
