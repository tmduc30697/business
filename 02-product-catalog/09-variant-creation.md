# Variant creation

### Quản lý kho thời trang đa kênh

Một cửa hàng quần áo cần quản lý các sản phẩm có nhiều thuộc tính như màu sắc, kích thước và chất liệu. Mỗi sự kết hợp giữa các thuộc tính này tạo thành một mã lưu kho duy nhất để theo dõi số lượng tồn kho chính xác. Khi khách hàng chọn một chiếc áo sơ mi màu trắng và size L, hệ thống phải trừ kho đúng mã đó chứ không phải trừ vào tổng số lượng áo sơ mi chung. Thách thức ở đây là việc hiển thị danh sách sản phẩm ngoài trang chủ sao cho gọn gàng nhưng vẫn cho phép người dùng lọc nhanh theo từng biến thể cụ thể.

### Thực đơn nhà hàng tùy chỉnh món ăn

Trong một ứng dụng đặt đồ ăn, một món chính có thể đi kèm với nhiều lựa chọn bổ sung hoặc thay đổi thành phần. Ví dụ, khi đặt một ly trà sữa, khách hàng có thể chọn kích cỡ ly, mức độ đường, mức độ đá và các loại topping đi kèm. Mỗi lựa chọn này có thể làm thay đổi giá cuối cùng của sản phẩm. Hệ thống cần ghi nhận chính xác cấu hình mà khách hàng đã chọn để đầu bếp có thể chế biến đúng yêu cầu và hóa đơn được tính toán chính xác dựa trên các tùy chọn thêm vào.

### Cấu hình máy tính xách tay theo yêu cầu

Một trang web bán đồ công nghệ cho phép người dùng tự cấu hình linh kiện cho laptop trước khi mua. Từ một mẫu máy cơ bản, người dùng có thể chọn nâng cấp dung lượng RAM, ổ cứng SSD hoặc thay đổi loại màn hình giữa độ phân giải Full HD và 4K. Khác với quần áo, các biến thể ở đây có mối quan hệ ràng buộc với nhau, ví dụ như một loại vỏ máy nhất định chỉ tương thích với một vài loại bo mạch chủ cụ thể. Việc thiết kế database phải đảm bảo lưu trữ được các quy tắc ràng buộc này để tránh người dùng chọn nhầm cấu hình không hợp lệ.

### Hệ thống bán vé rạp chiếu phim

Trong lĩnh vực giải trí, một bộ phim có thể được chiếu ở nhiều định dạng như 2D, 3D hoặc IMAX và tại các khung giờ khác nhau trong ngày. Mỗi suất chiếu tại một phòng chiếu cụ thể với một định dạng nhất định được coi là một biến thể của sản phẩm phim đó. Giá vé sẽ thay đổi tùy thuộc vào loại ghế là ghế thường hay ghế VIP và thời điểm xem là ngày thường hay cuối tuần. Bài toán yêu cầu quản lý sơ đồ ghế ngồi cho từng biến thể suất chiếu để tránh tình trạng trùng lặp chỗ ngồi.

### Quản lý sản phẩm sơn công nghiệp

Một công ty sản xuất sơn có danh mục sản phẩm rất đa dạng dựa trên bảng màu và dung tích đóng chai. Một loại sơn bóng nội thất có thể có hàng trăm mã màu khác nhau và được đóng gói trong các lon 1 lít, 5 lít hoặc thùng 18 lít. Điểm đặc biệt là giá của sản phẩm không chỉ phụ thuộc vào dung tích mà còn phụ thuộc vào nhóm màu vì một số màu đặc biệt đòi hỏi nguyên liệu pha chế đắt tiền hơn. Hệ thống cần hỗ trợ việc cập nhật giá hàng loạt cho các nhóm biến thể có cùng đặc điểm.

### Dịch vụ đăng ký gói thành viên phần mềm

Một công ty cung cấp phần mềm theo mô hình dịch vụ cần quản lý các gói đăng ký khác nhau cho người dùng. Các biến thể ở đây được xác định bởi thời hạn thanh toán như hàng tháng hoặc hàng năm và cấp độ tính năng như gói cá nhân, gói đội nhóm hoặc gói doanh nghiệp. Mỗi biến thể sẽ có những giới hạn sử dụng khác nhau như dung lượng lưu trữ hoặc số lượng dự án tối đa được tạo. Database cần lưu vết được lịch sử thay đổi gói của người dùng và tính toán phần tiền chênh lệch khi họ nâng cấp giữa chu kỳ.

### Kinh doanh gạch men và vật liệu xây dựng

Trong ngành vật liệu xây dựng, sản phẩm gạch men được quản lý theo mã sản phẩm, kích thước và đặc biệt là số lô sản xuất. Các thùng gạch thuộc cùng một mã màu nhưng khác lô sản xuất có thể có độ lệch màu nhẹ. Do đó, khi khách hàng đặt hàng, nhân viên kho phải chọn các biến thể thuộc cùng một lô để đảm bảo tính thẩm mỹ. Bài toán này yêu cầu hệ thống quản lý kho cực kỳ chi tiết đến từng thuộc tính kỹ thuật và vị trí lưu trữ trong kho bãi.

### Sàn giao dịch thẻ game và vật phẩm ảo

Trên một sàn giao dịch vật phẩm trong trò chơi điện tử, một thanh kiếm có thể có nhiều biến thể dựa trên độ bền, cấp độ cường hóa và các thuộc tính ẩn ngẫu nhiên. Mỗi vật phẩm là duy nhất mặc dù chúng có cùng tên gọi ban đầu. Khi thiết kế hệ thống này, việc lưu trữ các biến thể đòi hỏi khả năng mở rộng tốt vì số lượng thuộc tính tùy biến có thể tăng lên theo các bản cập nhật của trò chơi. API cần phải trả về thông số chi tiết của từng vật phẩm cụ thể để người mua so sánh trước khi giao dịch.

### Đặt phòng khách sạn và resort

Một khu nghỉ dưỡng có nhiều loại phòng như phòng đơn, phòng đôi hoặc biệt thự hướng biển. Với mỗi loại phòng, khách hàng có thể chọn các gói dịch vụ đi kèm như có bao gồm bữa sáng, dịch vụ đón tiễn sân bay hoặc chính sách hoàn hủy linh hoạt. Sự kết hợp giữa loại phòng và gói dịch vụ tạo ra các biến thể giá khác nhau cho cùng một đêm lưu trú. Hệ thống phải xử lý được việc kiểm tra phòng trống theo thời gian thực và áp dụng các chương trình khuyến mãi cho từng nhóm biến thể cụ thể.

### Quản lý dược phẩm theo đơn vị đóng gói

Trong ngành dược, một loại thuốc có thể được bán theo nhiều đơn vị tính khác nhau như viên lẻ, vỉ hoặc hộp. Mỗi đơn vị này có mã vạch riêng và giá bán lẻ được quy đổi từ đơn vị lớn nhất xuống đơn vị nhỏ nhất. Việc quản lý biến thể ở đây còn đi kèm với quản lý hạn sử dụng và số lô sản xuất cho từng đơn vị đóng gói. Khi bán một vỉ thuốc, hệ thống phải tự động tính toán số lượng tương ứng còn lại trong hộp để đảm bảo báo cáo tồn kho luôn chính xác.
