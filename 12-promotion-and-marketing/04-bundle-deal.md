# Bundle deal

### Gói sản phẩm cố định không thay đổi thành phần

Cửa hàng kinh doanh thiết bị máy tính muốn tạo một gói Combo Gaming bao gồm đúng một con chuột, một bàn phím và một tai nghe cụ thể. Khách hàng không được phép thay đổi bất kỳ món đồ nào trong gói này. Hệ thống cần quản lý giá của cả gói thấp hơn tổng giá lẻ, đồng thời khi khách hàng thêm gói này vào giỏ hàng, database phải ghi nhận mối liên kết để khi trừ tồn kho, cả ba mặt hàng lẻ đều được cập nhật số lượng tương ứng.

### Gói sản phẩm linh hoạt chọn lựa theo danh mục

Một cửa hàng mỹ phẩm cho phép khách hàng tự tạo gói quà tặng bằng cách chọn một loại sữa rửa mặt bất kỳ và một loại kem dưỡng bất kỳ trong danh sách mười sản phẩm quy định. Giá của gói sẽ cố định bất kể khách hàng chọn sản phẩm đắt hay rẻ trong danh mục đó. Bài toán này yêu cầu thiết kế database có khả năng định nghĩa các nhóm sản phẩm hợp lệ cho từng vị trí trong gói và kiểm tra tính hợp lệ khi người dùng gửi yêu cầu đặt hàng qua API.

### Mua càng nhiều giảm càng sâu theo số lượng sản phẩm

Một siêu thị áp dụng chương trình mua ba món đồ gia dụng bất kỳ trong danh sách khuyến mãi để được hưởng mức giá ưu đãi đồng giá cho mỗi món. Nếu khách hàng chỉ mua một hoặc hai món, giá sẽ quay về giá niêm yết ban đầu. Hệ thống cần tính toán lại giá trị giỏ hàng một cách động ngay khi số lượng sản phẩm thỏa mãn điều kiện gói được thêm vào, đồng thời phải xử lý được trường hợp khách hàng xóa bớt một sản phẩm ra khỏi gói sau khi đã áp dụng giảm giá.

### Gói sản phẩm có tùy chọn thuộc tính riêng lẻ

Cửa hàng thời trang bán gói Combo ba áo thun với mức giá ưu đãi. Tuy nhiên, mỗi chiếc áo trong gói khách hàng đều phải được chọn kích cỡ và màu sắc riêng biệt. Điều này gây khó khăn cho việc quản lý tồn kho vì mã định danh của gói không đại diện cho một thực thể vật lý duy nhất. Bạn cần thiết kế hệ thống sao cho dữ liệu đơn hàng lưu trữ được chi tiết thuộc tính của từng món con bên trong một mã gói tổng quát.

### Giới hạn số lượng gói bán ra dựa trên tồn kho sản phẩm thấp nhất

Một gói combo bao gồm một máy pha cà phê và hai túi hạt cà phê. Trong kho hiện có mười máy pha nhưng chỉ còn mười túi hạt. Mặc dù số lượng máy pha còn nhiều, hệ thống phải tự động tính toán và hiển thị rằng chỉ còn tối đa năm gói combo có thể bán được cho khách hàng. Bài toán này đòi hỏi logic tính toán tồn kho ảo của gói dựa trên sự ràng buộc về số lượng của các sản phẩm thành phần trong thời gian thực.

### Chính sách hoàn trả một phần sản phẩm trong gói combo

Khách hàng mua một gói combo gồm điện thoại và ốp lưng với giá ưu đãi, sau đó họ muốn hoàn trả lại chỉ riêng chiếc điện thoại vì lỗi kỹ thuật nhưng muốn giữ lại ốp lưng. Hệ thống cần có quy tắc xử lý tài chính để tính toán lại số tiền hoàn lại cho khách hàng sao cho không bị thiệt hại cho cửa hàng, ví dụ như thu hồi lại phần chiết khấu của gói và tính giá chiếc ốp lưng theo giá bán lẻ ban đầu.

### Gói sản phẩm mua kèm giá sốc khi đạt giá trị đơn hàng tối thiểu

Khi khách hàng mua một chiếc laptop có giá trị trên một mức quy định, hệ thống sẽ gợi ý một gói phụ kiện gồm chuột và túi chống sốc với mức giá gần như tặng kèm. Gói này chỉ xuất hiện và có hiệu lực nếu sản phẩm chính có mặt trong giỏ hàng. Nếu người dùng xóa sản phẩm chính là chiếc laptop, gói phụ kiện phải tự động bị hủy bỏ hoặc chuyển về giá bán lẻ thông thường để tránh việc khách hàng trục lợi mua lẻ phụ kiện giá rẻ.

### Phân bổ doanh thu cho các sản phẩm trong một gói combo

Về mặt kế toán, khi bán một gói combo có giá thấp hơn tổng giá lẻ, hệ thống cần có cơ chế phân bổ doanh thu cho từng sản phẩm thành phần dựa trên tỷ trọng giá trị ban đầu của chúng. Điều này cực kỳ quan trọng cho việc báo cáo lợi nhuận của từng ngành hàng và tính toán thuế. Thiết kế database của bạn phải lưu trữ được giá trị thực tế đã phân bổ cho từng món hàng bên trong gói tại thời điểm thanh toán thành công.
