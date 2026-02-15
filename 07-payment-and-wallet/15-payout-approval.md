# Payout approval

### Kiểm soát hạn mức rút tiền theo cấp bậc tài khoản

Trong hệ thống này, người dùng được phân thành nhiều hạng khác nhau như Đồng, Bạc, Vàng dựa trên lịch sử giao dịch. Mỗi hạng sẽ có một hạn mức rút tiền tối đa trong ngày và số lần rút tối đa trong tháng. Khi người dùng gửi yêu cầu vượt quá hạn mức tự động, hệ thống không từ chối ngay mà chuyển sang trạng thái chờ admin phê duyệt thủ công. Bạn cần thiết kế cách lưu trữ cấu hình hạn mức linh hoạt và logic kiểm tra điều kiện trước khi tạo bản ghi yêu cầu rút tiền.

### Phê duyệt đa tầng cho các giao dịch giá trị lớn

Đối với các doanh nghiệp thương mại điện tử, việc rút tiền từ ví hoa hồng của đại lý thường có giá trị rất cao. Quy trình yêu cầu một đơn hàng phải đi qua ít nhất hai cấp phê duyệt: Kế toán viên kiểm tra tính hợp lệ của hóa đơn và Giám đốc tài chính xác nhận lệnh chuyển tiền. Hệ thống cần lưu vết chi tiết ai đã phê duyệt vào lúc nào, ghi chú của từng cấp và cơ chế chuyển trạng thái yêu cầu theo đúng trình tự nghiệp vụ.

### Cơ chế đóng băng số dư và hoàn tiền khi từ chối

Một vấn đề quan trọng khi người dùng tạo yêu cầu rút tiền là số dư trong ví phải bị trừ tạm thời hoặc chuyển vào một tài khoản treo để ngăn chặn việc chi tiêu trùng lặp. Bài toán đặt ra là nếu admin từ chối yêu cầu vì lý do thông tin ngân hàng sai lệch, hệ thống phải thực hiện hoàn trả số tiền đó về ví chính của người dùng một cách chính xác. Bạn cần xử lý tính nhất quán dữ liệu giữa bảng số dư ví và bảng lịch sử yêu cầu rút tiền.

### Quản lý danh sách trắng và tự động duyệt cho đối tác tin cậy

Để giảm tải cho admin, hệ thống cần một cơ chế tự động duyệt cho những tài khoản thuộc danh sách tin cậy hoặc các yêu cầu có giá trị nhỏ dưới một ngưỡng nhất định. Tuy nhiên, nếu tổng giá trị các lệnh tự động trong một giờ vượt quá một con số cụ thể, hệ thống sẽ tự động kích hoạt chế độ phê duyệt thủ công để đề phòng rủi ro bị tấn công chiếm quyền điều khiển tài khoản hàng loạt.

### Xử lý hậu phê duyệt và tích hợp cổng thanh toán bên thứ ba

Sau khi admin nhấn nút phê duyệt, hệ thống không chỉ đổi trạng thái mà còn phải gọi API sang các đơn vị chuyển tiền nhanh hoặc cổng thanh toán. Bài toán thực tế phát sinh khi API của bên thứ ba phản hồi chậm hoặc lỗi mạng. Hệ thống cần thiết kế trạng thái trung gian là đang xử lý chuyển tiền và cơ chế đối soát hoặc cập nhật kết quả từ phía ngân hàng để đảm bảo trạng thái cuối cùng của yêu cầu rút tiền là chính xác tuyệt đối.

### Kiểm tra dấu hiệu gian lận và cảnh báo trước khi duyệt

Trước khi admin xem xét một yêu cầu rút tiền, hệ thống cần tự động chạy các thuật toán kiểm tra rủi ro như: địa chỉ IP rút tiền có khác lạ không, tài khoản ngân hàng nhận tiền có đang nằm trong danh sách đen không, hoặc người dùng có vừa thay đổi mật khẩu trong vòng 24 giờ qua hay không. Các thông tin cảnh báo này phải được hiển thị kèm theo yêu cầu rút tiền để admin có cơ sở đưa ra quyết định chính xác.

### Quản lý phí rút tiền và thuế thu nhập cá nhân

Mỗi yêu cầu rút tiền thực tế thường đi kèm với các loại phí như phí cố định, phí phần trăm hoặc thuế thu nhập khấu trừ tại nguồn đối với các nền tảng tiếp thị liên kết. Khi người dùng nhập số tiền muốn rút, hệ thống phải tính toán ra số tiền thực nhận sau khi trừ các loại phí. Database cần lưu trữ rõ ràng các thành phần này để phục vụ việc xuất báo cáo tài chính và đối soát dòng tiền sau này.

### Cơ chế xếp hàng xử lý và ngăn chặn lặp lệnh

Trong các đợt trả thưởng lớn, hàng nghìn yêu cầu rút tiền có thể được gửi lên cùng lúc. Nếu admin hoặc hệ thống xử lý đồng thời mà không có cơ chế khóa bản ghi, có thể dẫn đến việc một yêu cầu được duyệt hai lần hoặc chuyển tiền thừa. Bài toán yêu cầu thiết kế hệ thống hàng đợi và cơ chế đánh dấu trạng thái sao cho tại một thời điểm chỉ có một tiến trình được phép xử lý một yêu cầu rút tiền cụ thể.

### Lưu vết thay đổi và nhật ký hành động của Admin

Để đảm bảo tính minh bạch và phục vụ công tác kiểm toán, mọi thao tác của admin từ việc xem chi tiết, yêu cầu bổ sung hồ sơ, cho đến khi phê duyệt hoặc từ chối đều phải được ghi lại. Nhật ký này bao gồm mã nhân viên, hành động, thời gian và dữ liệu cũ so với dữ liệu mới. Đây là cơ sở để truy cứu trách nhiệm nếu có sai sót trong quá trình luân chuyển dòng tiền của hệ thống.

### Phân quyền theo chi nhánh hoặc khu vực quản lý

Trong một hệ thống toàn cầu hoặc đa chi nhánh, admin ở khu vực miền Bắc chỉ được quyền phê duyệt các yêu cầu rút tiền từ người dùng thuộc khu vực đó. Bài toán yêu cầu thiết kế database về phân quyền người quản trị gắn liền với cấu trúc tổ chức và địa lý, đồng thời đảm bảo các báo cáo tổng hợp rút tiền vẫn có thể được truy xuất bởi admin cấp cao nhất ở trụ sở chính.
