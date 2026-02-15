# Cashback credit

### Quản lý các chiến dịch hoàn tiền đa điều kiện

Hệ thống cần lưu trữ và vận hành nhiều chương trình khuyến mãi cùng lúc với các quy tắc khác nhau. Một chiến dịch có thể áp dụng hoàn tiền theo phần trăm giá trị đơn hàng hoặc một số tiền cố định, kèm theo đó là các điều kiện về thời gian bắt đầu, thời gian kết thúc và ngân sách tối đa cho toàn bộ chiến dịch. Bài toán yêu cầu thiết kế cách lưu trữ cấu hình chiến dịch sao cho khi người dùng thanh toán, hệ thống có thể nhanh chóng xác định giao dịch đó thuộc diện ưu đãi nào.

### Phân loại hoàn tiền theo danh mục hàng hóa và đối tác

Không phải mọi mặt hàng đều có mức hoàn tiền giống nhau. Một sàn thương mại điện tử muốn áp dụng mức hoàn tiền 5% cho ngành hàng điện tử nhưng lại là 10% cho ngành hàng thời trang. Ngoài ra, mức hoàn tiền còn phụ thuộc vào việc người dùng mua hàng từ đối tác chiến lược hay người bán thông thường. Bạn cần giải quyết cách tổ chức dữ liệu để truy xuất nhanh chóng mối quan hệ giữa sản phẩm, người bán và tỷ lệ hoàn tiền tương ứng.

### Kiểm soát hạn mức hoàn tiền cá nhân và toàn hệ thống

Để tránh rủi ro thâm hụt ngân sách, mỗi chương trình thường có giới hạn số tiền tối đa một người dùng được nhận trong ngày hoặc trong suốt cả chiến dịch. Đồng thời, hệ thống cũng cần theo dõi tổng số tiền đã chi trả trên quy mô toàn sàn để tự động dừng chương trình khi chạm ngưỡng ngân sách cho phép. Bài toán này tập trung vào việc cập nhật số dư và kiểm tra điều kiện trong môi trường có lưu lượng giao dịch cao.

### Xử lý hoàn tiền theo cấp độ thành viên

Nhiều hệ thống sử dụng chính sách hoàn tiền để giữ chân khách hàng thân thiết. Người dùng hạng Đồng nhận được mức hoàn tiền cơ bản, trong khi hạng Vàng hoặc Kim cương nhận được tỷ lệ cao hơn cho cùng một loại giao dịch. Hệ thống cần có cơ chế liên kết giữa tài khoản người dùng, thứ hạng hiện tại và bảng biểu phí hoàn tiền để đảm bảo tính toán chính xác số dư cộng vào ví tại thời điểm giao dịch hoàn tất.

### Quy trình phê duyệt và trạng thái tiền treo

Tiền hoàn lại thường không khả dụng ngay lập tức để tránh gian lận. Khi giao dịch thành công, số tiền hoàn sẽ rơi vào trạng thái chờ xử lý. Sau một khoảng thời gian nhất định hoặc sau khi đơn hàng được xác nhận không có khiếu nại hay đổi trả, trạng thái này mới chuyển sang đã xác nhận và tiền mới thực sự được cộng vào số dư khả dụng của ví. Bài toán yêu cầu thiết kế quy trình chuyển đổi trạng thái giao dịch và cơ chế đối soát dữ liệu.

### Xử lý thu hồi tiền hoàn khi hủy đơn hoặc đổi trả

Đây là vấn đề nhức nhối trong thực tế khi khách hàng thực hiện giao dịch để nhận cashback sau đó yêu cầu hoàn tiền đơn hàng. Hệ thống phải có cơ chế kiểm tra xem giao dịch bị hủy đã được hoàn tiền vào ví hay chưa. Nếu tiền vẫn ở trạng thái chờ, hệ thống phải hủy lệnh hoàn tiền đó. Nếu tiền đã vào ví và người dùng đã tiêu hết, hệ thống cần xử lý ghi nợ hoặc trừ vào lần hoàn tiền tiếp theo để đảm bảo không thất thoát tài chính.

### Hệ thống ghi chép lịch sử biến động số dư và đối soát

Mọi hoạt động cộng tiền từ chương trình khuyến mãi, trừ tiền khi mua sắm bằng cashback hoặc thu hồi tiền đều phải được ghi lại dưới dạng nhật ký giao dịch chi tiết. Mỗi bản ghi cần lưu lại mã giao dịch gốc, mã chiến dịch, số tiền biến động và thời điểm thực hiện. Điều này phục vụ cho việc khách hàng tự tra cứu lịch sử và giúp bộ phận vận hành có thể đối soát thủ công khi có tranh chấp hoặc sai lệch dữ liệu.

### Tích lũy hoàn tiền theo mô hình đa tầng hoặc giới thiệu bạn bè

Hệ thống mở rộng cho phép người dùng nhận được một phần tiền hoàn lại từ các giao dịch của những người mà họ đã giới thiệu. Điều này tạo ra một cấu trúc dạng cây hoặc mạng lưới liên kết. Khi một người mua hàng thành công, hệ thống không chỉ tính toán tiền hoàn cho người đó mà còn phải truy vấn ngược lên các cấp trên để phân bổ hoa hồng hoặc tiền thưởng theo tỷ lệ quy định của chương trình giới thiệu.
