# Refund to bank

### Hoàn tiền một phần cho đơn hàng có nhiều sản phẩm

Khách hàng đặt mua một đơn hàng gồm năm món đồ khác nhau và thanh toán tổng giá trị qua thẻ tín dụng. Sau khi nhận hàng, khách hàng phát hiện hai món đồ bị lỗi và yêu cầu trả hàng hoàn tiền cho riêng hai món đó. Hệ thống cần tính toán số tiền chính xác cần hoàn lại dựa trên giá trị của từng sản phẩm tại thời điểm mua, bao gồm cả việc phân bổ lại các mã giảm giá hoặc phí vận chuyển đã áp dụng cho toàn bộ đơn hàng. Việc hoàn tiền này phải được ghi nhận sao cho trạng thái của đơn hàng gốc chuyển sang dạng hoàn tiền một phần và không cho phép hoàn tiền quá tổng giá trị đã thanh toán.

### Xử lý hoàn tiền cho giao dịch thanh toán bằng nhiều nguồn tiền

Một nền tảng thương mại điện tử cho phép người dùng thanh toán kết hợp giữa số dư ví điện tử và thẻ ngân hàng cho cùng một giao dịch. Khi phát sinh yêu cầu hoàn tiền toàn phần, hệ thống phải có quy tắc ưu tiên hoàn trả tiền về đâu trước. Thông thường, số dư ví sẽ được hoàn lại ngay lập tức, trong khi phần tiền từ thẻ ngân hàng phải được gửi yêu cầu sang cổng thanh toán quốc tế. Bài toán yêu cầu theo dõi lộ trình của từng dòng tiền để đảm bảo người dùng nhận lại đúng và đủ số tiền từ các nguồn ban đầu họ đã chi trả.

### Đối soát trạng thái hoàn tiền từ cổng thanh toán bên thứ ba

Khi hệ thống gửi yêu cầu hoàn tiền sang ngân hàng hoặc cổng thanh toán, giao dịch không được thực hiện ngay lập tức mà thường rơi vào trạng thái chờ xử lý. Ngân hàng có thể mất từ ba đến bảy ngày làm việc để ghi có vào tài khoản khách hàng. Hệ thống cần một cơ chế để định kỳ kiểm tra trạng thái hoặc tiếp nhận phản hồi thông báo từ phía ngân hàng để cập nhật trạng thái cuối cùng cho người dùng. Thách thức ở đây là xử lý các trường hợp yêu cầu hoàn tiền bị ngân hàng từ chối do thẻ hết hạn hoặc tài khoản bị khóa sau khi đã thanh toán thành công.

### Quản lý hạn mức và số dư khả dụng của tài khoản doanh nghiệp

Để có thể hoàn tiền cho khách hàng, tài khoản thanh toán của doanh nghiệp tại cổng thanh toán phải có đủ số dư. Trong trường hợp doanh nghiệp đã rút hết tiền doanh thu về tài khoản trung tâm, các yêu cầu hoàn tiền mới sẽ bị treo ở trạng thái chờ vốn. Hệ thống cần thiết kế luồng ưu tiên hoặc thông báo cho bộ phận kế toán nạp tiền vào quỹ hoàn tiền, đồng thời phải đảm bảo việc giữ chỗ số tiền này trong hệ thống để không xảy ra tình trạng hoàn tiền vượt quá khả năng chi trả thực tế tại thời điểm đó.

### Xử lý hoàn tiền khi khách hàng thay đổi thẻ hoặc ngân hàng

Khách hàng thực hiện thanh toán bằng một thẻ ghi nợ, nhưng trước khi yêu cầu hoàn tiền được thực hiện, thẻ đó đã bị mất hoặc hết hạn và khách hàng đã đóng tài khoản ngân hàng đó. Lúc này, giao dịch hoàn tiền tự động về nguồn cũ sẽ thất bại. Hệ thống cần một quy trình cho phép nhân viên chăm sóc khách hàng can thiệp để thay đổi thông tin nhận tiền sang một tài khoản ngân hàng khác của khách hàng, đồng thời vẫn phải lưu vết liên kết với giao dịch thanh toán gốc để phục vụ mục đích kiểm toán và chống gian lận.

### Tự động xử lý hoàn tiền hàng loạt do sự cố hủy dịch vụ

Một hãng hàng không hoặc đơn vị tổ chức sự kiện buộc phải hủy bỏ một chuyến bay hoặc một buổi hòa nhạc do điều kiện bất khả kháng. Hệ thống phải xử lý hoàn tiền đồng loạt cho hàng nghìn khách hàng đã thanh toán trước đó. Bài toán này đòi hỏi khả năng xử lý giao dịch song song cực lớn để không làm nghẽn hệ thống, đồng thời phải đảm bảo tính toàn vẹn dữ liệu, tránh việc một giao dịch bị hoàn tiền hai lần hoặc bị bỏ sót trong quá trình quét dữ liệu quy mô lớn.

### Khấu trừ phí dịch vụ và phí giao dịch khi hoàn tiền

Trong một số mô hình kinh doanh, khi khách hàng yêu cầu hoàn tiền vì lý do cá nhân, đơn vị bán hàng sẽ không hoàn lại 100% số tiền mà khấu trừ một khoản phí quản lý hoặc phí giao dịch mà ngân hàng đã thu. Hệ thống cần lưu trữ cấu hình các loại phí này theo từng loại hình dịch vụ hoặc theo thời điểm yêu cầu hoàn tiền. Việc ghi nhận kế toán phải tách bạch rõ ràng giữa số tiền khách đã trả, số tiền thực tế hoàn về ngân hàng, và số tiền doanh nghiệp giữ lại làm doanh thu phí.

### Theo dõi lịch sử và khiếu nại liên quan đến hoàn tiền

Khách hàng thường xuyên thắc mắc về việc họ chưa nhận được tiền mặc dù hệ thống báo đã hoàn thành. Hệ thống cần lưu trữ mã tham chiếu giao dịch từ phía ngân hàng cung cấp để cung cấp cho khách hàng làm bằng chứng làm việc với ngân hàng của họ. Đồng thời, hệ thống cần thiết kế các bảng ghi nhật ký chi tiết từng bước thay đổi trạng thái, từ lúc khách gửi yêu cầu, kế toán phê duyệt, cổng thanh toán tiếp nhận, cho đến khi có xác nhận thành công từ hệ thống liên ngân hàng.
