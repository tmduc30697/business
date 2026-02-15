# Schedule publish time

### Chiến dịch khuyến mãi Flash Sale theo giờ vàng

Trong các sàn thương mại điện tử, người bán thường muốn chuẩn bị sẵn các sản phẩm đặc biệt cho khung giờ Flash Sale. Bài toán đặt ra là sản phẩm phải ở trạng thái chờ và tự động hiển thị đúng vào lúc 0h ngày khuyến mãi, sau đó tự động ẩn đi hoặc chuyển về giá gốc khi kết thúc khung giờ đó vào lúc 2h sáng. Hệ thống cần đảm bảo tính chính xác về thời gian đến từng giây để tránh việc người dùng mua được hàng giá rẻ trước hoặc sau khi chương trình kết thúc.

### Phát hành bộ sưu tập thời trang theo mùa

Một nhãn hàng thời trang cao cấp dự định ra mắt bộ sưu tập mùa Đông vào tuần tới. Họ có hàng trăm mẫu mã cần được nhập liệu, kiểm tra hình ảnh và mô tả trước đó cả tháng. Thay vì nhân viên vận hành phải trực đêm để bấm nút đăng bài, họ thiết lập lịch đăng đồng loạt cho toàn bộ danh mục sản phẩm vào đúng thời điểm buổi lễ ra mắt diễn ra. Yêu cầu hệ thống phải xử lý được việc xuất bản hàng loạt sản phẩm cùng một lúc mà không làm treo trang web hoặc gây nghẽn truy vấn.

### Quản lý nội dung số và game trả phí theo múi giờ

Một nền tảng phân phối trò chơi điện tử toàn cầu cần phát hành một bản mở rộng mới. Do chênh lệch múi giờ, sản phẩm cần được mở bán tại thị trường Mỹ vào lúc 9h sáng của họ, tương đương với buổi tối tại Việt Nam. Bài toán yêu cầu database phải lưu trữ thời gian theo chuẩn quốc tế để việc tính toán thời điểm publish chính xác cho từng khu vực địa lý nếu cần, hoặc đơn giản là đồng bộ hóa theo một múi giờ gốc của máy chủ.

### Sản phẩm giới hạn số lượng trong thời gian ngắn

Một cửa hàng bánh ngọt thủ công chỉ mở bán loại bánh trung thu đặc biệt trong vòng 15 ngày trước rằm. Chủ cửa hàng muốn thiết lập lịch unpublish tự động để sản phẩm biến mất khỏi thực đơn trực tuyến ngay khi hết thời hạn, tránh việc khách hàng vẫn đặt hàng khi nguyên liệu đã hết. Logic này cần kết hợp giữa điều kiện thời gian và có thể là cả điều kiện về số lượng tồn kho trong kho dữ liệu.

### Cập nhật menu món ăn theo ca làm việc của nhà hàng

Một ứng dụng đặt đồ ăn cần thay đổi thực đơn giữa thực đơn bữa sáng và thực đơn bữa trưa. Các món điểm tâm sẽ tự động unpublish vào lúc 10h30 sáng hàng ngày và các món ăn trưa sẽ được publish thay thế ngay sau đó. Bài toán này đòi hỏi thiết kế hệ thống có tính chu kỳ, thay vì chỉ là một mốc thời gian đơn lẻ, giúp người quản lý không phải thiết lập lại lịch trình mỗi ngày.

### Kiểm duyệt nội dung trước khi xuất bản tự động

Trong một hệ thống marketplace có nhiều người bán, các sản phẩm sau khi được chỉnh sửa lịch đăng phải đi qua một bước kiểm duyệt của quản trị viên. Sản phẩm chỉ được phép tự động publish vào thời điểm đã chọn nếu trạng thái kiểm duyệt là đã phê duyệt. Nếu đến giờ hẹn mà chưa được duyệt, hệ thống phải hủy lệnh publish và thông báo cho người bán. Đây là bài toán kết hợp giữa state machine và scheduling.

### Thay đổi giá sản phẩm theo sự kiện ngắn hạn

Thay vì tạo sản phẩm mới, hệ thống cho phép đặt lịch để thay đổi thuộc tính của sản phẩm hiện tại. Ví dụ, một chiếc điện thoại sẽ được giảm giá 20% vào ngày độc thân và tự động quay về giá cũ vào ngày hôm sau. Thực chất đây là việc publish một phiên bản dữ liệu mới của sản phẩm và unpublish phiên bản cũ dựa trên mốc thời gian, đòi hỏi thiết kế database có khả năng lưu trữ lịch sử phiên bản hoặc bảng giá theo thời gian.

### Xuất bản tài liệu học tập theo lộ trình khóa học

Một nền tảng học trực tuyến bán các khóa học theo dạng bài giảng giải phóng dần dần. Bài giảng thứ nhất xuất bản ngay khi học viên mua khóa học, nhưng bài giảng thứ hai sẽ tự động được publish sau đó đúng 7 ngày. Bài toán này yêu cầu hệ thống tính toán thời điểm publish dựa trên một mốc thời gian động là thời điểm người dùng kích hoạt khóa học, thay vì một ngày cố định trong lịch.
