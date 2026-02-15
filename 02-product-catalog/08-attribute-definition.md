# Attribute definition

### Quản lý cấu hình máy tính xách tay theo thông số kỹ thuật

Trong ngành hàng điện tử, một mẫu laptop có thể có hàng chục cấu hình khác nhau. Bài toán yêu cầu bạn định nghĩa các thuộc tính như loại CPU, dung lượng RAM, loại ổ cứng và kích thước màn hình. Khó khăn nằm ở chỗ mỗi thuộc tính lại có đơn vị đo lường khác nhau (ví dụ RAM dùng GB, CPU dùng GHz). Bạn cần thiết kế hệ thống sao cho khi người dùng chọn một thuộc tính, hệ thống sẽ lọc ra được các phiên bản sản phẩm tương ứng và hiển thị đúng thông số kỹ thuật chi tiết của phiên bản đó.

### Hệ thống phân loại kích cỡ và chất liệu trong thời trang nhanh

Ngành thời trang đối mặt với vấn đề đa dạng về bảng quy đổi kích cỡ giữa các thương hiệu. Bài toán này yêu cầu định nghĩa thuộc tính màu sắc và kích cỡ nhưng phải đi kèm với thuộc tính chất liệu và hướng dẫn bảo quản. Bạn cần xử lý việc một chiếc áo phông có thể có màu xanh, size L, làm từ 100% cotton, trong khi chiếc khác lại là sự pha trộn giữa nhiều loại vải. Hệ thống phải cho phép quản lý kho dựa trên sự kết hợp của các thuộc tính này để tạo ra các mã định danh duy nhất cho từng biến thể.

### Tùy chỉnh thành phần và topping trong ứng dụng đặt đồ ăn

Khác với hàng hóa vật lý, thuộc tính của món ăn thường mang tính thêm bớt. Bài toán đặt ra là định nghĩa các thuộc tính như mức đường, mức đá, và các loại topping đi kèm. Mỗi thuộc tính này có thể làm thay đổi giá cuối cùng của sản phẩm. Bạn cần thiết kế sao cho hệ thống có thể định nghĩa được thuộc tính nào là bắt buộc chọn, thuộc tính nào là tùy chọn, và giới hạn số lượng lựa chọn tối đa cho mỗi nhóm thuộc tính để đảm bảo quy trình chế biến.

### Quản lý thuộc tính động cho sàn thương mại điện tử đa ngành hàng

Một sàn thương mại điện tử bán cả thực phẩm lẫn đồ gia dụng sẽ có bộ thuộc tính hoàn toàn khác nhau. Thực phẩm cần ngày hết hạn và điều kiện bảo quản, trong khi đồ gia dụng cần công suất điện và thời gian bảo hành. Bài toán yêu cầu bạn thiết kế một cấu trúc thuộc tính động (Dynamic Attributes) để người quản trị có thể tự thêm mới các loại thuộc tính mà không cần thay đổi cấu trúc bảng trong cơ sở dữ liệu mỗi khi có ngành hàng mới xuất hiện.

### Hệ thống sơn và pha màu công nghiệp theo mã màu quốc tế

Trong ngành sơn, thuộc tính màu sắc không chỉ đơn thuần là tên gọi mà còn là các mã màu theo tiêu chuẩn quốc tế hoặc công thức pha trộn. Bài toán yêu cầu định nghĩa thuộc tính màu sắc đi kèm với độ bóng và dung tích bao bì. Hệ thống phải xử lý được việc một mã màu có thể áp dụng cho nhiều loại sơn khác nhau (sơn dầu, sơn nước) và mỗi sự kết hợp này sẽ dẫn đến một quy trình sản xuất và mức giá riêng biệt.

### Cấu hình đồ nội thất lắp ghép theo không gian sống

Sản phẩm nội thất như tủ quần áo thường có các thuộc tính về số cánh cửa, loại tay nắm, và màu sơn gỗ. Bài toán này đòi hỏi việc định nghĩa thuộc tính phải có tính ràng buộc. Ví dụ, nếu khách hàng chọn loại tủ kích thước nhỏ thì không thể chọn loại cửa lùa lớn. Bạn cần thiết kế hệ thống thuộc tính sao cho các giá trị của thuộc tính này có thể giới hạn hoặc kích hoạt các giá trị của thuộc tính kia, phục vụ cho việc tạo ra các bộ lọc thông minh trên giao diện người dùng.

### Phân loại phụ tùng ô tô theo khả năng tương thích dòng xe

Đây là bài toán phức tạp về thuộc tính kỹ thuật. Một linh kiện như má phanh có các thuộc tính về kích thước vật lý, chất liệu chịu nhiệt và đặc biệt là danh sách các dòng xe tương thích. Thuộc tính ở đây không chỉ là mô tả sản phẩm mà còn là dữ liệu để truy vấn chéo. Bạn cần định nghĩa các thuộc tính sao cho khi người dùng nhập tên dòng xe và năm sản xuất, hệ thống phải trả về đúng các linh kiện có thuộc tính tương ứng với thông số của chiếc xe đó.

### Quản lý gói dịch vụ phần mềm dựa trên tính năng và giới hạn

Trong mô hình kinh doanh phần mềm, thuộc tính của sản phẩm chính là các tính năng và giới hạn sử dụng (ví dụ: số lượng người dùng, dung lượng lưu trữ). Bài toán yêu cầu định nghĩa các gói dịch vụ (Basic, Pro, Enterprise) thông qua các thuộc tính định lượng và định tính. Hệ thống cần cho phép thay đổi giá trị của các thuộc tính này để tạo ra các gói khuyến mãi hoặc gói tùy chỉnh cho khách hàng doanh nghiệp mà không làm xáo trộn cấu trúc sản phẩm cốt lõi.
