# Wallet balance

### Sàn thương mại điện tử với cơ chế thanh toán tạm giữ

Trong mô hình này, khi người mua thanh toán một đơn hàng, số tiền sẽ không chuyển ngay cho người bán mà bị đưa vào trạng thái tạm giữ. Hệ thống cần quản lý việc trừ tiền từ ví người mua, treo số tiền đó trong một tài khoản trung gian của sàn. Chỉ khi người mua xác nhận đã nhận hàng thành công hoặc sau một khoảng thời gian nhất định không có khiếu nại, số tiền này mới được giải tỏa và cộng vào số dư khả dụng của người bán. Ngược lại, nếu đơn hàng bị hủy, số tiền đang bị giữ phải được hoàn trả chính xác về ví của người mua.

### Hệ thống đặt đồ ăn và phí dịch vụ biến đổi

Khi một khách hàng đặt đơn hàng trên ứng dụng, hệ thống sẽ thực hiện giữ một khoản tiền tương ứng với giá trị dự kiến của đơn hàng đó trong ví. Tuy nhiên, trong quá trình tài xế đi mua hàng, giá trị thực tế có thể thay đổi do hết món hoặc thay đổi topping. Hệ thống phải xử lý bài toán điều chỉnh số tiền đang giữ: nếu giá cuối cùng thấp hơn, phần chênh lệch phải được mở khóa về số dư khả dụng; nếu cao hơn, hệ thống cần kiểm tra xem số dư khả dụng còn lại có đủ để giữ thêm hay không trước khi cho phép tài xế hoàn tất đơn.

### Nền tảng đấu giá trực tuyến và tiền đặt cọc

Để đảm bảo người tham gia đấu giá có trách nhiệm, hệ thống yêu cầu người dùng phải ký gửi một khoản tiền đặt cọc trước khi đưa ra mức giá thầu. Số tiền này sẽ bị chuyển vào trạng thái phong tỏa. Nếu người dùng đó thua cuộc ở phiên đấu giá, số tiền phải được tự động giải tỏa ngay lập tức để họ có thể dùng cho phiên khác. Nếu họ thắng cuộc, khoản tiền đặt cọc này sẽ được chuyển thành khoản thanh toán một phần hoặc toàn bộ cho món hàng, đòi hỏi sự phối hợp chặt chẽ giữa trạng thái phiên đấu giá và trạng thái ví.

### Dịch vụ thuê xe điện thông minh theo phút

Khi người dùng bắt đầu mở khóa một chiếc xe điện, hệ thống sẽ thực hiện phong tỏa một hạn mức tiền tối thiểu trong ví để đảm bảo người dùng có khả năng chi trả. Trong suốt hành trình, cứ mỗi 5 phút, hệ thống lại cập nhật và tính toán lại số tiền cần giữ dựa trên thời gian di chuyển thực tế. Khi kết thúc chuyến đi, hệ thống sẽ thực hiện một giao dịch quyết toán duy nhất: giải tỏa số tiền đang giữ và trừ đi số tiền thực tế phải trả, đảm bảo tính nhất quán của dữ liệu ngay cả khi kết nối mạng của thiết bị di động không ổn định.

### Hệ thống ví quảng cáo trả trước cho doanh nghiệp

Các doanh nghiệp chạy quảng cáo thường nạp một số tiền lớn vào ví, nhưng số tiền này sẽ bị tiêu hao dần dựa trên lượt click hoặc lượt hiển thị. Hệ thống cần cơ chế giữ tiền tạm thời cho các chiến dịch đang chạy để tránh việc doanh nghiệp rút sạch tiền trong khi quảng cáo vẫn đang hiển thị. Bài toán đặt ra là phải xử lý hàng nghìn yêu cầu giữ tiền và quyết toán tiền nhỏ lẻ trong mỗi giây, đồng thời đảm bảo số dư khả dụng luôn phản ánh đúng khả năng thanh toán còn lại của doanh nghiệp để hệ thống phân phối quảng cáo biết khi nào nên dừng.

### Nền tảng Freelancer và bảo vệ dự án theo cột mốc

Trên các trang web tuyển dụng freelancer, dự án thường được chia thành nhiều giai đoạn. Chủ dự án sẽ nạp tiền vào hệ thống và số tiền cho toàn bộ dự án sẽ bị giữ trong tài khoản đảm bảo. Sau khi freelancer hoàn thành mỗi cột mốc và được chủ dự án phê duyệt, một phần tiền từ số dư đang giữ sẽ được chuyển sang ví của freelancer. Bài toán này yêu cầu thiết kế hệ thống có khả năng truy xuất nguồn gốc dòng tiền rất chi tiết để phục vụ việc đối soát và giải quyết tranh chấp giữa hai bên nếu có.

### Hệ thống thanh toán hóa đơn tự động định kỳ

Người dùng có thể đăng ký thanh toán tự động cho các loại hóa đơn như điện, nước, internet. Vào ngày hóa đơn được phát hành, hệ thống sẽ tự động quét và thực hiện lệnh giữ tiền từ ví của người dùng để chờ ngày quyết toán cuối cùng với nhà cung cấp dịch vụ. Điểm phức tạp ở đây là việc xử lý các tình huống ưu tiên: nếu số dư không đủ cho tất cả các hóa đơn, hệ thống cần có logic để quyết định hóa đơn nào được giữ tiền trước, hóa đơn nào sẽ bị thông báo thất bại.

### Ví đa ngoại tệ với tỷ giá biến động

Trong bài toán này, người dùng sở hữu một ví có nhiều loại tiền tệ khác nhau. Khi một giao dịch giữ tiền diễn ra ở loại tiền tệ A nhưng số dư khả dụng của tiền tệ đó không đủ, hệ thống có thể cho phép giữ tiền từ loại tiền tệ B theo tỷ giá quy đổi tại thời điểm đó. Thách thức nằm ở việc khi giải tỏa hoặc quyết toán, nếu tỷ giá thay đổi, hệ thống phải tính toán lại phần chênh lệch để đảm bảo người dùng không bị thiệt và sàn không bị lỗ, đồng thời vẫn giữ đúng bản chất của số tiền đang bị đóng băng.
