# System announcement

### Hệ thống thông báo bảo trì theo khu vực địa lý

Bài toán yêu cầu thiết kế một nền tảng cho phép quản trị viên gửi thông báo bảo trì máy chủ đến người dùng dựa trên vị trí của họ. Hệ thống cần phân loại được người dùng theo quốc gia hoặc thành phố để tránh gửi thông báo làm phiền đến những người không thuộc vùng ảnh hưởng. Dữ liệu cần lưu trữ được lịch trình bảo trì, danh sách các khu vực bị tác động và trạng thái hiển thị của thông báo đó trên ứng dụng của người dùng cuối.

### Quản lý chiến dịch khuyến mãi đa kênh với điều kiện ràng buộc

Hệ thống cần quản lý các thông báo khuyến mãi không chỉ hiện trên ứng dụng mà còn gửi qua email hoặc tin nhắn điện thoại. Bài toán đặt ra là mỗi chương trình khuyến mãi sẽ có đối tượng mục tiêu riêng, ví dụ như chỉ dành cho khách hàng mới hoặc khách hàng thân thiết. Bạn cần thiết kế cách lưu trữ các phân đoạn khách hàng và logic để hệ thống biết được người dùng nào đã đọc thông báo để tránh gửi lặp lại gây khó chịu.

### Cập nhật chính sách bảo mật và xác nhận bắt buộc

Khi có sự thay đổi về điều khoản sử dụng hoặc chính sách bảo mật, hệ thống cần gửi một thông báo yêu cầu tất cả người dùng phải nhấn nút đồng ý trước khi tiếp tục sử dụng dịch vụ. Bài toán này đòi hỏi việc theo dõi phiên bản của chính sách và ghi lại lịch sử phản hồi của từng người dùng cụ thể. Nếu người dùng chưa xác nhận phiên bản mới nhất, hệ thống sẽ liên tục hiển thị thông báo này ở vị trí ưu tiên cao nhất.

### Thông báo khẩn cấp và độ ưu tiên hiển thị

Trong các tình huống xảy ra sự cố hệ thống nghiêm trọng, quản trị viên cần phát đi thông báo khẩn cấp ngay lập tức. Bài toán yêu cầu phân loại các mức độ thông báo như thông tin, cảnh báo và khẩn cấp. Mỗi mức độ sẽ có quy định về thời gian tồn tại và cách thức hiển thị khác nhau trên giao diện người dùng. Việc thiết kế cần đảm bảo các thông báo có độ ưu tiên cao luôn nằm ở trên cùng và không bị trôi đi bởi các thông báo thông thường khác.

### Hệ thống bảng tin nội bộ cho doanh nghiệp nhiều chi nhánh

Một công ty lớn muốn gửi các thông báo nội bộ đến nhân viên theo từng phòng ban hoặc chi nhánh khác nhau. Bài toán yêu cầu thiết kế phân quyền quản trị sao cho người quản lý chi nhánh A chỉ có thể gửi thông báo cho nhân viên chi nhánh A, trong khi giám đốc tổng công ty có thể gửi cho toàn bộ nhân viên. Hệ thống cũng cần ghi nhận số lượng nhân viên đã xem thông báo để đánh giá mức độ tiếp nhận thông tin nội bộ.

### Tự động hóa thông báo dựa trên sự kiện hệ thống

Thay vì quản trị viên nhập tay, hệ thống sẽ tự động kích hoạt thông báo dựa trên các sự kiện cụ thể, chẳng hạn như khi số dư tài khoản của người dùng xuống thấp hoặc khi một đơn hàng thay đổi trạng thái. Bài toán này tập trung vào việc thiết kế các mẫu thông báo có sẵn với các biến động để chèn thông tin cá nhân hóa. Bạn cần xử lý việc lưu trữ các cấu hình sự kiện và cách liên kết chúng với các nội dung thông báo tương ứng.

### Lưu trữ và lưu trữ tạm thời thông báo cho người dùng mới

Khi một người dùng mới đăng ký tài khoản, họ thường cần xem lại các thông báo chung đã phát hành trong vòng 30 ngày qua nhưng không cần xem các thông báo cũ hơn. Bài toán yêu cầu thiết kế cơ chế lưu trữ sao cho việc truy xuất danh sách thông báo chung của hệ thống diễn ra nhanh chóng mà không làm nặng cơ sở dữ liệu khi số lượng người dùng tăng lên hàng triệu người. Bạn cần tính đến việc tách biệt giữa thông báo cá nhân và thông báo hệ thống.

### Lên lịch phát hành và tự động gỡ bỏ thông báo

Quản trị viên muốn soạn thảo sẵn các thông báo cho chiến dịch Tết và cài đặt giờ hiển thị tự động vào đúng đêm giao thừa, sau đó tự động ẩn đi khi hết ngày mùng 3. Bài toán yêu cầu quản lý trạng thái của thông báo theo thời gian thực bao gồm các trạng thái như bản nháp, đã lên lịch, đang hiển thị và đã kết thúc. Việc thiết kế cần đảm bảo hệ thống có thể kiểm tra và cập nhật trạng thái hiển thị mà không cần sự can thiệp thủ công của con người tại thời điểm thay đổi.
