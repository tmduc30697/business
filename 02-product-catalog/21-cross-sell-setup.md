# Cross-sell setup

### Gợi ý phụ kiện theo nhóm sản phẩm bắt buộc

Trong mô hình bán lẻ điện tử, một sản phẩm chính thường đi kèm với danh sách phụ kiện tương thích hoàn toàn. Bài toán yêu cầu hệ thống phải quản lý được các ràng buộc kỹ thuật, ví dụ như ốp lưng iPhone 15 không thể gợi ý cho người mua iPhone 15 Pro. Dữ liệu cần thể hiện được mối quan hệ cha con và các thuộc tính tương thích để khi người dùng xem một sản phẩm, hệ thống tự động lọc ra danh sách phụ kiện phù hợp nhất đang còn hàng trong kho.

### Combo ưu đãi cố định từ nhà bán hàng

Nhà bán hàng muốn tạo ra các gói sản phẩm mua cùng nhau để được giảm giá sâu, ví dụ combo máy ảnh, ống kính và thẻ nhớ. Bài toán này đòi hỏi việc thiết kế database sao cho có thể lưu trữ một thực thể combo như một sản phẩm ảo nhưng vẫn liên kết chặt chẽ với tồn kho của từng món đơn lẻ bên trong. Khi người dùng thêm combo vào giỏ hàng, hệ thống cần tính toán lại giá khuyến mãi và kiểm tra xem tất cả các thành phần có đủ số lượng cung ứng hay không.

### Gợi ý dựa trên hành vi mua sắm cùng nhau của cộng đồng

Đây là tính năng thường thấy trên các sàn thương mại điện tử lớn dưới dạng khách hàng thường mua cùng nhau. Hệ thống cần ghi nhận lại lịch sử các đơn hàng thành công để tìm ra những cặp sản phẩm có tần suất xuất hiện chung cao nhất. Thử thách ở đây là thiết kế hệ thống xử lý dữ liệu lớn để cập nhật các gợi ý này theo thời gian thực hoặc theo định kỳ mà không làm ảnh hưởng đến hiệu năng của trang chi tiết sản phẩm.

### Bán kèm dịch vụ bảo hành và bảo hiểm mở rộng

Đối với các mặt hàng giá trị cao như đồ gia dụng hoặc xe máy, việc bán kèm không chỉ là hàng hóa vật lý mà còn là các gói dịch vụ. Các gói bảo hiểm này thường có quy tắc tính phí dựa trên phần trăm giá trị sản phẩm chính hoặc một mức giá cố định tùy theo phân khúc. Hệ thống API cần xử lý được việc ràng buộc dịch vụ vào sản phẩm chính sao cho nếu sản phẩm chính bị xóa khỏi giỏ hàng, dịch vụ đi kèm cũng phải tự động bị loại bỏ.

### Gợi ý sản phẩm thay thế khi hết hàng

Mặc dù không hoàn toàn là cross-sell truyền thống nhưng việc gợi ý sản phẩm tương tự khi món hàng khách muốn mua đã hết kho là một bài toán rất quan trọng. Hệ thống cần phân tích các thuộc tính như thương hiệu, tầm giá, và công dụng để đưa ra lựa chọn thay thế tốt nhất. Điều này yêu cầu một cấu trúc database về danh mục và thuộc tính sản phẩm cực kỳ linh hoạt để thực hiện các câu truy vấn tìm kiếm sự tương đồng.

### Hệ thống quà tặng kèm theo giá trị đơn hàng

Nhiều cửa hàng áp dụng chính sách mua sản phẩm A sẽ được chọn 1 trong 3 món quà miễn phí ở danh mục B. Bài toán này phức tạp ở chỗ phải quản lý được điều kiện áp dụng và giới hạn số lượng quà tặng trên mỗi đơn hàng. Việc thiết kế ERD phải đảm bảo tách biệt được sản phẩm có giá và sản phẩm quà tặng nhưng vẫn duy trì được mối liên kết để phục vụ cho việc quản lý kho và báo cáo doanh thu sau này.

### Cross-sell cá nhân hóa dựa trên lịch sử xem trang

Hệ thống sẽ theo dõi các sản phẩm mà người dùng đã xem trong phiên làm việc hiện tại để gợi ý những món đồ liên quan ở trang thanh toán. Ví dụ, nếu khách đã xem qua 3 mẫu áo thun khác nhau nhưng chỉ bỏ 1 cái vào giỏ, hệ thống sẽ gợi ý 2 mẫu còn lại hoặc các mẫu quần phù hợp với phong cách đó. Đây là bài toán về thiết kế hệ thống lưu trữ cache hoặc session để truy xuất nhanh danh sách hành vi người dùng.

### Gợi ý sản phẩm theo mùa và xu hướng ngắn hạn

Vào các dịp lễ như Valentine hay Tết, các sản phẩm vốn không liên quan có thể được bán kèm nhau trong một chiến dịch marketing ngắn hạn, ví dụ mua chocolate tặng kèm gấu bông. Hệ thống cần một module quản lý chiến dịch linh hoạt, cho phép người quản trị thiết lập thời gian bắt đầu và kết thúc của các liên kết sản phẩm này. Sau khi chiến dịch kết thúc, các mối liên kết cross-sell này phải tự động biến mất mà không cần can thiệp thủ công vào cơ sở dữ liệu sản phẩm.
