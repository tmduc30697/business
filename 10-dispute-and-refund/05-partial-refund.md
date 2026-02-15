# Partial refund

### Quản lý hoàn tiền theo đơn vị sản phẩm trong thương mại điện tử

Khách hàng đặt một đơn hàng gồm nhiều loại mặt hàng khác nhau như quần áo, giày dép và phụ kiện. Sau khi nhận hàng, khách hàng phát hiện một chiếc áo bị lỗi đường may nhưng vẫn muốn giữ lại đôi giày và túi xách. Hệ thống cần cho phép nhân viên vận hành chọn đúng mã sản phẩm cụ thể và số lượng của sản phẩm đó để thực hiện hoàn tiền, trong khi các sản phẩm khác vẫn giữ nguyên trạng thái đã thanh toán.

### Xử lý hoàn phí vận chuyển linh hoạt

Một đơn hàng được giao thành nhiều kiện khác nhau do hàng nằm ở các kho khác nhau. Kiện hàng đầu tiên đến đúng hạn nhưng kiện hàng thứ hai bị chậm trễ nghiêm trọng so với cam kết. Để chăm sóc khách hàng, bộ phận hỗ trợ quyết định hoàn lại toàn bộ hoặc một phần phí vận chuyển mà khách hàng đã trả ban đầu, tuy nhiên giá trị tiền hàng của các sản phẩm vẫn được giữ nguyên không thay đổi.

### Hoàn tiền dựa trên giá trị khuyến mãi và mã giảm giá

Khách hàng áp dụng mã giảm giá dạng trừ thẳng một số tiền cố định cho đơn hàng có tổng giá trị lớn. Khi khách hàng muốn trả lại một sản phẩm trong đơn hàng đó, hệ thống không thể hoàn lại toàn bộ giá tiền niêm yết của sản phẩm. Thay vào đó, hệ thống phải tính toán lại tỷ lệ chiết khấu đã phân bổ cho sản phẩm đó để hoàn trả số tiền thực tế mà khách hàng đã chi trả sau khi trừ đi phần ưu đãi tương ứng.

### Khấu trừ phí lưu kho hoặc phí kiểm định khi trả hàng

Trong mô hình kinh doanh đồ xa xỉ hoặc đồ điện tử cũ, khách hàng có quyền trả lại hàng trong vòng bảy ngày. Tuy nhiên, quy định của cửa hàng là khách hàng sẽ phải chịu một khoản phí kiểm định hoặc phí lưu kho nhất định. Khi thực hiện lệnh hoàn tiền, hệ thống phải ghi nhận giá trị gốc của đơn hàng, số tiền khấu trừ và số tiền thực tế chuyển về tài khoản khách hàng để đảm bảo khớp số liệu kế toán.

### Hoàn tiền theo gói sản phẩm combo

Cửa hàng bán một combo gồm ba sản phẩm với mức giá ưu đãi thấp hơn mua lẻ. Khách hàng nhận hàng nhưng muốn trả lại một sản phẩm trong combo vì không vừa kích cỡ. Bài toán đặt ra là hệ thống phải xác định giá trị của từng cấu phần trong combo để hoàn tiền một phần, hoặc chuyển đổi đơn hàng từ giá combo sang giá bán lẻ của các sản phẩm còn lại và chỉ hoàn lại phần chênh lệch.

### Xử lý hoàn tiền cho đơn hàng thanh toán đa phương thức

Khách hàng thanh toán một đơn hàng bằng cách kết hợp giữa điểm thưởng hệ thống và tiền mặt qua ví điện tử. Khi có yêu cầu hoàn tiền một phần giá trị đơn hàng, hệ thống cần có quy tắc ưu tiên để quyết định sẽ hoàn trả bằng điểm trước hay hoàn trả tiền mặt trước vào ví điện tử của khách hàng, đồng thời phải đảm bảo tổng giá trị hoàn không vượt quá số tiền thực tế ở từng phương thức.

### Hoàn tiền do thiếu hàng hoặc giao sai mẫu

Sau khi khách hàng đã thanh toán trước cho đơn hàng, đơn vị vận chuyển phát hiện một món hàng trong kho đã hết hoặc bị hư hỏng nên không thể giao đủ. Thay vì hủy toàn bộ đơn hàng, hệ thống tự động thực hiện lệnh hoàn lại đúng số tiền của món hàng thiếu đó ngay tại thời điểm đóng gói để khách hàng vẫn nhận được những món còn lại mà không cần thực hiện thêm thao tác thủ công nào.

### Điều chỉnh giá sau khi mua hàng

Khách hàng mua một sản phẩm với giá niêm yết, nhưng ngay ngày hôm sau cửa hàng có chương trình giảm giá lớn cho chính sản phẩm đó. Để giữ chân khách hàng thân thiết, cửa hàng đồng ý hoàn lại phần tiền chênh lệch giữa giá cũ và giá mới dưới dạng số dư tài khoản. Hệ thống cần ghi nhận đây là một khoản hoàn tiền một phần dựa trên sự thay đổi về giá bán thay vì trả hàng vật lý.

### Hoàn tiền cho dịch vụ theo thời gian sử dụng

Một người dùng đăng ký gói thành viên cao cấp theo năm nhưng quyết định hạ cấp xuống gói cơ bản sau sáu tháng sử dụng. Hệ thống cần tính toán số tiền tương ứng với khoảng thời gian sáu tháng còn lại chưa sử dụng để hoàn trả lại cho người dùng, sau khi đã trừ đi các chi phí quản lý hoặc phí kích hoạt dịch vụ ban đầu.

### Hoàn tiền một phần trong mô hình đặt đồ ăn trực tuyến

Khách hàng đặt một bữa tối gồm nhiều món ăn nhưng khi nhận hàng thì một món bị đổ vỡ hoặc thiếu nước sốt đi kèm. Thay vì yêu cầu shipper quay lại hoặc hủy cả bữa ăn, khách hàng yêu cầu khiếu nại để được hoàn lại một phần tiền tương ứng với món bị hỏng hoặc một khoản bồi thường nhỏ cho trải nghiệm không tốt, trong khi các món khác vẫn được sử dụng bình thường.
