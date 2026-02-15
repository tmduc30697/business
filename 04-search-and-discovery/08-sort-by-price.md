# Sort by price

### Sàn thương mại điện tử đa biến thể

Trong bài toán này, một sản phẩm thường có nhiều phiên bản khác nhau như kích cỡ, màu sắc hoặc dung lượng bộ nhớ với các mức giá khác nhau. Khi người dùng chọn sắp xếp theo giá tăng dần trên trang danh mục, hệ thống cần xác định xem sẽ lấy giá thấp nhất của biến thể đại diện hay giá của phiên bản mặc định để hiển thị. Thách thức nằm ở việc truy vấn hiệu quả từ bảng sản phẩm sang bảng biến thể mà không làm chậm tốc độ tải trang khi có hàng triệu bản ghi.

### Hệ thống đặt phòng khách sạn theo mùa

Giá phòng khách sạn không cố định mà thay đổi theo ngày nhận phòng, ngày trả phòng và các chương trình khuyến mãi theo mùa. Khi khách hàng tìm kiếm và sắp xếp theo giá, hệ thống phải tính toán giá thực tế dựa trên khoảng thời gian khách chọn thay vì chỉ lấy giá niêm yết trong cơ sở dữ liệu. Điều này đòi hỏi thiết kế logic API phức tạp để tính toán tổng tiền và sắp xếp kết quả trả về trong thời gian thực.

### Trang web đấu giá trực tuyến

Đối với một nền tảng đấu giá, mức giá hiện tại của sản phẩm thay đổi liên tục sau mỗi lượt đặt giá của người dùng. Việc sắp xếp theo giá yêu cầu hệ thống phải luôn cập nhật mức giá cao nhất hiện tại hoặc mức giá khởi điểm tùy theo bộ lọc. Bạn cần cân nhắc cách đồng bộ dữ liệu giữa bảng sản phẩm và bảng lịch sử đấu giá để đảm bảo thứ tự sắp xếp luôn chính xác tại thời điểm người dùng tải trang.

### Nền tảng môi giới bất động sản

Giá bất động sản thường được lưu trữ dưới nhiều đơn vị khác nhau như tổng giá trị căn nhà hoặc giá trên mỗi mét vuông. Khi người dùng thực hiện lệnh sắp xếp, hệ thống cần thực hiện các phép quy đổi đơn vị ngay trong câu lệnh truy vấn để đưa về cùng một mặt bằng so sánh. Ngoài ra, một số tin đăng có thể để giá thỏa thuận thay vì con số cụ thể, gây khó khăn cho việc xác định vị trí của chúng trong danh sách sắp xếp.

### Ứng dụng giao đồ ăn với phí vận chuyển

Trong các ứng dụng giao đồ ăn, người dùng thường quan tâm đến tổng chi phí bao gồm giá món ăn và phí giao hàng. Phí giao hàng lại thay đổi tùy vào khoảng cách từ nhà hàng đến vị trí người dùng. Khi người dùng chọn sắp xếp theo giá từ thấp đến cao, hệ thống không chỉ lấy giá thực đơn mà còn phải tính toán phí vận chuyển động để đưa ra thứ tự ưu tiên chính xác nhất cho người dùng tại vị trí đó.

### Quản lý kho hàng phân phối dược phẩm

Trong ngành dược, cùng một loại thuốc có thể được nhập từ nhiều lô hàng khác nhau với đơn giá nhập và hạn sử dụng khác nhau. Khi nhân viên kho tìm kiếm để xuất hàng, họ cần sắp xếp theo giá nhập hoặc giá bán lẻ tùy theo chiến lược kinh doanh. Bài toán này yêu cầu thiết kế database có khả năng quản lý tồn kho theo lô và xử lý logic sắp xếp dựa trên các thuộc tính của từng lô hàng cụ thể thay vì chỉ dừng lại ở mã sản phẩm chung.

### Hệ thống so sánh giá vé máy bay

Vé máy bay có đặc thù là giá thay đổi theo hạng ghế và các dịch vụ đi kèm như hành lý ký gửi hoặc suất ăn. Một yêu cầu sắp xếp giá tăng dần thường phải xử lý dữ liệu từ nhiều hãng hàng không khác nhau với các cấu trúc thuế phí khác biệt. Việc thiết kế API cho bài toán này cần đảm bảo tính nhất quán giữa giá hiển thị ban đầu và giá cuối cùng sau khi đã cộng đầy đủ các khoản thuế phí bắt buộc.

### Chợ mua bán xe cũ từ nhiều nguồn

Trên các trang tin rao vặt xe cũ, người bán có thể đăng tin với nhiều loại tiền tệ khác nhau như đồng nội tệ hoặc ngoại tệ. Để tính năng sắp xếp giá hoạt động chuẩn xác, hệ thống cần tích hợp một bảng tỷ giá hối đoái được cập nhật thường xuyên. Khi thực hiện truy vấn sắp xếp, cơ sở dữ liệu phải chuyển đổi tất cả mức giá về một loại tiền tệ cơ sở để đảm bảo thứ tự hiển thị không bị sai lệch do sự khác biệt về đơn vị tiền tệ.
