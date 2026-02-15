# Category management

### Phân cấp danh mục đa tầng không giới hạn độ sâu

Một sàn thương mại điện tử cần tổ chức hàng nghìn loại mặt hàng theo cấu trúc hình cây. Ví dụ, danh mục lớn nhất là Thời trang, bên trong có Thời trang nam, trong đó lại có Áo nam, rồi đến Áo sơ mi nam. Hệ thống phải cho phép người quản trị tạo ra các cấp con mới mà không bị giới hạn về số tầng. Khi thiết kế database, bạn cần giải quyết việc làm sao để truy vấn toàn bộ các danh mục con của một danh mục cha bất kỳ một cách nhanh nhất mà không làm quá tải máy chủ.

### Thay đổi cấu trúc và di chuyển danh mục cha con

Trong quá trình vận hành, người quản trị muốn tái cấu trúc lại toàn bộ hệ thống. Ví dụ, danh mục Máy tính bảng hiện đang nằm trong mục Điện thoại và Máy tính bảng, nhưng nay muốn chuyển nó thành danh mục con của mục Thiết bị điện tử. Khi di chuyển một danh mục cha, toàn bộ các danh mục con và các sản phẩm thuộc danh mục đó cũng phải được cập nhật theo đúng vị trí mới trong cây phân cấp mà không làm mất đi các liên kết dữ liệu cũ.

### Một sản phẩm thuộc nhiều danh mục khác nhau

Một chiếc đồng hồ thông minh vừa có thể thuộc danh mục Thiết bị đeo tay, vừa thuộc danh mục Phụ kiện công nghệ và cũng nằm trong danh mục Quà tặng cho nam. Bài toán đặt ra là làm thế nào để thiết kế cơ sở dữ liệu cho phép một sản phẩm liên kết với nhiều danh mục cùng lúc. Đồng thời, khi người dùng duyệt ở bất kỳ danh mục nào trong ba cái tên trên, họ đều phải thấy được sản phẩm đó hiện ra chính xác.

### Tùy chỉnh thứ tự hiển thị danh mục theo ý muốn

Trên giao diện trang chủ hoặc menu điều hướng, người quản trị muốn danh mục Khuyến mãi luôn đứng đầu tiên, sau đó mới đến các danh mục khác. Thứ tự này không tuân theo bảng chữ cái hay ID tăng dần mà được sắp xếp thủ công bằng cách kéo thả hoặc nhập số thứ tự ưu tiên. Bạn cần thiết kế API và database sao cho việc thay đổi thứ tự của một danh mục không gây ảnh hưởng đến hàng loạt bản ghi khác và việc truy vấn danh mục luôn trả về kết quả đã được sắp xếp đúng.

### Quản lý thuộc tính đặc thù theo từng danh mục

Mỗi danh mục sản phẩm sẽ có những thuộc tính lọc khác nhau. Ví dụ, khi người dùng vào danh mục Laptop, hệ thống cần hiển thị bộ lọc về RAM, Chip, Card đồ họa. Nhưng khi vào danh mục Thời trang, bộ lọc phải chuyển thành Kích cỡ, Chất liệu, Màu sắc. Bài toán này yêu cầu bạn thiết kế hệ thống sao cho các thuộc tính lọc được gắn chặt với cấp danh mục tương ứng và các danh mục con có thể thừa hưởng hoặc mở rộng thuộc tính từ danh mục cha.

### Đồng bộ hóa danh mục cho các chiến dịch theo mùa

Hệ thống cần tạo ra các danh mục tạm thời cho các dịp lễ như Giáng sinh hoặc Tết Nguyên đán. Các danh mục này chứa sản phẩm từ nhiều danh mục gốc khác nhau nhưng chỉ tồn tại trong một khoảng thời gian nhất định. Sau khi hết mùa, danh mục này sẽ ẩn đi nhưng không được xóa hoàn toàn dữ liệu để có thể tái sử dụng cho năm sau. Điều này đòi hỏi thiết kế thêm các trạng thái hiển thị và quản lý thời gian hiệu lực cho từng nhánh trong cây danh mục.

### Tối ưu hóa đường dẫn thân thiện cho SEO

Để hỗ trợ việc tìm kiếm trên Google, mỗi danh mục cần có một đường dẫn dạng văn bản không dấu và ngăn cách bởi dấu gạch ngang, gọi là slug. Ví dụ, danh mục Điện gia dụng sẽ có đường dẫn là dien-gia-dung. Thách thức ở đây là nếu có hai danh mục cùng tên nằm ở hai nhánh cha khác nhau, bạn phải xử lý việc trùng lặp slug như thế nào. Ngoài ra, nếu người quản trị đổi tên danh mục, hệ thống cần xử lý việc chuyển hướng từ đường dẫn cũ sang đường dẫn mới để không bị lỗi trang.

### Thống kê số lượng sản phẩm trong từng cấp danh mục

Trên giao diện người dùng, bên cạnh tên mỗi danh mục thường hiển thị số lượng sản phẩm đang kinh doanh bên trong đó, ví dụ Giày thể thao (150). Con số 150 này phải bao gồm tổng tất cả sản phẩm của các danh mục con bên dưới nó nữa. Việc đếm trực tiếp từ bảng sản phẩm mỗi khi người dùng tải trang sẽ rất chậm nếu dữ liệu lớn. Bạn cần thiết kế giải pháp để lưu trữ hoặc tính toán con số này một cách hiệu quả để đảm bảo tốc độ phản hồi của hệ thống.
