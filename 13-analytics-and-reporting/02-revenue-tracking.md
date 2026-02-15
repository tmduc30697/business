# Revenue tracking

### Tính toán doanh thu thực sau khi áp dụng nhiều loại chiết khấu

Một đơn hàng có thể áp dụng cùng lúc mã giảm giá của sàn thương mại điện tử, mã giảm giá của riêng cửa hàng và chương trình giảm giá trực tiếp trên sản phẩm. Hệ thống cần ghi nhận rõ ràng số tiền khách hàng thực trả và phân tách xem ngân sách giảm giá đó được trừ vào phần thu của sàn hay phần thu của cửa hàng. Bài toán này yêu cầu thiết kế database có khả năng bóc tách từng loại dòng tiền để cuối tháng có thể đối soát chính xác số tiền thực tế thu về sau khi đã trừ hết các lớp ưu đãi.

### Xử lý hoàn tiền từng phần cho đơn hàng có nhiều sản phẩm

Khách hàng mua một đơn hàng gồm năm sản phẩm khác nhau và sử dụng một mã giảm giá tổng cho toàn đơn. Sau khi nhận hàng, khách hàng chỉ muốn trả lại hai sản phẩm do bị lỗi. Hệ thống phải tính toán lại số tiền cần hoàn trả cho khách dựa trên giá trị của hai sản phẩm đó sau khi đã phân bổ tỷ lệ giảm giá ban đầu. Đồng thời, doanh thu thực tế của hệ thống phải được cập nhật giảm xuống tương ứng, đảm bảo tính nhất quán giữa bảng đơn hàng và bảng lịch sử giao dịch tài chính.

### Đối soát phí thanh toán của các bên trung gian

Mỗi khi khách hàng thanh toán qua thẻ tín dụng hoặc ví điện tử, đơn vị cung cấp dịch vụ thanh toán sẽ thu một khoản phí phần trăm nhất định trên tổng giá trị giao dịch. Doanh thu đổ về tài khoản của nền tảng không phải là con số khách hàng bấm thanh toán mà là con số sau khi đã trừ phí cổng thanh toán. Hệ thống cần thiết kế các bảng ghi nhận phí dịch vụ này cho từng giao dịch để tính toán ra số tiền thực nhận cuối cùng (Net Cash Flow) và phục vụ việc kiểm tra chênh lệch với sao kê ngân hàng.

### Quản lý doanh thu tạm tính và doanh thu thực tế theo trạng thái giao hàng

Trong mô hình giao hàng thu tiền hộ (COD), khi đơn hàng được tạo, doanh thu chỉ ở mức tạm tính trên hệ thống. Chỉ khi đơn vị vận chuyển xác nhận đã thu tiền thành công và đối soát xong với nền tảng, số tiền đó mới được coi là doanh thu thực tế. Nếu đơn hàng bị chuyển hoàn, toàn bộ doanh thu tạm tính phải bị hủy bỏ. Bài toán này đòi hỏi hệ thống quản lý dòng tiền phải đồng bộ chặt chẽ với trạng thái vận đơn và có cơ chế xử lý các giao dịch đang treo.

### Ghi nhận điều chỉnh doanh thu do lỗi vận hành hoặc khiếu nại

Đôi khi đơn hàng đã hoàn tất và tiền đã về túi, nhưng sau đó phát sinh khiếu nại dẫn đến việc nền tảng phải đền bù cho khách hàng một khoản tiền nhất định mà không thu hồi lại sản phẩm. Khoản đền bù này cần được ghi nhận như một khoản điều chỉnh giảm doanh thu cho đơn hàng đó. Hệ thống cần một bảng ghi nhận các bút toán điều chỉnh tài chính phát sinh sau khi đơn hàng đã đóng để đảm bảo báo cáo doanh thu cuối tháng phản ánh đúng số tiền còn lại sau mọi biến số.

### Phân bổ doanh thu theo thời gian sử dụng dịch vụ trả trước

Đối với các nền tảng bán gói thành viên hoặc phần mềm theo đăng ký (SaaS), khách hàng có thể trả trước một khoản tiền cho một năm sử dụng. Tuy nhiên, về mặt kế toán, doanh thu này không được tính hết vào một ngày mà phải phân bổ đều cho từng tháng. Nếu khách hàng hủy gói ở tháng thứ ba và yêu cầu trả lại tiền cho chín tháng còn lại, hệ thống phải tự động tính toán được phần doanh thu đã thực hiện và phần doanh thu phải hoàn trả để cập nhật vào báo cáo tài chính hàng tháng.

### Theo dõi doanh thu từ các đối tác liên kết và hoa hồng

Nền tảng hoạt động theo mô hình trung gian, nơi doanh thu thực sự của nền tảng chỉ là phần phí hoa hồng thu từ người bán. Ví dụ, khách hàng trả một trăm đơn vị tiền, nhưng nền tảng chỉ giữ lại mười đơn vị làm phí dịch vụ và phải chuyển chín mươi đơn vị còn lại cho nhà cung cấp. Database cần thiết kế sao cho theo dõi được tổng dòng tiền luân chuyển qua hệ thống nhưng vẫn tách biệt được đâu là doanh thu thực của công ty và đâu là khoản nợ phải trả cho đối tác.

### Xử lý chênh lệch tỷ giá và phí chuyển đổi ngoại tệ

Nếu nền tảng kinh doanh đa quốc gia, khách hàng thanh toán bằng nhiều loại tiền tệ khác nhau nhưng báo cáo doanh thu tổng phải quy về một loại tiền tệ duy nhất. Do tỷ giá hối đoái thay đổi theo từng giờ, hệ thống cần lưu lại tỷ giá tại thời điểm giao dịch phát sinh. Khi có phát sinh hoàn tiền vào một thời điểm khác với tỷ giá khác, hệ thống phải xử lý phần chênh lệch này sao cho tổng doanh thu thực tế không bị sai lệch bởi các biến động tiền tệ khách quan.
