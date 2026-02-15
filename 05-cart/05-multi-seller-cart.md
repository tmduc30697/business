# Multi-seller cart

### Quản lý trạng thái tồn kho và khóa sản phẩm tạm thời

Khi người dùng thêm sản phẩm từ nhiều seller vào giỏ hàng, một vấn đề lớn phát sinh là số lượng tồn kho có thể thay đổi liên tục trước khi họ bấm nút thanh toán. Bài toán đặt ra là làm thế nào để đồng bộ hóa số lượng tồn kho thực tế của từng seller với giỏ hàng của người dùng. Hệ thống cần cơ chế kiểm tra tồn kho tại thời điểm checkout cho từng item riêng lẻ và xử lý kịch bản một sản phẩm trong giỏ bị hết hàng trong khi các sản phẩm của seller khác vẫn còn. Điều này liên quan đến việc thiết kế bảng Cart Item và tích hợp với bảng Inventory của từng Seller.

### Áp dụng mã giảm giá đa tầng cho đơn hàng tổng và đơn hàng con

Trong mô hình đa người bán, người dùng thường có hai loại mã giảm giá: mã giảm giá của toàn sàn áp dụng cho tổng giá trị đơn hàng và mã giảm giá riêng của từng seller chỉ áp dụng cho sản phẩm của họ. Bài toán yêu cầu thiết kế hệ thống tính toán sao cho khi tách đơn, số tiền giảm giá được phân bổ chính xác. Bạn cần xác định xem mã giảm giá nào được ưu tiên trước, cách lưu trữ thông tin giảm giá vào các đơn hàng con sau khi tách để đảm bảo minh bạch trong việc đối soát tài chính với seller sau này.

### Tính toán phí vận chuyển linh hoạt theo từng nhà bán hàng

Mỗi seller có thể tọa lạc ở các vị trí địa lý khác nhau và sử dụng các đơn vị vận chuyển khác nhau với bảng giá khác nhau. Khi người dùng checkout một giỏ hàng chung, hệ thống phải gọi đồng thời đến nhiều đơn vị vận chuyển hoặc tra cứu bảng phí của từng seller để tính toán phí ship riêng biệt cho từng kiện hàng con. Bài toán này đòi hỏi thiết kế API sao cho có thể tổng hợp phí vận chuyển từ nhiều nguồn và hiển thị rõ ràng cho người dùng trước khi họ xác nhận thanh toán cuối cùng.

### Quy trình thanh toán tập trung và phân bổ dòng tiền

Mặc dù đơn hàng được tách theo từng seller để quản lý, người dùng thường chỉ muốn thực hiện một giao dịch thanh toán duy nhất cho toàn bộ giỏ hàng. Bài toán ở đây là thiết kế luồng thanh toán qua cổng trung gian, sau đó hệ thống phải tự động ghi nhận và phân bổ số tiền đó vào các đơn hàng con tương ứng. Bạn cần giải quyết vấn đề về giao dịch (transaction) trong database để đảm bảo nếu thanh toán tổng thành công thì tất cả đơn hàng con phải được tạo, còn nếu thất bại thì phải rollback toàn bộ trạng thái.

### Quản lý vòng đời đơn hàng và hủy đơn cục bộ

Sau khi thanh toán thành công và đơn hàng được tách, mỗi seller sẽ có quy trình đóng gói và giao hàng riêng. Bài toán thực tế là người dùng có thể muốn hủy đơn của seller A nhưng vẫn muốn nhận hàng từ seller B. Hệ thống cần hỗ trợ việc thay đổi trạng thái đơn hàng độc lập giữa các đơn hàng con mà không làm ảnh hưởng đến tính toàn vẹn của lịch sử giao dịch gốc. Điều này đòi hỏi một thiết kế database có sự liên kết chặt chẽ giữa bảng Order Parent và Order Child.

### Xử lý thông báo và tương tác thời gian thực cho từng seller

Khi một giỏ hàng chung được thanh toán, hệ thống cần gửi thông báo ngay lập tức đến tất cả các seller có sản phẩm trong đơn hàng đó. Bài toán là làm sao để thiết kế hệ thống queue hoặc notification service để gửi thông tin đơn hàng mới đến đúng Dashboard của từng nhà bán hàng mà không xảy ra tình trạng nhầm lẫn dữ liệu. Mỗi seller chỉ được phép xem thông tin khách hàng và danh sách sản phẩm thuộc phạm vi quản lý của mình, đòi hỏi thiết kế phân quyền và truy vấn dữ liệu chính xác.

### Đối soát tài chính và khấu trừ hoa hồng sàn thương mại

Mỗi giao dịch thông qua giỏ hàng đa người bán đều liên quan đến phí dịch vụ của sàn. Sau khi đơn hàng hoàn tất, hệ thống phải tính toán số tiền thực nhận cho từng seller sau khi đã trừ đi phí hoa hồng, phí vận chuyển và các loại thuế liên quan. Bài toán này tập trung vào thiết kế các bảng giao dịch tài chính và ví điện tử của seller, nơi mà mỗi đơn hàng con sau khi tách sẽ tạo ra một dòng tiền tương ứng cần được đối soát định kỳ.

### Quản lý đánh giá và khiếu nại sau khi tách đơn

Người dùng mua nhiều sản phẩm trong một lần checkout nhưng trải nghiệm với mỗi seller có thể khác nhau. Bài toán đặt ra là hệ thống đánh giá (review) và khiếu nại (refund) phải được thiết kế dựa trên các đơn hàng con đã tách. Bạn cần xây dựng logic sao cho người dùng có thể khiếu nại một sản phẩm cụ thể của một seller nhất định mà không ảnh hưởng đến trạng thái hoàn thành của các sản phẩm khác trong cùng một giỏ hàng ban đầu.
