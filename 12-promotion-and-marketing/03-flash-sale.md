# Flash sale

### Quản lý kho hàng ảo và giữ chỗ sản phẩm trong giỏ hàng

Khi một sản phẩm Flash Sale có số lượng rất ít nhưng hàng nghìn người cùng nhấn nút mua tại một thời điểm, hệ thống cần cơ chế trừ kho ảo ngay khi người dùng cho sản phẩm vào giỏ hàng hoặc bắt đầu tạo đơn hàng. Vấn đề đặt ra là nếu người dùng giữ chỗ nhưng không thanh toán, số lượng này phải được hoàn lại kho sau một khoảng thời gian nhất định để người khác có thể mua. Bạn cần thiết kế làm sao để cân bằng giữa việc không bị bán quá số lượng thực tế và không bị tồn kho ảo do người dùng ảo giữ chỗ.

### Cấu hình khung giờ chạy Flash Sale lặp lại hoặc đơn lẻ

Một hệ thống Flash Sale thực tế không chỉ chạy một lần rồi thôi. Bộ phận vận hành cần thiết lập các khung giờ cố định như khung 9 giờ sáng, 12 giờ trưa, 21 giờ tối hàng ngày hoặc các đợt bùng nổ duy nhất vào ngày đôi như 11 tháng 11. Bài toán yêu cầu thiết kế dữ liệu sao cho một sản phẩm có thể tham gia vào nhiều khung giờ khác nhau với giá bán và số lượng khuyến mãi khác nhau mà không làm ảnh hưởng đến giá bán gốc của sản phẩm đó trong các giao dịch thông thường.

### Giới hạn số lượng mua tối đa trên mỗi khách hàng

Để ngăn chặn các đại lý hoặc người đầu cơ gom hết hàng giảm giá, hệ thống Flash Sale luôn có quy định mỗi tài khoản chỉ được mua tối đa một số lượng sản phẩm nhất định, ví dụ mỗi người chỉ được mua 1 chiếc điện thoại giá sốc. Hệ thống phải kiểm tra lịch sử mua hàng của người dùng đó trong khung giờ Flash Sale hiện tại để quyết định có cho phép họ thêm hàng vào giỏ hoặc thanh toán hay không, kể cả khi họ cố tình tạo nhiều đơn hàng nhỏ.

### Xử lý đồng thời cực lớn tại thời điểm mở bán

Vào đúng 0 giờ 0 phút, hàng triệu yêu cầu sẽ gửi đến API để lấy thông tin sản phẩm và nhấn nút mua. Đây là bài toán về thiết kế hệ thống và database để tránh tình trạng nghẽn cổ chai. Bạn cần tính toán việc sử dụng các lớp đệm dữ liệu hoặc hàng đợi tin nhắn để ghi nhận yêu cầu mua hàng theo thứ tự ưu tiên, đảm bảo rằng những người nhấn nút trước sẽ có cơ hội mua hàng cao hơn và hệ thống không bị sập khi cơ sở dữ liệu bị quá tải truy vấn ghi.

### Thay đổi trạng thái hiển thị sản phẩm theo thời gian thực

Trước khi Flash Sale bắt đầu, sản phẩm thường ở trạng thái sắp mở bán và nút mua bị vô hiệu hóa. Đúng thời điểm bắt đầu, nút mua phải được kích hoạt và giá hiển thị phải chuyển sang giá khuyến mãi ngay lập tức trên tất cả các thiết bị của người dùng. Tương tự, khi sản phẩm hết hàng hoặc hết giờ, trạng thái phải cập nhật là đã hết hàng hoặc kết thúc chương trình. Việc thiết kế API và cơ chế cập nhật trạng thái này cần sự đồng bộ rất cao giữa backend và frontend.

### Quản lý danh sách người dùng chờ và hàng đợi mua hàng

Trong các đợt Flash Sale cực lớn, số lượng người truy cập vượt xa khả năng xử lý tức thời của hệ thống thanh toán. Thay vì báo lỗi, hệ thống thường đưa người dùng vào một hàng đợi ảo. Bài toán này yêu cầu thiết kế logic để xếp hàng người dùng, thông báo cho họ vị trí trong hàng và điều hướng họ đến trang thanh toán khi đến lượt. Database cần lưu trữ được trạng thái của hàng đợi này và đảm bảo công bằng cho những người đến sớm.

### Áp dụng mức giá ưu đãi theo phân hạng hội viên trong Flash Sale

Nhiều sàn thương mại điện tử kết hợp Flash Sale với chương trình khách hàng thân thiết, ví dụ thành viên Kim Cương được quyền mua sớm hơn người thường 15 phút hoặc được giảm thêm 5% trên giá Flash Sale. Điều này làm phức tạp hóa logic tính giá và kiểm tra điều kiện truy cập. Bạn cần thiết kế các bảng quan hệ sao cho việc truy vấn phân hạng người dùng và điều kiện tham gia Flash Sale diễn ra cực nhanh mà không làm chậm quá trình thanh toán.

### Đối soát và hoàn tiền sau chiến dịch Flash Sale

Sau khi chiến dịch kết thúc, bộ phận vận hành cần báo cáo chính xác bao nhiêu sản phẩm đã bán, bao nhiêu đơn bị hủy, và doanh thu thực tế là bao nhiêu. Đặc biệt là xử lý các đơn hàng bị lỗi thanh toán nhưng đã bị trừ tiền của khách hàng. Bài toán này tập trung vào thiết kế database cho phần lịch sử giao dịch và log hệ thống, đảm bảo tính nhất quán giữa số lượng tồn kho giảm đi và số lượng đơn hàng thực tế được tạo ra.
