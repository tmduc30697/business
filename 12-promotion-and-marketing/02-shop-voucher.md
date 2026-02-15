# Shop voucher

### Phân quyền tạo và quản lý mã giảm giá theo từng người bán

Trong một sàn thương mại điện tử có hàng nghìn nhà bán hàng, mỗi người bán cần có không gian riêng để tự thiết kế các chương trình khuyến mãi của mình. Hệ thống phải đảm bảo rằng người bán A chỉ có thể tạo, chỉnh sửa hoặc xem báo cáo sử dụng của các mã giảm giá thuộc cửa hàng của họ. Các mã này không được phép hiển thị hoặc cho phép áp dụng tại cửa hàng của người bán B. Điều này đòi hỏi cấu trúc dữ liệu phải có sự liên kết chặt chẽ giữa mã giảm giá và định danh của cửa hàng.

### Giới hạn phạm vi áp dụng mã giảm giá cho một số sản phẩm nhất định trong cửa hàng

Người bán muốn tạo mã giảm giá nhưng không áp dụng cho toàn bộ gian hàng mà chỉ áp dụng cho một danh sách sản phẩm cụ thể, ví dụ như các sản phẩm đang tồn kho lâu ngày hoặc các sản phẩm mới ra mắt. Khi khách hàng thanh toán, hệ thống phải kiểm tra xem trong giỏ hàng có sản phẩm nào thuộc danh sách được phép áp dụng mã hay không. Nếu giỏ hàng có cả sản phẩm được giảm giá và sản phẩm không được giảm giá, hệ thống chỉ được tính toán số tiền giảm dựa trên giá trị của các sản phẩm hợp lệ.

### Kiểm soát ngân sách khuyến mãi tối đa của mỗi người bán

Mỗi người bán có một ngân sách nhất định cho chiến dịch marketing. Họ thiết lập một mã giảm giá với tổng số lượt sử dụng tối đa là một con số cụ thể. Bài toán đặt ra là khi có hàng trăm khách hàng cùng lúc nhấn nút đặt hàng và sử dụng mã của cùng một shop, hệ thống phải xử lý tranh chấp để đảm bảo tổng số lượt sử dụng thực tế không bao giờ vượt quá con số mà người bán đã thiết lập, tránh gây thiệt hại về tài chính cho họ.

### Thiết lập giá trị đơn hàng tối thiểu để được áp dụng mã của shop

Để khuyến khích khách hàng mua nhiều sản phẩm hơn trong cùng một đơn hàng, người bán thiết lập điều kiện mã giảm giá chỉ có hiệu lực khi tổng giá trị các sản phẩm của shop đó trong giỏ hàng đạt một ngưỡng nhất định. Ví dụ, khách hàng phải mua ít nhất 500 nghìn đồng tiền hàng của shop A thì mới được giảm 50 nghìn đồng. Hệ thống cần tính toán tổng phụ của từng shop trong giỏ hàng chung trước khi quyết định mã giảm giá đó có hợp lệ hay không.

### Quản lý hiển thị mã giảm giá tại trang chi tiết sản phẩm và trang cửa hàng

Khác với mã toàn sàn thường hiện ở trang chủ, mã của shop cần được hiển thị ngay tại trang sản phẩm hoặc trang cá nhân của shop đó để thu hút khách hàng. Hệ thống cần một cơ chế truy vấn hiệu quả để khi người dùng vào xem một sản phẩm, hệ thống sẽ tự động liệt kê tất cả các mã giảm giá còn hiệu lực, còn lượt sử dụng và phù hợp với sản phẩm đó. Việc này yêu cầu thiết kế database tối ưu cho các câu lệnh tìm kiếm theo cửa hàng và trạng thái mã.

### Xử lý hoàn trả lượt dùng mã khi khách hàng hủy đơn hàng của một shop

Trong một đơn hàng lớn gồm sản phẩm của nhiều shop khác nhau, nếu khách hàng chỉ yêu cầu hủy các sản phẩm thuộc shop A (nơi họ đã áp dụng mã giảm giá của shop), hệ thống phải có quy trình cập nhật lại số lượng mã đã sử dụng của shop đó. Lượt dùng phải được trả về kho để người khác có thể sử dụng, hoặc để chính khách hàng đó sử dụng lại cho đơn hàng sau. Logic này phải tách biệt hoàn toàn với các mã giảm giá của các shop khác hoặc mã giảm giá của toàn sàn trong cùng đơn hàng đó.

### Giới hạn số lượng mã giảm giá tối đa mà một shop được phát hành cùng lúc

Để tránh việc người bán tạo ra quá nhiều mã rác làm loãng hệ thống hoặc gây nhầm lẫn cho khách hàng, sàn giao dịch quy định mỗi shop chỉ được có tối đa một số lượng mã nhất định đang ở trạng thái hoạt động. Khi người bán muốn tạo mã mới nhưng đã đạt giới hạn, hệ thống phải yêu cầu họ kết thúc các chiến dịch cũ. Bài toán này giúp bạn luyện tập cách thiết kế các ràng buộc về số lượng bản ghi dựa trên điều kiện của một thực thể cha là cửa hàng.

### Thống kê và báo cáo hiệu quả sử dụng mã giảm giá cho người bán

Người bán cần biết mã giảm giá nào mang lại doanh thu tốt nhất, có bao nhiêu khách hàng đã sử dụng và tổng số tiền họ đã bỏ ra để giảm giá là bao nhiêu. Hệ thống cần lưu trữ dữ liệu sử dụng mã một cách chi tiết theo từng đơn hàng để có thể tổng hợp báo cáo theo thời gian. Đây là bài toán về thiết kế bảng lịch sử sử dụng và các câu lệnh truy vấn tổng hợp dữ liệu (aggregation) để cung cấp thông tin chi tiết cho dashboard của người bán.
