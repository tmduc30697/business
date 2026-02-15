# Variant pricing

### Kinh doanh thời trang đa kích cỡ và màu sắc

Trong ngành hàng quần áo, các size lớn như XXL hoặc XXXL thường tiêu tốn nhiều vải hơn và chi phí vận chuyển cao hơn so với size S hoặc M. Hệ thống cần cho phép chủ cửa hàng thiết lập một mức giá cơ bản cho mẫu áo thun, nhưng khi khách hàng chọn các size đặc biệt hoặc các màu sắc sử dụng công nghệ nhuộm đắt tiền, giá hiển thị trên giỏ hàng phải tự động cập nhật theo giá riêng của biến thể đó thay vì dùng giá gốc.

### Dịch vụ lưu trú khách sạn theo ngày trong tuần

Một khách sạn bán phòng tiêu chuẩn với giá mặc định áp dụng cho các ngày từ thứ Hai đến thứ Năm. Tuy nhiên, cùng là căn phòng đó nhưng vào các biến thể ngày thứ Sáu và Chủ Nhật hoặc các ngày lễ cao điểm, giá thuê phải được cấu hình riêng biệt. Bài toán đặt ra là làm sao để khi người dùng chọn ngày trên lịch, hệ thống truy vấn đúng bảng giá biến thể thời gian để trả về tổng tiền chính xác.

### Phân phối linh kiện máy tính lắp ráp

Khi bán một bộ máy tính, giá tổng thể thường dựa trên cấu hình linh kiện bên trong. Ví dụ, một mẫu máy tính văn phòng có giá nền, nhưng nếu khách hàng nâng cấp biến thể dung lượng RAM từ 8GB lên 16GB hoặc đổi ổ cứng từ SSD 256GB sang 512GB, mỗi sự thay đổi này không chỉ cộng thêm tiền mà là một mức giá định danh riêng cho tổ hợp đó. Hệ thống phải quản lý được hàng nghìn mã biến thể với các mức giá chênh lệch nhau rất lớn.

### Gói đăng ký phần mềm SaaS theo số lượng người dùng

Một công ty phần mềm cung cấp gói dịch vụ với giá mặc định cho tối đa 5 người sử dụng. Khi khách hàng chọn biến thể dành cho 10 người, 20 người hoặc số lượng không giới hạn, mức giá không đơn thuần là nhân lên theo cấp số nhân mà là một con số cố định đã được thiết lập sẵn cho gói đó. Việc lưu trữ cần đảm bảo khi thay đổi giá gói chính, các gói biến thể vẫn giữ nguyên giá cũ nếu không có lệnh cập nhật thủ công.

### Thực phẩm tươi sống theo trọng lượng đóng gói

Tại các siêu thị trực tuyến, một loại thịt bò có thể được bán theo các quy cách đóng gói khác nhau như khay 200 gram, 500 gram hoặc 1kg. Thay vì tạo ra ba sản phẩm riêng lẻ gây loãng dữ liệu tìm kiếm, người ta tạo một sản phẩm duy nhất với các biến thể trọng lượng. Giá của khay 1kg thường sẽ rẻ hơn so với việc mua năm khay 200 gram, do đó mỗi biến thể trọng lượng cần có một ô nhập liệu giá riêng biệt hoàn toàn với giá niêm yết của sản phẩm gốc.

### Vé sự kiện âm nhạc theo khu vực chỗ ngồi

Một buổi biểu diễn ca nhạc có cùng một mã sản phẩm là vé xem show, nhưng giá vé lại phụ thuộc vào biến thể vị trí ghế ngồi như hạng phổ thông, hạng VIP hoặc hạng Premium. Mỗi khu vực ghế ngồi là một biến thể và có mức giá độc lập. Thách thức ở đây là hệ thống phải xử lý việc giữ chỗ và áp dụng đúng bảng giá cho từng khu vực trong thời gian thực khi có hàng ngàn người cùng truy cập mua vé.

### Đặt món ăn tại nhà hàng với tùy chọn thêm

Khi khách hàng đặt một bát phở trên ứng dụng, giá mặc định là giá cho bát phở truyền thống. Tuy nhiên, các biến thể như thêm bò viên, thêm trứng chèn hoặc bát đặc biệt sẽ có mức giá riêng. Điểm phức tạp là một sản phẩm có thể có nhiều nhóm biến thể kết hợp với nhau, và hệ thống cần tính toán xem nên cộng dồn giá hay lấy giá của biến thể cuối cùng làm giá thanh toán chính thức.

### Kinh doanh vật liệu xây dựng theo đơn vị tính

Một cửa hàng sơn bán cùng một loại sơn nhưng dưới các dạng biến thể đơn vị như lon 1 lít, thùng 5 lít hoặc thùng 18 lít. Giá của biến thể thùng 18 lít không nhất thiết phải bằng 18 lần giá của lon 1 lít do chi phí bao bì và chiết khấu bán buôn. Nhân viên bán hàng cần một giao diện quản lý nơi họ có thể nhìn thấy tất cả quy cách đóng gói và chỉnh sửa giá nhanh chóng cho từng đơn vị mà không làm ảnh hưởng đến giá của các đơn vị khác.
