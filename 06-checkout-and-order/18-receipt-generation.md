# Receipt generation

### Biên nhận bán lẻ tại siêu thị mini

Hệ thống cần ghi lại việc mua hàng của khách tại quầy thu ngân. Mỗi biên nhận bao gồm danh sách các mặt hàng, đơn giá tại thời điểm mua, số lượng và tổng tiền. Bài toán yêu cầu xử lý việc thay đổi giá sản phẩm theo thời gian mà không làm ảnh hưởng đến các biên nhận cũ đã xuất. Ngoài ra, cần lưu thông tin về nhân viên thu ngân thực hiện giao dịch và mã máy tính tiền để phục vụ việc đối soát cuối ngày.

### Biên nhận thanh toán hóa đơn điện nước trực tuyến

Đây là dạng biên nhận cho các dịch vụ tiện ích hàng tháng. Nội dung biên nhận không chỉ có số tiền mà còn phải thể hiện chỉ số đầu kỳ, chỉ số cuối kỳ, đơn giá theo từng bậc thang sử dụng và các loại thuế phí đi kèm. Hệ thống cần lưu trữ mã khách hàng từ một hệ thống định danh riêng biệt và trạng thái xác nhận từ cổng thanh toán trung gian để đảm bảo biên nhận chỉ được xuất khi tiền đã thực sự vào tài khoản công ty.

### Biên nhận đặt phòng khách sạn và dịch vụ lưu trú

Biên nhận này phức tạp hơn vì bao gồm thời gian nhận phòng và trả phòng, số lượng người lớn, trẻ em và các phụ phí phát sinh như tiền phòng, tiền ăn uống hoặc giặt ủi. Hệ thống phải quản lý được các khoản đặt cọc trước đó và trừ đi vào tổng hóa đơn cuối cùng. Việc thiết kế cần tính đến trường hợp khách hàng thanh toán bằng nhiều hình thức khác nhau như tiền mặt kết hợp với thẻ tín dụng cho cùng một biên nhận.

### Biên nhận phí cầu đường điện tử không dừng

Trong kịch bản này, biên nhận được tạo ra tự động khi xe đi qua trạm thu phí. Dữ liệu đầu vào bao gồm biển số xe, loại phương tiện, mã thẻ định danh phương tiện và vị trí trạm thu phí. Thách thức ở đây là tốc độ ghi nhận dữ liệu và khả năng truy xuất biên nhận theo thời gian thực để gửi thông báo về ứng dụng điện thoại cho chủ xe ngay lập tức sau khi giao dịch thành công.

### Biên nhận đăng ký khóa học và tài liệu đào tạo

Bài toán tập trung vào việc thanh toán cho các gói khóa học trực tuyến. Biên nhận cần thể hiện rõ tên khóa học, thời hạn truy cập và các mã giảm giá đã áp dụng. Nếu người dùng mua một combo nhiều khóa học, hệ thống phải phân bổ số tiền giảm giá cho từng mục để thuận tiện cho việc hoàn tiền sau này nếu khách hàng yêu cầu hủy một phần đơn hàng.

### Biên nhận thanh toán dịch vụ Grab hoặc Taxi công nghệ

Biên nhận này cần lưu trữ tọa độ điểm đi, điểm đến, quãng đường di chuyển thực tế và thời gian bắt đầu cũng như kết thúc chuyến xe. Ngoài cước phí chính, biên nhận còn phải bóc tách các loại phí nền tảng, phí cầu đường và tiền tip cho tài xế. Đối với thiết kế API, bạn cần chú ý đến việc tích hợp thông tin tài xế và phương tiện vào bản ghi thanh toán để gửi về email cho người dùng.

### Biên nhận nạp tiền vào ví điện tử hoặc tài khoản game

Đây là dạng biên nhận cho các giao dịch tài chính thuần túy. Thông tin quan trọng nhất là mã tham chiếu giao dịch từ ngân hàng, phương thức nạp và số dư tài khoản trước và sau khi thực hiện giao dịch. Bài toán này đòi hỏi tính toàn vẹn dữ liệu cực cao để đảm bảo rằng biên nhận được xuất ra luôn khớp với biến động số dư trong cơ sở dữ liệu hệ thống lõi.

### Biên nhận phí quản lý và gửi xe tại chung cư

Biên nhận này được xuất định kỳ cho cư dân, bao gồm nhiều loại phí khác nhau như phí quản lý diện tích căn hộ, phí gửi xe máy, phí gửi ô tô và tiền điện nước khu vực chung. Hệ thống cần quản lý danh sách căn hộ và chủ sở hữu, cho phép gộp nhiều loại phí vào một biên nhận duy nhất hoặc tách rời tùy theo nhu cầu thanh toán của cư dân tại thời điểm đó.

### Biên nhận mua hàng trả góp qua công ty tài chính

Biên nhận này không chỉ xác nhận việc thanh toán một số tiền mà còn phải thể hiện số kỳ đã thanh toán trên tổng số kỳ quy định. Dữ liệu cần lưu trữ bao gồm số tiền gốc, tiền lãi của kỳ hiện tại và dư nợ còn lại sau giao dịch. Đây là bài toán tốt để thiết kế database cho các lịch trình thanh toán dài hạn và đối soát công nợ.

### Biên nhận xuất kho và thanh toán cho đại lý phân phối

Trong mô hình doanh nghiệp với doanh nghiệp, biên nhận thanh toán thường đi kèm với thông tin chiết khấu thương mại dựa trên doanh số. Biên nhận cần thể hiện đơn giá niêm yết, tỷ lệ chiết khấu, giá trị chiết khấu và số tiền thực thu. Ngoài ra, cần lưu thông tin về hợp đồng kinh tế liên quan để phục vụ việc kiểm toán và đối chiếu giữa hai bên công ty.
