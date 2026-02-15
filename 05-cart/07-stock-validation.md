# Stock validation

### Giữ hàng trong giỏ hàng có thời hạn

Trong các trang thương mại điện tử vào ngày giảm giá lớn, khi người dùng thêm sản phẩm vào giỏ hàng và tiến hành thanh toán, hệ thống cần tạm giữ số lượng tồn kho đó trong một khoảng thời gian nhất định như mười lăm phút. Bài toán đặt ra là làm sao để cập nhật số lượng tồn kho thực tế và số lượng đang bị tạm giữ trong cơ sở dữ liệu để những người mua sau không nhìn thấy số lượng ảo, đồng thời phải có cơ chế tự động hoàn lại tồn kho nếu người dùng không hoàn tất thanh toán sau khi hết thời gian chờ.

### Flash Sale với lượng truy cập đột biến

Một hệ thống bán điện thoại thông minh tung ra chương trình giảm giá chỉ có một trăm sản phẩm nhưng có hàng chục ngàn người cùng nhấn nút mua tại một thời điểm. Vấn đề ở đây là việc kiểm tra tồn kho và trừ số lượng phải diễn ra cực nhanh và chính xác để tránh tình trạng bán quá số lượng thực tế có trong kho. Bạn cần thiết kế cách thức lưu trữ dữ liệu sao cho việc đọc ghi không bị nghẽn cổ chai và đảm bảo tính nhất quán dữ liệu giữa các máy chủ khác nhau.

### Quản lý tồn kho đa kho hàng cho một đơn hàng

Một chuỗi cửa hàng bán lẻ có nhiều kho hàng tại các thành phố khác nhau. Khi khách hàng đặt mua một đơn hàng gồm nhiều món hàng, hệ thống phải tự động kiểm tra xem kho nào gần khách hàng nhất còn đủ hàng để tối ưu phí vận chuyển. Nếu một kho không đủ tất cả các món, hệ thống phải quyết định tách đơn hàng ra nhiều kho hay điều chuyển hàng giữa các kho, điều này yêu cầu thiết kế bảng dữ liệu kho hàng và vị trí sản phẩm rất linh hoạt.

### Combo sản phẩm và linh kiện lắp ráp

Cửa hàng máy tính bán các bộ máy tính lắp sẵn được cấu thành từ nhiều linh kiện riêng lẻ như chip, ram, vỏ máy và nguồn. Khi một khách hàng mua một bộ máy tính combo, hệ thống không chỉ kiểm tra tồn kho của chính bộ combo đó mà phải kiểm tra đồng thời tồn kho của tất cả các linh kiện thành phần. Nếu chỉ cần một linh kiện hết hàng thì toàn bộ combo phải hiển thị là hết hàng trên website để ngăn chặn việc thanh toán không thể giao hàng.

### Đặt vé xem phim và chọn ghế trực tuyến

Hệ thống đặt vé xem phim yêu cầu việc xác minh tồn kho ở mức độ chi tiết đến từng vị trí ghế ngồi cụ thể trong phòng chiếu. Khó khăn nằm ở chỗ khi hai người dùng cùng chọn một chiếc ghế vào cùng một giây, hệ thống phải đảm bảo chỉ có một người được đi tiếp đến bước thanh toán. Việc thiết kế trạng thái của từng đơn vị hàng hóa và cơ chế khóa bản ghi trong cơ sở dữ liệu là yếu tố then chốt để giải quyết vấn đề này.

### Trả hàng và cập nhật tồn kho lỗi

Trong thực tế, không phải lúc nào hàng trả về cũng có thể bán lại ngay lập tức. Khi khách hàng hủy đơn hoặc trả hàng, hệ thống cần phân loại hàng trả về vào các trạng thái như hàng mới, hàng lỗi cần sửa chữa hoặc hàng hư hỏng hoàn toàn. Việc thiết kế hệ thống phải cho phép tách biệt giữa tồn kho tổng và tồn kho có thể bán để bộ phận bán hàng không bán nhầm những sản phẩm đang chờ xử lý kỹ thuật.

### Bán hàng đa kênh đồng bộ thời gian thực

Một đơn vị bán hàng đồng thời trên website riêng, trên các sàn thương mại điện tử lớn và tại cửa hàng vật lý. Khi có một đơn hàng phát sinh ở cửa hàng vật lý, số lượng tồn kho trên tất cả các sàn thương mại điện tử phải được cập nhật giảm ngay lập tức để tránh khách hàng trực tuyến đặt mua đúng món đồ vừa mới bán xong. Bài toán này tập trung vào thiết kế API và cơ chế hàng đợi tin nhắn để đẩy dữ liệu đi khắp các nền tảng một cách đồng bộ.

### Đặt trước sản phẩm chưa về kho

Đối với các sản phẩm sắp ra mắt, doanh nghiệp cho phép khách hàng đặt cọc trước mặc dù hàng chưa thực sự có trong kho vật lý. Hệ thống cần quản lý một loại tồn kho đặc biệt là tồn kho dự kiến sẽ về. Việc xác minh lúc này dựa trên số lượng nhà cung cấp cam kết giao và số lượng khách đã đặt cọc. Khi hàng về kho thật, hệ thống phải có quy trình chuyển đổi từ đơn đặt trước sang đơn hàng thực tế và ưu tiên xuất hàng cho những người đã đặt trước theo thứ tự thời gian.
