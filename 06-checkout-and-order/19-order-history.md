# Order history

### Lưu trữ sự thay đổi trạng thái và dấu vết thời gian

Trong thực tế, một đơn hàng không chỉ có trạng thái hiện tại mà còn có một hành trình từ lúc chờ xác nhận, đang giao cho đến khi hoàn tất hoặc bị hủy. Bài toán yêu cầu bạn phải thiết kế làm sao để khi người dùng xem lại lịch sử, họ thấy được mốc thời gian chi tiết cho từng bước thay đổi đó. Bạn cần xử lý việc lưu trữ các mốc thời gian này sao cho hiệu quả, cho phép truy xuất nhanh danh sách các sự kiện đã xảy ra với đơn hàng mà không làm chậm hệ thống khi số lượng đơn hàng lên đến hàng triệu.

### Quản lý biến động giá và thông tin sản phẩm tại thời điểm mua

Một lỗi phổ biến khi thiết kế lịch sử đơn hàng là chỉ lưu mã sản phẩm. Nếu một năm sau cửa hàng thay đổi tên sản phẩm hoặc tăng giá, lịch sử đơn hàng cũ sẽ bị hiển thị sai lệch thông tin so với lúc khách mua. Bài toán này yêu cầu bạn thiết kế cấu trúc dữ liệu sao cho thông tin về tên sản phẩm, hình ảnh đại diện, giá bán và các chương trình khuyến mãi được đóng băng ngay tại thời điểm thanh toán. Điều này đảm bảo tính minh bạch và làm bằng chứng đối soát nếu có tranh chấp sau này.

### Phân trang và lọc lịch sử đơn hàng đa tiêu chí

Khi người dùng mua sắm qua nhiều năm, danh sách đơn hàng trở nên rất dài. Hệ thống cần hỗ trợ tìm kiếm và lọc theo nhiều điều kiện như khoảng thời gian mua hàng, trạng thái đơn hàng hoặc tìm kiếm theo tên sản phẩm nằm bên trong đơn hàng đó. Thử thách ở đây là thiết kế API và chỉ mục trong cơ sở dữ liệu để việc tìm kiếm diễn ra tức thì, ngay cả khi người dùng muốn xem lại những đơn hàng từ ba năm trước trong một kho dữ liệu khổng lồ.

### Xử lý hoàn tiền và trả hàng một phần

Thực tế mua sắm thường phát sinh tình huống một đơn hàng có năm sản phẩm nhưng người dùng chỉ muốn trả lại hai sản phẩm do bị lỗi. Bài toán này buộc bạn phải thiết kế hệ thống có khả năng quản lý trạng thái chi tiết đến từng mặt hàng bên trong một đơn hàng lớn. Bạn phải tính toán lại tổng tiền, quản lý số tiền đã hoàn trả và cập nhật lại trạng thái của đơn hàng tổng quát sao cho logic kế toán vẫn chính xác và người dùng dễ dàng theo dõi được phần nào đã nhận, phần nào đã trả.

### Tích hợp hệ thống đánh giá và phản hồi vào lịch sử

Lịch sử đơn hàng thường là nơi người dùng thực hiện đánh giá sản phẩm sau khi nhận hàng. Bài toán yêu cầu bạn thiết kế mối liên kết giữa đơn hàng và hệ thống đánh giá sao cho mỗi sản phẩm trong một đơn hàng chỉ được đánh giá một lần duy nhất. Ngoài ra, hệ thống phải hiển thị được trạng thái trực quan như sản phẩm nào đã đánh giá, sản phẩm nào chưa, và cho phép người dùng sửa đổi đánh giá trong một khoảng thời gian quy định sau khi nhận hàng.

### Quản lý mã giảm giá và điểm thưởng trong lịch sử

Một đơn hàng thực tế thường áp dụng nhiều loại giảm giá khác nhau như mã giảm phí vận chuyển, mã giảm giá của cửa hàng và điểm tích lũy của người dùng. Khi xem lại lịch sử, người dùng cần thấy rõ bảng phân rã chi phí: giá gốc là bao nhiêu, từng loại mã giảm giá đã trừ bao nhiêu tiền và số điểm thưởng họ nhận được từ đơn hàng đó là bao nhiêu. Việc thiết kế database phải tách biệt được các loại chi phí này để phục vụ việc báo cáo tài chính và hoàn tiền sau này.

### Đồng bộ thông tin vận chuyển từ đối tác thứ ba

Dữ liệu về vị trí đơn hàng thường được lấy từ API của các đơn vị vận chuyển bên ngoài. Bài toán đặt ra là làm thế nào để lưu trữ hoặc hiển thị thông tin vận chuyển theo thời gian thực trong trang lịch sử đơn hàng mà không làm phụ thuộc quá nhiều vào hệ thống bên ngoài. Bạn cần cân nhắc giữa việc lưu tạm dữ liệu vận chuyển vào database của mình hay gọi API trực tiếp mỗi khi người dùng xem chi tiết đơn hàng, đồng thời xử lý trường hợp mã vận đơn bị thay đổi.

### Chế độ xem lịch sử đơn hàng cho khách vãng lai

Nhiều trang thương mại điện tử cho phép mua hàng mà không cần đăng ký tài khoản. Bài toán này yêu cầu bạn thiết kế hệ thống truy xuất lịch sử đơn hàng dựa trên các thông tin bảo mật thay thế như địa chỉ email và số điện thoại kết hợp với mã xác thực gửi qua tin nhắn. Bạn phải đảm bảo tính bảo mật để người lạ không thể xem được thông tin cá nhân của khách hàng khác chỉ bằng cách đoán mã đơn hàng, đồng thời vẫn giữ được trải nghiệm thuận tiện cho người dùng.

### Tối ưu hóa hiệu năng bằng cách tách biệt dữ liệu cũ

Các đơn hàng từ nhiều năm trước thường rất ít khi được truy cập nhưng lại chiếm dung lượng lưu trữ rất lớn, làm ảnh hưởng đến tốc độ truy vấn của các đơn hàng mới. Bài toán này yêu cầu bạn thiết kế kiến trúc hệ thống để lưu trữ đơn hàng theo dạng dữ liệu nóng và dữ liệu nguội. Bạn cần tính toán xem khi nào thì nên chuyển đơn hàng vào kho lưu trữ lâu dài và làm thế nào để API vẫn có thể truy xuất đồng nhất khi người dùng yêu cầu xem lại toàn bộ lịch sử từ trước đến nay.

### Tính năng mua lại nhanh từ đơn hàng cũ

Người dùng thường có thói quen mua lại các sản phẩm họ đã từng dùng. Bài toán yêu cầu thiết kế một chức năng trong trang lịch sử cho phép người dùng thêm nhanh tất cả các món đồ từ một đơn hàng cũ vào giỏ hàng hiện tại. Thử thách ở đây là hệ thống phải kiểm tra lại tính khả dụng của sản phẩm ở thời điểm hiện tại: liệu sản phẩm đó còn hàng không, giá có thay đổi không, và có chương trình khuyến mãi nào mới thay thế cho cái cũ hay không trước khi đưa vào giỏ hàng mới.
