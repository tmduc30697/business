# Order creation

### Xử lý đơn hàng đa trạng thái và lịch sử thay đổi

Trong thực tế, một đơn hàng không dừng lại ở việc tạo xong là kết thúc. Bạn cần thiết kế hệ thống sao cho có thể theo dõi toàn bộ vòng đời của đơn hàng từ lúc vừa thanh toán, đang đóng gói, đơn vị vận chuyển đã lấy hàng, cho đến khi giao thành công hoặc bị hoàn trả. Thách thức ở đây là việc lưu trữ lịch sử thay đổi trạng thái để bộ phận chăm sóc khách hàng có thể tra cứu xem ai đã tác động vào đơn hàng vào thời điểm nào.

### Đơn hàng chứa sản phẩm có nhiều biến thể phức tạp

Bài toán này tập trung vào cấu trúc dữ liệu của giỏ hàng. Một sản phẩm như điện thoại có thể có nhiều màu sắc, dung lượng bộ nhớ khác nhau với mức giá riêng biệt. Khi khách hàng thanh toán, hệ thống phải "chụp ảnh" được chính xác phiên bản sản phẩm tại thời điểm đó. Điều này ngăn chặn việc dữ liệu đơn hàng bị thay đổi nếu sau này người quản trị cập nhật lại tên sản phẩm hoặc giá bán trong kho hàng chung.

### Áp dụng đa dạng loại mã giảm giá và thuế phí

Một đơn hàng thực tế thường đi kèm với các phép tính khấu trừ phức tạp. Bạn cần giải quyết việc áp dụng mã giảm giá của sàn, mã giảm giá của shop, và các loại phí vận chuyển sau khi đã trừ ưu đãi. Hệ thống cần lưu trữ rõ ràng số tiền gốc, số tiền được giảm theo từng loại mã và tổng số tiền cuối cùng khách hàng thực trả để phục vụ cho việc đối soát kế toán sau này.

### Đơn hàng từ nhiều nhà cung cấp trong một lần thanh toán

Trên các sàn thương mại điện tử, người mua có thể bỏ sản phẩm từ nhiều cửa hàng khác nhau vào cùng một giỏ và thanh toán một lần. Bài toán đặt ra là làm thế nào để thiết kế Database và API để vừa hiển thị được một mã thanh toán duy nhất cho khách hàng, vừa có thể tách thành các đơn hàng con riêng biệt cho từng nhà bán hàng để họ quản lý việc đóng gói và vận chuyển độc lập.

### Quản lý tồn kho ảo và giữ hàng trong hàng chờ

Khi khách hàng bấm thanh toán nhưng chưa hoàn tất thủ tục ở cổng thanh toán ngân hàng, hệ thống cần có cơ chế giữ hàng tạm thời để tránh trường hợp người khác mua mất. Bạn cần thiết kế một cơ chế xử lý các đơn hàng đang chờ thanh toán này, bao gồm cả việc tự động hủy đơn và hoàn lại số lượng tồn kho nếu sau một khoảng thời gian nhất định khách hàng không thực hiện giao dịch thành công.

### Xuất hóa đơn tài chính và lưu trữ thông tin pháp lý

Bên cạnh thông tin mua hàng thông thường, nhiều khách hàng doanh nghiệp yêu cầu xuất hóa đơn đỏ. Hệ thống cần có các bảng dữ liệu riêng để lưu trữ thông tin thuế, địa chỉ công ty và tên doanh nghiệp. Dữ liệu này cần được liên kết chặt chẽ với đơn hàng nhưng phải đảm bảo tính toàn vẹn, ngay cả khi người dùng thay đổi thông tin cá nhân trong tương lai thì thông tin trên hóa đơn đã xuất vẫn phải giữ nguyên.

### Xử lý khối lượng đơn hàng lớn trong các sự kiện giảm giá

Vào các ngày lễ mua sắm, số lượng đơn hàng được tạo ra trong một giây có thể tăng đột biến. Bài toán này đòi hỏi bạn thiết kế hệ thống có khả năng ghi dữ liệu cực nhanh mà không gây nghẽn cổ chai cho cơ sở dữ liệu. Bạn có thể cần cân nhắc việc sử dụng các hàng đợi tin nhắn để tiếp nhận yêu cầu thanh toán và xử lý việc tạo đơn hàng dưới nền nhằm đảm bảo trải nghiệm người dùng không bị gián đoạn.

### Đồng bộ đơn hàng với các hệ thống vận chuyển bên thứ ba

Sau khi đơn hàng được tạo, thông tin cần được đẩy sang các đơn vị giao hàng như Giao Hàng Nhanh hay Viettel Post. Bạn cần thiết kế hệ thống lưu trữ các mã vận đơn, thông tin định vị bưu kiện và các mốc thời gian lấy hàng từ phía đối tác. Việc đồng bộ dữ liệu hai chiều giữa hệ thống của bạn và API của đơn vị vận chuyển là yếu tố then chốt để khách hàng có thể theo dõi hành trình đơn hàng ngay trên ứng dụng của bạn.
