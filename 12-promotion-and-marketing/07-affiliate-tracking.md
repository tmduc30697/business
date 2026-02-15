# Affiliate tracking

### Theo dõi lượt nhấp và ghi nhận chuyển đổi qua Cookie

Đây là bài toán nền tảng nhất của Affiliate. Khi người dùng nhấp vào một đường dẫn tiếp thị của đối tác, hệ thống cần ghi lại các thông tin như mã đối tác, mã chiến dịch, thiết bị sử dụng và thời gian nhấp. Hệ thống sẽ lưu một tệp tin tạm thời trên trình duyệt của người dùng để đánh dấu rằng người này đến từ nguồn nào. Nếu người dùng thực hiện mua hàng trong một khoảng thời gian quy định, ví dụ là ba mươi ngày, hệ thống phải truy vấn lại dữ liệu từ tệp tạm đó để xác định đơn hàng thuộc về đối tác nào và tính toán hoa hồng tương ứng.

### Xử lý hoa hồng theo trạng thái đơn hàng từ sàn thương mại

Trong thực tế, một đơn hàng không bao giờ hoàn thành ngay lập tức. Bài toán yêu cầu hệ thống phải đồng bộ hóa dữ liệu với bên bán hàng để cập nhật trạng thái đơn hàng từ lúc mới đặt, đang giao, đã thanh toán cho đến khi hết thời hạn đổi trả. Hoa hồng ban đầu sẽ ở trạng thái chờ duyệt và chỉ được chuyển sang trạng thái sẵn sàng rút tiền khi đơn hàng được xác nhận thành công. Ngoài ra, hệ thống cần có cơ chế xử lý việc hủy đơn hoặc hoàn hàng để trừ lại số tiền hoa hồng đã ghi nhận tạm thời trước đó.

### Mô hình hoa hồng đa tầng cho hệ thống cộng tác viên

Nhiều hệ thống hiện nay không chỉ trả hoa hồng cho người giới thiệu trực tiếp mà còn trả cho người cấp trên của họ. Bài toán này yêu cầu thiết kế cấu trúc cây để quản lý mối quan hệ giữa các đối tác. Khi một đơn hàng phát sinh từ đối tác cấp dưới, hệ thống cần tự động tính toán tỷ lệ chia sẻ hoa hồng cho nhiều cấp bậc khác nhau theo quy tắc đã định sẵn. Việc này đòi hỏi khả năng truy vấn ngược danh sách người bảo trợ và đảm bảo tổng tỷ lệ hoa hồng chi trả không vượt quá lợi nhuận của sản phẩm.

### Chiến dịch khuyến mãi và mã giảm giá định danh

Thay vì dùng đường dẫn dài, nhiều đối tác ưu tiên sử dụng mã giảm giá riêng để quảng bá. Bài toán đặt ra là mỗi đối tác sẽ được cấp một hoặc nhiều mã giảm giá độc quyền. Khi khách hàng nhập mã này tại bước thanh toán, hệ thống phải tự động nhận diện mã đó thuộc về đối tác nào để ghi nhận hoa hồng, ngay cả khi khách hàng không nhấp vào đường dẫn giới thiệu trước đó. Điều này đòi hỏi sự liên kết chặt chẽ giữa bảng dữ liệu mã giảm giá và bảng dữ liệu đối tác trong hệ thống.

### Đối soát và thanh toán định kỳ cho đối tác

Hệ thống cần một quy trình để tổng hợp toàn bộ hoa hồng đã được phê duyệt của đối tác vào cuối tháng hoặc khi đạt một ngưỡng tiền tối thiểu. Bài toán bao gồm việc gom nhóm các đơn hàng thành công, tính toán các khoản thuế thu nhập cá nhân hoặc phí chuyển khoản nếu có, và tạo ra các yêu cầu thanh toán. Sau khi quản trị viên xác nhận đã chuyển khoản thực tế, hệ thống phải cập nhật lịch sử thanh toán để đối tác có thể theo dõi sự minh bạch của dòng tiền.

### Phân tích hiệu quả chuyển đổi theo nguồn lưu lượng

Để giúp đối tác tối ưu hóa cách làm việc, hệ thống cần cung cấp các báo cáo chi tiết về hiệu suất. Bài toán yêu cầu thống kê số lượng lượt nhấp, số lượng đơn hàng và tỷ lệ chuyển đổi dựa trên từng nguồn khác nhau như mạng xã hội, trang blog hoặc email marketing. Bạn cần thiết kế cách lưu trữ dữ liệu sao cho có thể truy xuất báo cáo theo thời gian thực hoặc theo các khoảng thời gian tùy chỉnh, đồng thời phân loại được lưu lượng truy cập đến từ các vùng địa lý hoặc loại thiết bị khác nhau.

### Ngăn chặn gian lận nhấp chuột và đơn hàng ảo

Đây là vấn đề nhức nhối trong Affiliate khi đối tác tìm cách tự tạo đơn hàng hoặc dùng công cụ để tạo lượt nhấp giả nhằm chiếm đoạt hoa hồng. Bài toán yêu cầu hệ thống ghi lại địa chỉ mạng và định danh thiết bị của cả người giới thiệu lẫn người mua. Nếu phát hiện nhiều đơn hàng từ một địa chỉ mạng hoặc một thiết bị trong thời gian ngắn, hệ thống phải đưa các đơn hàng này vào danh sách nghi vấn để kiểm tra thủ công hoặc tự động từ chối tính hoa hồng để bảo vệ ngân sách của nhà bán hàng.

### Quản lý chính sách hoa hồng linh hoạt theo danh mục sản phẩm

Không phải sản phẩm nào cũng có mức hoa hồng giống nhau. Bài toán yêu cầu thiết kế một hệ thống luật cho phép quản trị viên thiết lập hoa hồng khác nhau dựa trên danh mục hàng hóa, giá trị đơn hàng hoặc cấp độ của đối tác. Ví dụ, hàng điện tử có hoa hồng thấp hơn hàng thời trang, hoặc đối tác kim cương sẽ nhận mức chiết khấu cao hơn đối tác mới tham gia. Hệ thống phải đảm bảo khi một đơn hàng có nhiều loại sản phẩm khác nhau, việc tính toán hoa hồng cho từng sản phẩm vẫn diễn ra chính xác.
