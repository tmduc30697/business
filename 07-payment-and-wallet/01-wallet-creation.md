# Wallet creation

### Quản lý số dư đa ví cho người dùng và đối tác

Trong một nền tảng thương mại điện tử, mỗi người dùng có thể sở hữu nhiều loại ví khác nhau cùng một lúc. Ví dụ, một người dùng có ví tiền mặt để nạp tiền từ ngân hàng, ví khuyến mãi chỉ dùng để nhận các mã giảm giá hoặc hoàn tiền, và ví ký quỹ đối với người bán hàng. Bài toán yêu cầu thiết kế cách quản lý để hệ thống phân biệt được số dư khả dụng của từng loại ví, đồng thời đảm bảo khi thanh toán, hệ thống có thể ưu tiên trừ tiền từ ví khuyến mãi trước rồi mới đến ví tiền mặt.

### Xử lý giao dịch đồng thời và cơ chế khóa số dư

Khi một người dùng thực hiện thanh toán cho nhiều đơn hàng cùng một lúc hoặc vừa nạp tiền vừa rút tiền trong cùng một giây, hệ thống rất dễ gặp tình trạng tranh chấp dữ liệu. Bài toán đặt ra là làm thế nào để đảm bảo tính nhất quán của số dư, tránh việc số dư bị trừ âm hoặc cập nhật sai lệch khi có hàng ngàn yêu cầu ghi vào cơ sở dữ liệu cùng lúc. Bạn cần tính đến các trạng thái của giao dịch như đang xử lý, thành công, thất bại và cơ chế tạm giữ tiền để đảm bảo giao dịch diễn ra an toàn.

### Hệ thống đối soát và lịch sử biến động số dư

Bất kỳ một ví điện tử nào cũng cần một bảng ghi lại mọi dấu vết của dòng tiền để phục vụ việc tra soát sau này. Mỗi khi số dư thay đổi, hệ thống phải tạo ra một bản ghi chi tiết bao gồm mã giao dịch, số tiền thay đổi, số dư trước khi đổi, số dư sau khi đổi và mục đích của giao dịch đó. Bài toán này tập trung vào việc thiết kế cấu trúc dữ liệu sao cho việc truy xuất lịch sử giao dịch nhanh chóng nhưng vẫn đảm bảo tính toàn vẹn, không thể chỉnh sửa các bản ghi đã tồn tại trong quá khứ.

### Cơ chế hoàn tiền và xử lý giao dịch đảo ngược

Trong thực tế, khách hàng thường xuyên yêu cầu hủy đơn hàng hoặc trả hàng sau khi đã thanh toán bằng ví nội bộ. Bài toán yêu cầu thiết kế quy trình hoàn tiền sao cho tiền được trả về đúng ví ban đầu mà khách đã dùng để thanh toán. Đặc biệt, nếu giao dịch thanh toán ban đầu được kết hợp từ nhiều ví khác nhau, hệ thống phải biết cách phân bổ lại số tiền hoàn trả vào từng ví theo tỷ lệ tương ứng và đánh dấu mối quan hệ giữa giao dịch hoàn tiền với giao dịch thanh toán gốc.

### Quản lý phí giao dịch và chiết khấu cho người bán

Đối với các sàn giao dịch, mỗi khi người bán thực hiện rút tiền hoặc nhận tiền từ đơn hàng, hệ thống sẽ tự động trích một phần trăm phí dịch vụ. Bài toán này yêu cầu thiết kế logic tính toán phí linh hoạt cho từng loại đối tượng người dùng hoặc từng loại giao dịch khác nhau. Ngoài ra, hệ thống cần tách bạch giữa số tiền thực tế khách trả, số tiền phí sàn thu và số tiền thực nhận của người bán để phục vụ việc báo cáo doanh thu chính xác cho doanh nghiệp.

### Hệ thống hạn mức và rào cản bảo mật giao dịch

Để phòng chống gian lận và rửa tiền, hệ thống ví cần quản lý các hạn mức giao dịch theo ngày hoặc theo tháng cho từng cấp độ tài khoản. Bài toán đặt ra là thiết kế cách lưu trữ các cấu hình hạn mức và kiểm tra điều kiện này mỗi khi người dùng khởi tạo một giao dịch mới. Nếu số tiền vượt quá ngưỡng cho phép hoặc tài khoản đang bị tạm khóa vì nghi ngờ gian lận, hệ thống phải ngăn chặn hành động trừ tiền và phản hồi lỗi chính xác cho phía ứng dụng.

### Luồng tiền trung gian trong mô hình thanh toán hộ

Trong mô hình này, khi người mua thanh toán, tiền không chuyển ngay vào ví người bán mà được giữ bởi một tài khoản trung gian của hệ thống. Chỉ khi người mua xác nhận đã nhận hàng thành công, tiền mới được giải ngân từ tài khoản trung gian sang ví của người bán. Bài toán yêu cầu thiết kế hệ thống có khả năng quản lý các tài khoản hệ thống, theo dõi các khoản tiền đang treo và thực hiện các lệnh chuyển tiền nội bộ giữa các ví mà không cần thông qua cổng thanh toán bên ngoài.

### Chuyển tiền nội bộ giữa các người dùng trong hệ thống

Tính năng này cho phép người dùng chuyển số dư cho nhau bằng cách sử dụng định danh như số điện thoại hoặc email. Bài toán yêu cầu thiết kế một giao dịch kép bao gồm hai hành động xảy ra đồng thời: trừ tiền ở ví người gửi và cộng tiền vào ví người nhận. Bạn cần đảm bảo tính nguyên tử của giao dịch, tức là nếu một trong hai hành động thất bại thì toàn bộ quá trình phải được hủy bỏ để tránh việc tiền bị mất đi hoặc tự động sinh ra trong hệ thống.
