# Order detail view

### Xử lý đơn hàng đa kho và giao hàng từng phần

Trong kịch bản này, một đơn hàng lớn của khách hàng không được xử lý tại một địa điểm duy nhất. Hệ thống cần hiển thị chi tiết cách chia nhỏ các sản phẩm trong đơn hàng theo từng kho hàng khác nhau dựa trên vị trí địa lý hoặc tình trạng tồn kho. Bài toán yêu cầu theo dõi trạng thái vận chuyển riêng biệt cho từng gói hàng trong cùng một mã đơn hàng tổng, bao gồm các thông tin về đơn vị vận chuyển khác nhau và mã vận đơn riêng lẻ cho mỗi kiện hàng.

### Quản lý biến động giá và khuyến mãi tại thời điểm đặt hàng

Vấn đề này tập trung vào việc lưu trữ dữ liệu lịch sử để đảm bảo tính nhất quán. Khi xem chi tiết đơn hàng, người dùng phải thấy chính xác mức giá, các chương trình giảm giá và chính sách thuế tại đúng thời điểm họ bấm nút đặt hàng, ngay cả khi sau đó giá sản phẩm trên hệ thống đã thay đổi hoặc chương trình khuyến mãi đã kết thúc. Bạn cần giải quyết cách lưu trữ thông tin sản phẩm "Snapshot" bên trong chi tiết đơn hàng thay vì chỉ liên kết đến bảng sản phẩm hiện tại.

### Truy vết lịch sử thay đổi trạng thái và dòng thời gian đơn hàng

Bài toán yêu cầu thiết kế một hệ thống nhật ký chi tiết ghi lại mọi biến động của đơn hàng từ lúc khởi tạo đến khi hoàn tất. Thông tin này bao gồm người thực hiện thay đổi là khách hàng hay nhân viên vận hành, thời điểm chính xác của thay đổi và lý do thay đổi nếu có. Giao diện chi tiết đơn hàng cần hiển thị một dòng thời gian trực quan giúp bộ phận hỗ trợ khách hàng có thể tra cứu nhanh chóng các bước xử lý đã diễn ra.

### Tích hợp thanh toán đa phương thức và trạng thái giao dịch

Đây là bài toán về việc xử lý dữ liệu tài chính phức tạp trong một đơn hàng. Một đơn hàng có thể được thanh toán bằng sự kết hợp của nhiều phương thức như điểm thưởng, thẻ quà tặng và phần còn lại thanh toán qua thẻ tín dụng. Chi tiết đơn hàng phải hiển thị rõ trạng thái của từng luồng thanh toán, mã giao dịch từ cổng thanh toán bên thứ ba và khả năng xử lý các tình huống hoàn tiền một phần cho một số sản phẩm cụ thể trong đơn.

### Hệ thống quản lý đổi trả và hoàn tiền tích hợp

Bài toán này mở rộng chi tiết đơn hàng sang quy trình sau bán hàng. Khi khách hàng muốn trả lại một vài món đồ trong đơn, hệ thống cần cập nhật trạng thái của riêng những sản phẩm đó mà không làm ảnh hưởng đến trạng thái chung của các sản phẩm còn lại. Việc thiết kế cần tính đến luồng dữ liệu giữa số lượng sản phẩm ban đầu, số lượng đã giao thành công và số lượng đang trong quá trình đổi trả hoặc đã hoàn tiền xong.

### Phân quyền hiển thị thông tin theo vai trò người dùng

Cùng một trang chi tiết đơn hàng nhưng dữ liệu hiển thị sẽ khác nhau tùy vào người đang truy cập. Khách hàng chỉ thấy các thông tin cơ bản và trạng thái vận chuyển, trong khi nhân viên kho thấy danh sách vị trí kệ hàng của sản phẩm, và nhân viên kế toán thấy chi tiết chiết khấu dòng tiền và lợi nhuận biên. Bài toán yêu cầu thiết kế API và cấu trúc dữ liệu sao cho việc kiểm soát quyền truy cập ở mức độ trường thông tin được thực hiện hiệu quả và bảo mật.

### Quản lý sản phẩm có cấu hình phức tạp và thuộc tính tùy chỉnh

Trong các ngành hàng như máy tính hoặc nội thất, một sản phẩm trong đơn hàng có thể đi kèm với nhiều tùy chọn cấu hình hoặc phụ kiện đi kèm. Bài toán đặt ra là làm thế nào để lưu trữ và hiển thị chi tiết các thuộc tính tùy chỉnh này trong đơn hàng mà không làm hỗn loạn cấu trúc bảng dữ liệu. Thông tin này phải đảm bảo đủ chi tiết để bộ phận sản xuất hoặc đóng gói nhìn vào là có thể thực hiện chính xác theo yêu cầu của khách hàng.

### Theo dõi vị trí vận chuyển theo thời gian thực và ước tính thời gian giao

Bài toán này nhấn mạnh vào việc tích hợp với các dịch vụ bản đồ và đơn vị vận chuyển bên thứ ba. Trong chi tiết đơn hàng, hệ thống cần cập nhật liên tục tọa độ hoặc các trạm luân chuyển mà gói hàng đã đi qua. Ngoài ra, dựa trên dữ liệu lịch sử và tình trạng giao thông, hệ thống phải tính toán và hiển thị thời gian dự kiến giao hàng chính xác đến từng giờ để tăng trải nghiệm cho người dùng cuối.
