# Create product

### Quản lý sản phẩm có nhiều biến thể

Trong thực tế, một mẫu áo thun có thể có nhiều kích thước như S, M, L và nhiều màu sắc như Xanh, Đỏ, Tím. Mỗi sự kết hợp giữa màu sắc và kích thước này được gọi là một SKU với mức giá và số lượng tồn kho riêng biệt. Bài toán đặt ra là làm thế nào để lưu trữ cấu trúc cha - con này sao cho seller chỉ cần nhập thông tin chung một lần nhưng vẫn quản lý được chi tiết từng biến thể, đồng thời hỗ trợ việc tìm kiếm và lọc sản phẩm theo thuộc tính một cách hiệu quả.

### Hệ thống danh mục đa cấp và thuộc tính động

Mỗi ngành hàng lại có những đặc tính kỹ thuật hoàn toàn khác nhau. Ví dụ, điện thoại cần các trường thông tin như dung lượng pin, RAM trong khi mặt hàng thời trang lại cần chất liệu vải hay kiểu dáng. Bạn cần giải quyết vấn đề thiết kế một hệ thống danh mục phân cấp nhiều tầng và đi kèm với đó là bộ thuộc tính tùy chỉnh (Dynamic Attributes) cho từng danh mục để seller có thể điền đúng các thông số kỹ thuật mà ngành hàng đó yêu cầu.

### Quản lý kho hàng đa kho và đồng bộ tồn kho

Một người bán có thể có nhiều kho hàng đặt tại các vị trí địa lý khác nhau như kho Hà Nội và kho Sài Gòn. Khi tạo sản phẩm, seller cần phân bổ số lượng tồn kho cho từng kho cụ thể. Bài toán yêu cầu thiết kế logic để khi có đơn hàng, hệ thống phải trừ tồn kho đúng kho hàng đã chọn và cảnh báo cho seller khi tổng số lượng hàng khả dụng trong tất cả các kho chạm mức tối thiểu.

### Tối ưu hóa lưu trữ và xử lý hình ảnh sản phẩm

Hình ảnh là yếu tố quan trọng nhất để thu hút khách hàng nhưng lại gây áp lực lên băng thông và dung lượng lưu trữ. Khi seller tải lên một tấm ảnh gốc có dung lượng lớn, hệ thống cần thực hiện các tác vụ như thay đổi kích thước thành nhiều phiên bản khác nhau, nén ảnh để tối ưu tốc độ tải trang và lưu trữ đường dẫn vào database sao cho dễ dàng truy xuất theo thứ tự ưu tiên ảnh bìa và ảnh chi tiết.

### Chiến lược giá đa dạng và lịch sử thay đổi giá

Giá sản phẩm không cố định mà thường xuyên thay đổi theo các chương trình khuyến mãi hoặc biến động thị trường. Bài toán yêu cầu thiết kế hệ thống có khả năng lưu trữ giá bán lẻ, giá gốc để tính lợi nhuận và đặc biệt là cơ chế lưu lại lịch sử thay đổi giá (Price History). Việc này không chỉ giúp seller theo dõi biến động doanh thu mà còn phục vụ cho việc hiển thị biểu đồ biến động giá cho người mua trong tương lai.

### Kiểm duyệt nội dung và trạng thái sản phẩm

Để đảm bảo chất lượng sàn thương mại điện tử, sản phẩm sau khi được tạo thường không được hiển thị ngay lập tức. Hệ thống cần một quy trình trạng thái phức tạp bao gồm: Đang chờ duyệt, Đã duyệt, Bị từ chối (kèm lý do), Bản nháp hoặc Tạm ẩn. Bạn cần thiết kế logic nghiệp vụ để kiểm soát quyền chỉnh sửa của seller trong khi sản phẩm đang chờ duyệt và cách thức hệ thống phản hồi trạng thái hiển thị dựa trên các điều kiện này.

### Tích hợp đơn vị vận chuyển và thông số đóng gói

Mỗi sản phẩm khi tạo cần đi kèm với các thông số vật lý như cân nặng, chiều dài, chiều rộng và chiều cao sau khi đóng gói. Những thông tin này là đầu vào bắt buộc để hệ thống gọi API của các đơn vị vận chuyển nhằm tính toán phí giao hàng dự kiến. Thách thức ở đây là thiết kế cách lưu trữ các thông số này sao cho có thể linh hoạt tính toán phí vận chuyển ngay cả khi đơn hàng có nhiều sản phẩm khác nhau được đóng gói chung.

### Hỗ trợ đa ngôn ngữ cho thông tin sản phẩm

Nếu seller muốn bán hàng ra thị trường quốc tế, các thông tin như tên sản phẩm và mô tả cần được hiển thị theo ngôn ngữ của người mua. Thay vì tạo nhiều sản phẩm khác nhau, bạn cần thiết kế cấu trúc database hỗ trợ Localization, cho phép lưu trữ nhiều bản dịch cho cùng một ID sản phẩm. Điều này đòi hỏi cách thiết kế bảng Schema sao cho việc truy vấn ngôn ngữ mặc định và ngôn ngữ phụ trở nên nhanh chóng và không làm phình to dữ liệu quá mức.
