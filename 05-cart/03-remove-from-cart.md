# Remove from cart

### Quản lý giỏ hàng thương mại điện tử đa kho hàng

Trong mô hình này, một đơn hàng có thể chứa các sản phẩm đến từ nhiều kho hoặc nhà cung cấp khác nhau. Khi người dùng xóa một sản phẩm, hệ thống không chỉ đơn giản là trừ tiền mà còn phải tính toán lại phí giao hàng dựa trên các kho còn lại. Nếu việc xóa sản phẩm dẫn đến việc một kho hàng không còn sản phẩm nào trong giỏ, toàn bộ gói đóng gói và phương thức vận chuyển dự kiến cho kho đó cũng phải bị loại bỏ khỏi cấu trúc dữ liệu giỏ hàng.

### Giỏ hàng có áp dụng mã giảm giá theo ngưỡng chi tiêu

Bài toán tập trung vào logic kiểm tra điều kiện của các chương trình khuyến mãi. Khi người dùng xóa sản phẩm khiến tổng giá trị đơn hàng giảm xuống dưới mức tối thiểu để hưởng ưu đãi, hệ thống phải tự động hủy bỏ mã giảm giá đã áp dụng trước đó. Điều này đòi hỏi API phải trả về trạng thái mới của giỏ hàng kèm theo thông báo cụ thể về việc mã giảm giá không còn hiệu lực để người dùng không bị nhầm lẫn về giá trị thanh toán cuối cùng.

### Cập nhật giỏ hàng trong phiên bản đặt đồ ăn trực tuyến

Đối với các ứng dụng đặt món, cấu trúc giỏ hàng thường phức tạp hơn do đi kèm các lựa chọn thêm như topping, mức độ đường đá hoặc ghi chú món ăn. Khi thực hiện xóa một món chính, hệ thống phải đảm bảo tất cả các tùy chọn đi kèm món đó cũng bị xóa sạch khỏi cơ sở dữ liệu tạm thời. Giá trị đơn hàng lúc này phải tính toán lại dựa trên cả đơn giá món chính và tổng tiền của các loại topping đi kèm đã chọn.

### Giỏ hàng nhóm cho mô hình mua chung hoặc đặt hàng tập thể

Hệ thống cho phép nhiều người dùng cùng thêm sản phẩm vào một giỏ hàng chung thông qua một mã phòng. Khi một thành viên xóa sản phẩm do chính họ đã thêm, hệ thống cần cập nhật lại giá trị đơn hàng tức thời cho tất cả các thành viên khác đang quan sát giỏ hàng đó. Thử thách ở đây là việc đồng bộ hóa dữ liệu giữa các phiên làm việc khác nhau và đảm bảo quyền hạn xóa sản phẩm được phân định rõ ràng giữa chủ phòng và thành viên.

### Xóa sản phẩm trong giỏ hàng có ràng buộc combo hoặc bộ quà tặng

Nhiều cửa hàng bán sản phẩm theo dạng bộ hoặc combo để hưởng giá ưu đãi đặc biệt. Nếu người dùng xóa một sản phẩm thành phần nằm trong một combo bắt buộc, hệ thống phải xử lý logic hoặc là xóa toàn bộ combo đó, hoặc chuyển các sản phẩm còn lại về mức giá bán lẻ thông thường. Việc cập nhật giá trị đơn hàng lúc này không chỉ là phép trừ đơn giản mà là một quy trình tính toán lại toàn bộ bảng giá dựa trên các quy tắc nghiệp vụ về gói sản phẩm.

### Quản lý giỏ hàng cho hệ thống bán vé máy bay hoặc dịch vụ theo thời gian

Trong lĩnh vực dịch vụ, việc xóa một hạng mục như hành lý ký gửi hoặc bảo hiểm du lịch khỏi đơn đặt chỗ yêu cầu hệ thống phải kiểm tra lại tính khả dụng của các dịch vụ còn lại. Khi người dùng loại bỏ một dịch vụ, hệ thống cần giải phóng giữ chỗ cho dịch vụ đó trong kho dữ liệu thời gian thực và cập nhật lại tổng tiền bao gồm cả các loại thuế, phí sân bay vốn thay đổi dựa trên tổng số lượng dịch vụ và hành khách hiện có.

### Hệ thống giỏ hàng hỗ trợ đa tiền tệ và tỷ giá hối đoái

Bài toán này đặt ra tình huống giỏ hàng được hiển thị theo tiền tệ địa phương nhưng thanh toán bằng tiền tệ gốc của hệ thống. Khi xóa sản phẩm, việc tính toán lại giá trị đơn tạm tính phải đi kèm với việc làm tròn số thập phân theo quy chuẩn của từng loại tiền tệ và áp dụng tỷ giá tại thời điểm thực hiện thao tác. Hệ thống cần lưu trữ giá trị tại thời điểm thêm vào để khi xóa, con số hoàn lại khớp chính xác với những gì người dùng đã thấy trước đó.

### Giỏ hàng dành cho khách vãng lai và chuyển đổi sang khách hàng đăng ký

Hệ thống cho phép người dùng chưa đăng nhập thêm sản phẩm vào giỏ hàng lưu trữ tại trình duyệt hoặc session. Khi người dùng xóa sản phẩm, hệ thống thực hiện cập nhật trên bộ nhớ tạm. Tuy nhiên, nếu người dùng đăng nhập ngay sau đó, hệ thống phải thực hiện việc hợp nhất giỏ hàng cũ và mới, đồng thời xử lý các thao tác xóa sản phẩm sao cho giá trị đơn hàng cuối cùng phản ánh đúng trạng thái mới nhất trên máy chủ, tránh xung đột dữ liệu giữa máy khách và cơ sở dữ liệu.
