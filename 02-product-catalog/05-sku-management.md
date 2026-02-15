# SKU management

### Quản lý biến thể sản phẩm thời trang đa cấp

Trong ngành thời trang, một mẫu áo thun không chỉ có một mã SKU duy nhất mà bao gồm nhiều tổ hợp giữa kích cỡ và màu sắc. Bài toán yêu cầu bạn phải thiết kế hệ thống sao cho một sản phẩm cha có thể chứa hàng chục sản phẩm con. Mỗi sản phẩm con này là một SKU riêng biệt với số lượng tồn kho và giá bán có thể khác nhau. Thách thức nằm ở việc truy xuất nhanh toàn bộ các SKU thuộc về một sản phẩm cha để hiển thị trên giao diện người dùng và quản lý sự thay đổi thuộc tính linh hoạt như thêm bảng size mới hoặc màu sắc mới mà không làm hỏng cấu trúc dữ liệu cũ.

### Theo dõi lịch sử biến động kho theo từng SKU

Một SKU không chỉ là con số tĩnh mà luôn biến động qua các giao dịch nhập kho, xuất kho, chuyển kho nội bộ hoặc hoàn hàng. Bài toán này tập trung vào việc ghi lại nhật ký chi tiết cho từng lần thay đổi số lượng của một SKU cụ thể. Bạn cần thiết kế cách lưu trữ sao cho có thể truy vấn được số dư tồn kho tại một thời điểm bất kỳ trong quá khứ và xác định được nguyên nhân của mỗi lần tăng giảm. Điều này rất quan trọng để đối soát khi xảy ra thất thoát hàng hóa giữa thực tế và phần mềm.

### Quản lý SKU đồng bộ trên mô hình bán hàng đa kênh

Khi một doanh nghiệp bán hàng đồng thời trên website, cửa hàng trực tiếp và các sàn thương mại điện tử, việc quản lý SKU trở nên phức tạp do mỗi nền tảng có thể có quy định mã khác nhau. Bài toán đặt ra là làm thế nào để ánh xạ nhiều mã định danh từ các sàn về một mã SKU gốc duy nhất trong hệ thống quản trị trung tâm. Khi có một đơn hàng phát sinh từ sàn thương mại điện tử, hệ thống phải tự động trừ tồn kho của đúng SKU đó và cập nhật số lượng còn lại lên tất cả các kênh bán hàng khác để tránh tình trạng bán quá số lượng thực tế.

### Hệ thống cảnh báo ngưỡng tồn kho an toàn cho SKU

Mỗi SKU có tốc độ tiêu thụ khác nhau, do đó việc đặt ra một ngưỡng tồn kho tối thiểu là cần thiết để duy trì hoạt động kinh doanh. Bài toán yêu cầu xây dựng logic kiểm tra liên tục số lượng tồn kho hiện tại của từng SKU so với định mức an toàn đã thiết lập. Nếu số lượng giảm xuống dưới ngưỡng, hệ thống phải tự động tạo ra các đề xuất nhập hàng hoặc gửi thông báo cho bộ phận thu mua. Việc này đòi hỏi cấu trúc dữ liệu phải hỗ trợ cấu hình ngưỡng riêng biệt cho từng kho hàng hoặc từng chi nhánh khác nhau.

### Quản lý SKU đi kèm số Serial và số Lô sản xuất

Đối với các mặt hàng điện tử hoặc dược phẩm, việc chỉ quản lý mã SKU là chưa đủ. Một SKU áo thun có thể có 100 chiếc giống hệt nhau, nhưng một SKU điện thoại iPhone cần quản lý chi tiết đến từng số Serial cho mỗi máy, hoặc một SKU thuốc cần quản lý theo số lô và hạn sử dụng. Bài toán này yêu cầu bạn thiết kế tầng dữ liệu bổ sung để theo dõi từng đơn vị hàng hóa cụ thể trong cùng một mã SKU. Điều này phục vụ cho việc bảo hành hoặc thu hồi sản phẩm theo lô khi có sự cố về chất lượng.

### Xử lý SKU cho mô hình đóng gói Combo và Bộ sản phẩm

Thực tế kinh doanh thường xuất hiện nhu cầu bán các gói Combo gồm nhiều SKU thành phần để khuyến khích mua sắm. Bài toán ở đây là làm thế nào để quản lý một mã SKU ảo đại diện cho Combo đó. Khi khách hàng mua một Combo, hệ thống không chỉ trừ tồn kho của mã Combo (nếu có) mà quan trọng hơn là phải tự động tính toán và trừ tồn kho của các SKU thành phần cấu thành nên nó. Đồng thời, hệ thống phải có khả năng kiểm tra xem liệu có đủ các thành phần để tạo thành một Combo hay không trước khi cho phép khách hàng đặt hàng.

### Quản lý mã vạch và quy đổi đơn vị tính cho SKU

Một sản phẩm có thể có một mã SKU duy nhất nhưng lại được quản lý dưới nhiều mã vạch khác nhau từ nhà sản xuất hoặc mã nội bộ. Thêm vào đó, bài toán đơn vị tính cũng rất phổ biến: nhập hàng theo Thùng nhưng bán ra theo Lon hoặc Gói. Bạn cần thiết kế hệ thống sao cho một mã SKU có thể tương ứng với nhiều đơn vị tính với tỷ lệ quy đổi cụ thể. Khi nhân viên kho quét bất kỳ mã vạch nào liên quan, hệ thống phải nhận diện đúng SKU và tự động thực hiện phép tính quy đổi để cập nhật chính xác số lượng tồn kho theo đơn vị cơ bản nhất.
