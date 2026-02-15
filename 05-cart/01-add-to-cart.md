# Add to cart

### Quản lý sản phẩm đa biến thể với thuộc tính động

Trong các hệ thống thương mại điện tử ngành thời trang, một sản phẩm không chỉ có tên và giá mà còn tồn tại nhiều biến thể dựa trên màu sắc, kích thước và chất liệu. Khi người dùng nhấn thêm vào giỏ hàng, hệ thống không chỉ lưu mã sản phẩm chính mà phải xác định chính xác mã định danh của biến thể cụ thể đó. Thách thức ở đây là cấu trúc dữ liệu phải linh hoạt để phản ánh đúng lựa chọn của khách hàng, đảm bảo rằng khi vào giỏ hàng, hình ảnh và tên biến thể hiển thị tương ứng với những gì họ đã chọn ban đầu.

### Ràng buộc tồn kho thực tế và giữ hàng tạm thời

Một vấn đề phổ biến là khi người dùng thêm sản phẩm vào giỏ hàng nhưng không thanh toán ngay, dẫn đến tình trạng tồn kho ảo. Bài toán yêu cầu hệ thống phải kiểm tra số lượng hàng còn lại trong kho ngay tại thời điểm người dùng nhấn nút thêm. Bạn cần thiết kế logic để xử lý việc giữ hàng trong một khoảng thời gian nhất định hoặc thông báo hết hàng nếu có nhiều người cùng thêm một sản phẩm cuối cùng vào giỏ hàng tại cùng một thời điểm, đảm bảo tính nhất quán dữ liệu giữa giỏ hàng và kho vận.

### Đồng bộ giỏ hàng giữa người dùng khách và thành viên

Người dùng thường có thói quen duyệt web và thêm hàng vào giỏ trước khi đăng nhập. Bài toán đặt ra là làm thế nào để lưu trữ giỏ hàng tạm thời dưới trình duyệt hoặc phía server cho khách vãng lai, sau đó thực hiện hợp nhất dữ liệu đó vào tài khoản chính thức sau khi họ đăng nhập thành công. Việc hợp nhất này cần xử lý các tình huống trùng lặp sản phẩm, cập nhật lại số lượng mới nhất và đảm bảo không làm mất đi các lựa chọn trước đó của người dùng trên cả hai trạng thái.

### Áp dụng khuyến mãi và thay đổi giá theo thời gian thực

Giá của sản phẩm có thể thay đổi do các chương trình flash sale hoặc mã giảm giá được áp dụng trực tiếp khi thêm vào giỏ. Hệ thống cần ghi nhận mức giá tại thời điểm người dùng thực hiện hành động thêm hàng để đối chiếu với giá lúc thanh toán. Bài toán yêu cầu bạn thiết kế cách lưu trữ thông tin giá gốc, giá sau giảm và các điều kiện khuyến mãi đi kèm sao cho khi người dùng thay đổi số lượng trong giỏ hàng, các mức chiết khấu được tính toán lại một cách chính xác và minh bạch.

### Quản lý giỏ hàng cho mô hình chợ điện tử nhiều nhà bán hàng

Trong mô hình Marketplace, một giỏ hàng có thể chứa sản phẩm từ nhiều nhà cung cấp khác nhau. Mỗi nhóm sản phẩm của từng nhà bán hàng sẽ có quy định về phí vận chuyển, đơn vị vận chuyển và kho bãi riêng biệt. Khi thiết kế hệ thống này, bạn cần phân tách các sản phẩm trong giỏ theo nhà bán hàng ngay từ bước thêm vào, giúp việc tính toán tổng tiền và phân loại đơn hàng ở các bước sau trở nên dễ dàng hơn, đồng thời cho phép người dùng chọn thanh toán riêng cho từng shop.

### Giới hạn số lượng mua tối đa cho mỗi sản phẩm

Để ngăn chặn việc đầu cơ hoặc theo chính sách của cửa hàng, một số sản phẩm chỉ cho phép mỗi khách hàng mua tối đa một số lượng nhất định. Khi người dùng thực hiện hành động thêm vào giỏ hàng, hệ thống phải truy vấn lịch sử mua hàng của người dùng đó cộng với số lượng hiện có trong giỏ để đưa ra cảnh báo nếu vượt quá định mức. Điều này đòi hỏi sự phối hợp chặt chẽ giữa dữ liệu giỏ hàng hiện tại và dữ liệu đơn hàng đã hoàn tất trong quá khứ.

### Lưu trữ trạng thái giỏ hàng phục vụ tiếp thị lại

Rất nhiều người dùng thêm hàng vào giỏ nhưng sau đó rời đi mà không thanh toán. Bài toán thực tế yêu cầu hệ thống phải lưu trữ giỏ hàng lâu dài và ghi nhận thời điểm cập nhật cuối cùng để bộ phận marketing có thể gửi email nhắc nhở hoặc thông báo giảm giá cho chính sản phẩm đó. Bạn cần thiết kế cơ chế dọn dẹp các giỏ hàng cũ đã quá hạn nhưng vẫn phải giữ lại dữ liệu phân tích để hiểu được hành vi từ bỏ giỏ hàng của khách hàng diễn ra ở bước nào.

### Xử lý sản phẩm tặng kèm và combo tự động

Khi thêm một sản phẩm chính vào giỏ hàng, hệ thống có thể tự động thêm các sản phẩm quà tặng 0 đồng hoặc các sản phẩm đi kèm trong một gói combo. Bài toán này yêu cầu sự phức tạp trong việc quản lý quan hệ giữa các item trong giỏ hàng. Bạn phải đảm bảo rằng nếu người dùng xóa sản phẩm chính hoặc giảm số lượng xuống dưới mức điều kiện, các sản phẩm tặng kèm cũng phải tự động được điều chỉnh hoặc xóa bỏ tương ứng để tránh gian lận trong mua sắm.
