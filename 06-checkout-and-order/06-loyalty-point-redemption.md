# Loyalty point redemption

### Tích điểm và tiêu điểm đa nền tảng theo tỷ lệ hối đoái động

Một hệ thống bán lẻ sở hữu chuỗi cửa hàng vật lý và trang thương mại điện tử muốn đồng nhất trải nghiệm khách hàng. Bài toán yêu cầu quản lý việc tích điểm dựa trên giá trị thanh toán thực tế sau khi trừ các loại mã giảm giá khác. Tỷ lệ quy đổi từ tiền sang điểm và từ điểm sang tiền có thể thay đổi tùy theo phân hạng thành viên hoặc các chiến dịch đặc biệt. Hệ thống cần ghi nhận chính xác nguồn gốc điểm và thời hạn sử dụng của từng đợt điểm để đảm bảo quy tắc điểm nào hết hạn trước thì được tiêu dùng trước.

### Giới hạn mức tiêu điểm tối đa dựa trên danh mục sản phẩm

Để bảo vệ biên lợi nhuận, doanh nghiệp không cho phép khách hàng dùng điểm để thanh toán toàn bộ đơn hàng. Thay vào đó, mỗi nhóm sản phẩm sẽ có một cấu hình riêng về tỷ lệ giảm giá tối đa bằng điểm. Ví dụ, các mặt hàng điện tử chỉ cho phép dùng điểm thanh toán tối đa mười phần trăm giá trị, trong khi các mặt hàng thời trang có thể cho phép lên đến năm mươi phần trăm. Bài toán này đòi hỏi việc tính toán mức điểm tối đa có thể sử dụng ngay tại bước giỏ hàng dựa trên sự kết hợp của nhiều loại mặt hàng khác nhau.

### Hoàn điểm và xử lý tranh chấp khi hủy đơn hàng

Khi một đơn hàng được thanh toán một phần bằng điểm bị hủy hoặc trả hàng, hệ thống cần có cơ chế hoàn trả điểm minh bạch. Thách thức nằm ở chỗ nếu đơn hàng chỉ bị trả một phần, lượng điểm hoàn lại phải được tính toán tỷ lệ thuận với giá trị món hàng đó. Ngoài ra, nếu điểm dùng để mua hàng đã hết hạn trong thời gian chờ giao hàng, hệ thống cần đưa ra quyết định có gia hạn điểm hay hủy bỏ số điểm đó. Việc lưu vết lịch sử giao dịch điểm phải cực kỳ chi tiết để phục vụ công tác đối soát và chăm sóc khách hàng.

### Đổi điểm lấy mã giảm giá hoặc quà tặng vật lý

Thay vì trừ tiền trực tiếp vào hóa đơn, khách hàng có thể dùng điểm tích lũy để đổi lấy các voucher giảm giá hoặc các phần quà hiện vật có trong kho. Bài toán này mở rộng sang quản lý kho quà tặng, tình trạng tồn kho của voucher và giới hạn số lượng đổi quà trên mỗi khách hàng. Bạn cần thiết kế quy trình từ lúc khách hàng nhấn đổi điểm, trừ điểm tạm thời, xác nhận nhận quà thành công cho đến khi mã voucher được kích hoạt hoặc quà tặng được vận chuyển đi.

### Hệ thống ví điểm dùng chung cho hộ gia đình hoặc nhóm

Một số nền tảng cho phép người dùng liên kết tài khoản để tích lũy và sử dụng chung một quỹ điểm thưởng. Điều này đặt ra bài toán về quản lý quyền hạn: ai là chủ nhóm có quyền tiêu điểm, ai chỉ có quyền tích điểm. Khi có giao dịch tiêu điểm, hệ thống cần ghi lại dấu chân của người thực hiện nhưng vẫn cập nhật số dư vào quỹ chung. Ngoài ra, việc xử lý khi một thành viên rời nhóm và muốn mang theo số điểm mình đã đóng góp cũng là một kịch bản cần được tính đến.

### Tích điểm thông qua hành động không mua hàng và nhiệm vụ

Để tăng tương tác, hệ thống cho phép người dùng nhận điểm từ các hoạt động như đánh giá sản phẩm, chia sẻ ứng dụng, hoặc đăng nhập liên tục trong nhiều ngày. Mỗi loại hành động này có giới hạn số lần nhận điểm trong một ngày hoặc một tuần để tránh việc gian lận điểm. Bài toán này tập trung vào việc thiết kế công cụ cấu hình nhiệm vụ linh hoạt, cho phép nhân viên marketing dễ dàng tạo ra các chương trình mới mà không cần can thiệp vào mã nguồn của hệ thống.

### Chuyển đổi điểm thưởng giữa các đối tác trong hệ sinh thái

Một liên minh các doanh nghiệp cho phép khách hàng chuyển đổi điểm tích lũy từ thương hiệu này sang thương hiệu khác. Bài toán yêu cầu xử lý các giao dịch xuyên biên giới giữa các hệ thống khác nhau, tính toán phí chuyển đổi và tỷ giá quy đổi giữa các loại đơn vị điểm. Điều này đòi hỏi thiết kế hệ thống có tính nhất quán cao, xử lý giao dịch phân tán để đảm bảo điểm không bị mất đi hoặc tự động sinh ra trong quá trình truyền tải dữ liệu giữa các bên.

### Ưu đãi điểm thưởng theo sự kiện và khung giờ vàng

Doanh nghiệp triển khai các chương trình nhân đôi hoặc nhân ba số điểm tích lũy khi mua hàng vào các khung giờ nhất định hoặc nhân ngày sinh nhật khách hàng. Ngược lại, vào những dịp lễ lớn, họ cũng có thể tung ra các chiến dịch tiêu điểm với giá trị ưu đãi hơn bình thường. Bài toán yêu cầu công cụ cấu hình thời gian thực (real-time) có khả năng áp dụng các quy tắc ưu đãi chồng chéo lên nhau và đảm bảo hệ thống tính toán chính xác số điểm cuối cùng mà khách hàng nhận được hoặc tiêu đi tại thời điểm thanh toán.
