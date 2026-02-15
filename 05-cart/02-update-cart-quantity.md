# Update cart quantity

### Cập nhật số lượng và kiểm tra tồn kho tức thời

Khi người dùng thay đổi số lượng của một sản phẩm trong giỏ hàng, hệ thống cần truy vấn trực tiếp vào bảng tồn kho để xác nhận số lượng yêu cầu còn đủ hay không. Nếu số lượng trong kho nhỏ hơn số lượng yêu cầu, hệ thống sẽ tự động điều chỉnh về mức tối đa có thể cung cấp và thông báo cho người dùng. Sau khi xác nhận tồn kho, hệ thống tính toán lại giá trị đơn hàng dựa trên đơn giá hiện hành và các chính sách giảm giá đang áp dụng cho sản phẩm đó.

### Xử lý tranh chấp tồn kho khi có nhiều người cùng mua

Trong các sự kiện giảm giá lớn, nhiều người dùng có thể cùng thêm một sản phẩm vào giỏ hàng với số lượng lớn. Bài toán yêu cầu thiết kế cơ chế khóa tạm thời hoặc kiểm tra tồn kho tại thời điểm người dùng nhấn cập nhật để tránh tình trạng bán quá số lượng thực tế. Hệ thống phải đảm bảo rằng tổng số lượng sản phẩm trong giỏ hàng của tất cả người dùng đang hoạt động không vượt quá ngưỡng an toàn của kho hàng vật lý, đồng thời cập nhật lại thành tiền ngay lập tức để người dùng chuẩn bị thanh toán.

### Cập nhật giỏ hàng với sản phẩm có nhiều biến thể

Đối với các mặt hàng thời trang, một sản phẩm có thể có nhiều thuộc tính như kích cỡ và màu sắc. Khi người dùng thay đổi số lượng của một biến thể cụ thể, hệ thống phải xác định đúng mã định danh của biến thể đó trong cơ sở dữ liệu để kiểm tra tồn kho riêng biệt. Việc cập nhật số lượng cho một biến thể không được làm ảnh hưởng đến số lượng của các biến thể khác cùng loại trong giỏ hàng, và tổng tiền của toàn bộ giỏ hàng phải được tính toán dựa trên giá của từng biến thể cụ thể.

### Áp dụng chính sách giá theo số lượng mua

Một số cửa hàng bán sỉ áp dụng quy tắc giá giảm dần khi số lượng sản phẩm tăng lên. Khi người dùng cập nhật số lượng trong giỏ hàng vượt qua các mốc quy định, hệ thống phải tự động thay đổi đơn giá của sản phẩm đó trong giỏ hàng sang mức giá ưu đãi tương ứng. Điều này đòi hỏi logic tính toán tổng tiền phải linh hoạt để nhận diện được các ngưỡng số lượng và áp dụng đúng bảng giá bậc thang đã được thiết lập trong hệ thống quản lý khuyến mãi.

### Đồng bộ giỏ hàng giữa khách vãng lai và thành viên

Người dùng có thể thay đổi số lượng sản phẩm khi chưa đăng nhập, dữ liệu lúc này thường được lưu trữ tại trình duyệt hoặc bộ nhớ tạm. Khi người dùng tiến hành đăng nhập, hệ thống cần có cơ chế hợp nhất dữ liệu từ giỏ hàng tạm thời vào giỏ hàng chính thức trong cơ sở dữ liệu. Trong quá trình hợp nhất và cập nhật số lượng, hệ thống phải kiểm tra lại toàn bộ tồn kho một lần nữa vì dữ liệu tạm thời có thể đã lỗi thời, sau đó mới cập nhật lại tổng giá trị đơn hàng cuối cùng.

### Giới hạn số lượng mua tối thiểu và tối đa

Hệ thống cần thiết lập các quy tắc ràng buộc về số lượng cho từng loại sản phẩm cụ thể, ví dụ như chỉ được mua tối đa 2 sản phẩm đối với hàng hiếm hoặc tối thiểu 10 sản phẩm đối với hàng bán sỉ. Khi người dùng nhập số lượng vào ô cập nhật, hệ thống sẽ đối chiếu với các cấu hình này trong database. Nếu số lượng nằm ngoài khoảng cho phép, hệ thống sẽ từ chối cập nhật, hiển thị lỗi và giữ nguyên trạng thái trước đó của giỏ hàng kèm theo thông tin chi tiết về quy định mua sắm.

### Tự động tính toán phí vận chuyển dựa trên số lượng

Việc thay đổi số lượng sản phẩm thường dẫn đến thay đổi trọng lượng và kích thước tổng thể của kiện hàng. Khi người dùng cập nhật số lượng, hệ thống không chỉ tính lại tiền hàng mà còn phải gọi sang dịch vụ vận chuyển hoặc dựa trên cấu hình kho bãi để tính lại phí giao hàng dự kiến. Nếu số lượng tăng làm thay đổi loại phương tiện vận chuyển hoặc vượt quá tải trọng của một đơn hàng thông thường, hệ thống cần thông báo cho người dùng về sự thay đổi của chi phí vận tải này.

### Xử lý giỏ hàng khi sản phẩm hết hàng hoặc ngừng kinh doanh

Trong trường hợp người dùng để sản phẩm trong giỏ hàng một thời gian dài rồi mới quay lại cập nhật số lượng, sản phẩm đó có thể đã bị quản trị viên gỡ bỏ hoặc chuyển trạng thái ngừng kinh doanh. Khi có yêu cầu cập nhật, hệ thống phải kiểm tra trạng thái hoạt động của sản phẩm. Nếu sản phẩm không còn khả dụng, hệ thống sẽ loại bỏ sản phẩm khỏi giỏ hàng hoặc đánh dấu trạng thái không thể thanh toán và trừ giá trị của sản phẩm đó ra khỏi tổng tiền của giỏ hàng.

### Cập nhật giỏ hàng kèm theo quà tặng đi kèm

Nhiều chương trình khuyến mãi quy định nếu mua một số lượng sản phẩm nhất định sẽ được tặng kèm một sản phẩm khác. Khi người dùng cập nhật số lượng đạt đến ngưỡng khuyến mãi, hệ thống phải tự động thêm sản phẩm quà tặng vào giỏ hàng với giá không đồng. Ngược lại, nếu người dùng giảm số lượng xuống dưới ngưỡng, hệ thống phải tự động gỡ bỏ quà tặng đó và cập nhật lại tổng tiền cũng như danh sách vật phẩm trong giỏ hàng để đảm bảo tính chính xác về mặt tồn kho quà tặng.

### Khôi phục số lượng giỏ hàng từ lịch sử thao tác

Để tăng trải nghiệm người dùng, hệ thống có thể lưu trữ lịch sử các lần thay đổi số lượng trong một phiên làm việc. Nếu việc cập nhật số lượng dẫn đến lỗi hệ thống hoặc người dùng muốn quay lại số lượng trước đó, hệ thống cần có khả năng truy xuất lại trạng thái gần nhất từ bảng nhật ký. Quá trình này vẫn phải đi kèm với việc kiểm tra lại tồn kho tại thời điểm khôi phục để đảm bảo rằng các con số hiện tại vẫn còn hiệu lực trước khi cập nhật lại tổng tiền cuối cùng.
