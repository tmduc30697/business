# Shipping method selection

### Tính toán phí vận chuyển dựa trên khoảng cách và khối lượng quy đổi

Trong thực tế, phí vận chuyển không chỉ dựa vào cân nặng thực tế mà còn dựa vào kích thước cồng kềnh của kiện hàng. Bài toán yêu cầu hệ thống phải lưu trữ được các công thức tính trọng lượng quy đổi từ chiều dài, chiều rộng, chiều cao. Sau đó, hệ thống đối chiếu với bảng giá của từng đơn vị vận chuyển theo từng vùng miền hoặc khoảng cách giữa kho hàng của người bán và địa chỉ của người mua để đưa ra mức phí chính xác nhất cho từng loại hình dịch vụ như giao hàng nhanh hay giao hàng tiết kiệm.

### Quản lý danh mục phương thức vận chuyển theo khu vực địa lý

Nhiều đơn vị vận chuyển chỉ hoạt động trong một số tỉnh thành nhất định hoặc có thế mạnh riêng tại các vùng sâu vùng xa. Bài toán đặt ra là làm thế nào để thiết lập cấu hình cho phép một phương thức vận chuyển (ví dụ: Hỏa tốc) chỉ xuất hiện khi địa chỉ người mua và người bán cùng nằm trong một quận/huyện hoặc một thành phố. Ngược lại, đối với các đơn hàng liên tỉnh, hệ thống phải tự động lọc bỏ các tùy chọn không khả dụng và chỉ hiển thị các phương thức vận chuyển đường bộ hoặc đường hàng không phù hợp.

### Tối ưu hóa hiển thị đơn vị vận chuyển dựa trên đánh giá và hiệu suất

Người bán thường muốn ưu tiên các đơn vị vận chuyển có tỷ lệ giao hàng thành công cao và thời gian lấy hàng nhanh. Bài toán yêu cầu thiết kế một hệ thống đánh giá hiệu suất cho từng phương thức vận chuyển của từng nhà cung cấp. Dựa trên dữ liệu lịch sử về thời gian giao hàng thực tế và phản hồi của khách hàng, hệ thống sẽ ưu tiên hiển thị các phương thức có điểm uy tín cao lên đầu danh sách lựa chọn của người mua để tăng trải nghiệm người dùng và giảm tỷ lệ hoàn hàng.

### Áp dụng quy tắc miễn phí vận chuyển và mã giảm giá vận chuyển

Hệ thống cần xử lý các kịch bản khuyến mãi phức tạp như miễn phí vận chuyển cho đơn hàng đạt giá trị tối thiểu hoặc giảm tối đa một số tiền nhất định cho một phương thức vận chuyển cụ thể. Bài toán này đòi hỏi thiết kế database có khả năng liên kết giữa giá trị đơn hàng, loại sản phẩm và các chiến dịch marketing. Khi người dùng chọn phương thức vận chuyển, hệ thống phải tính toán lại tổng tiền cuối cùng dựa trên việc áp dụng các điều kiện giảm giá đang có hiệu lực tại thời điểm đó.

### Tích hợp và điều phối đa đối tác vận chuyển thứ ba

Thay vì tự giao hàng, người bán thường sử dụng các đối tác như Giao Hàng Nhanh, Viettel Post hay J&T Express qua API. Bài toán thực tế là thiết kế một lớp trung gian có thể ánh xạ các phương thức vận chuyển nội bộ của hệ thống sang các mã dịch vụ tương ứng của từng đối tác. Hệ thống phải lưu trữ thông tin tài khoản tích hợp (API Key, Token) của từng người bán để khi người mua chọn một phương thức cụ thể, hệ thống có thể ngay lập tức gửi yêu cầu tạo đơn hàng và lấy mã vận đơn từ phía đối tác.

### Xử lý các mặt hàng đặc thù và hạn chế vận chuyển

Một số loại hàng hóa như chất lỏng, pin, hoặc hàng dễ vỡ thường bị từ chối bởi các phương thức vận chuyển hỏa tốc bằng xe máy hoặc vận chuyển hàng không. Bài toán yêu cầu hệ thống phải phân loại sản phẩm theo thuộc tính vận chuyển. Khi người mua có một sản phẩm đặc thù trong giỏ hàng, hệ thống sẽ tự động quét qua danh sách sản phẩm và loại bỏ tất cả các phương thức vận chuyển không hỗ trợ loại hàng hóa đó, ngay cả khi khu vực địa lý của khách hàng hoàn toàn thỏa mãn điều kiện.

### Quản lý thời gian lấy hàng và cam kết thời gian giao hàng

Thời gian giao hàng dự kiến là yếu tố quan trọng ảnh hưởng đến quyết định mua hàng. Bài toán này yêu cầu hệ thống phải tính toán được thời gian dự kiến dựa trên lịch làm việc của đơn vị vận chuyển, giờ chốt đơn của người bán và các ngày nghỉ lễ. Hệ thống cần hiển thị thông tin cụ thể như: nhận hàng vào thứ Tư nếu đặt ngay bây giờ. Điều này đòi hỏi database phải lưu trữ được lịch trình vận hành chi tiết của từng phương thức vận chuyển và thời gian xử lý đơn hàng của người bán.

### Tự động phân bổ đơn vị vận chuyển cho các đơn hàng lớn

Đối với các hệ thống sàn thương mại điện tử lớn, đôi khi người dùng không chọn đích danh đơn vị vận chuyển mà chỉ chọn loại dịch vụ như Nhanh hoặc Tiết kiệm. Lúc này, bài toán của hệ thống là phải tự động chọn ra nhà vận chuyển có giá cước thấp nhất hoặc có sẵn tài xế trong khu vực để tối ưu chi phí cho sàn. Quy trình này đòi hỏi một cơ chế thiết lập trọng số và các quy tắc ưu tiên linh hoạt để hệ thống có thể tự đưa ra quyết định mà không cần sự can thiệp thủ công từ nhân viên.
