# Buy X get Y

### Mua số lượng cố định tặng sản phẩm cùng loại

Cửa hàng thời trang chạy chương trình mua 2 tặng 1 áp dụng cho tất cả các loại áo thun. Khi khách hàng thêm vào giỏ hàng đúng 3 chiếc áo thun bất kỳ, hệ thống sẽ tự động xác định chiếc áo có giá trị thấp nhất trong số đó để giảm giá về mức không đồng. Bài toán này yêu cầu hệ thống phải có khả năng quét qua danh sách sản phẩm trong giỏ hàng, nhóm chúng theo loại và thực hiện logic tính toán dựa trên đơn giá của từng món đồ.

### Mua sản phẩm chính tặng kèm sản phẩm phụ kiện

Một cửa hàng đồ công nghệ thiết lập quy tắc khi khách hàng mua một chiếc điện thoại thông minh thuộc danh mục cao cấp, họ sẽ được tặng kèm một bao da hoặc một miếng dán cường lực. Tuy nhiên, sản phẩm tặng kèm không được tự động thêm vào mà khách hàng phải chủ động chọn từ một danh sách quà tặng cho trước. Hệ thống cần quản lý mối quan hệ giữa sản phẩm điều kiện và danh sách quà tặng khả dụng tương ứng để hiển thị trên giao diện giỏ hàng.

### Mua theo định mức doanh số để nhận ưu đãi

Siêu thị áp dụng chương trình khuyến mãi khi tổng giá trị các sản phẩm thuộc ngành hàng hóa mỹ phẩm đạt từ năm trăm nghìn đồng trở lên, khách hàng sẽ được giảm giá năm mươi phần trăm cho sản phẩm sữa tắm tùy chọn. Bài toán này đòi hỏi hệ thống phải tính toán tổng phụ của một nhóm sản phẩm cụ thể trong giỏ hàng trước khi kích hoạt điều kiện giảm giá cho một sản phẩm khác không nằm trong nhóm điều kiện ban đầu.

### Chương trình mua X tặng Y theo bội số

Để thúc đẩy bán sỉ, một đại lý sữa áp dụng quy tắc mua 12 hộp sữa sẽ được tặng thêm 2 hộp cùng loại. Điểm đặc biệt là ưu đãi này phải được nhân lên theo bội số, nghĩa là nếu khách mua 24 hộp thì được tặng 4 hộp, mua 36 hộp được tặng 6 hộp. Database và API cần xử lý được việc tự động tính toán số lượng quà tặng dựa trên số lượng sản phẩm X mà không cần thiết lập thủ công từng mốc số lượng.

### Mua gói combo sản phẩm để nhận quà tặng chung

Nhãn hàng mỹ phẩm tạo ra một bộ sưu tập gồm sữa rửa mặt, kem dưỡng và serum. Khách hàng chỉ nhận được một túi trang điểm cao cấp khi và chỉ khi trong giỏ hàng có đủ cả ba sản phẩm cụ thể này. Nếu thiếu bất kỳ sản phẩm nào trong bộ ba, quà tặng sẽ bị gỡ bỏ. Bài toán này kiểm tra khả năng thiết kế logic ràng buộc đa sản phẩm và kiểm tra điều kiện giỏ hàng theo thời gian thực mỗi khi có sự thay đổi về số lượng.

### Giới hạn số lượng quà tặng trên mỗi đơn hàng

Trong chương trình mua 1 tặng 1 cho dòng nước hoa mới, doanh nghiệp quy định mỗi đơn hàng chỉ được nhận tối đa 2 chai nước hoa tặng kèm dù khách hàng có mua 5 hay 10 chai sản phẩm chính. Hệ thống cần có một cơ chế kiểm soát giới hạn trên của quà tặng ngay tại bước áp dụng khuyến mãi để tránh thất thoát hàng hóa trong các đơn hàng mua số lượng lớn.

### Phân bổ giảm giá cho sản phẩm tặng khi trả hàng

Một cửa hàng áp dụng mua 3 tính tiền 2, tức là chiếc áo rẻ nhất được giảm giá một trăm phần trăm. Tuy nhiên, để tránh việc khách hàng lợi dụng trả lại 2 chiếc áo đắt tiền và giữ lại chiếc áo miễn phí, hệ thống phải phân bổ số tiền giảm giá của chiếc áo thứ 3 chia đều cho cả 3 chiếc áo dựa trên tỷ lệ giá trị. Đây là bài toán quan trọng trong thiết kế database liên quan đến dòng tiền và quản lý hoàn trả sau bán hàng.

### Mua sản phẩm bất kỳ trong danh mục để nhận quà theo lựa chọn

Chương trình khuyến mãi cho phép khách hàng mua bất kỳ 2 sản phẩm nào trong danh mục đồ gia dụng để được tặng 1 sản phẩm trong danh mục đồ tiện ích dưới mười nghìn đồng. Do số lượng sản phẩm trong mỗi danh mục có thể lên đến hàng nghìn, việc thiết kế database phải tối ưu hóa cách lưu trữ điều kiện khuyến mãi theo danh mục thay vì lưu danh sách ID sản phẩm cụ thể để dễ dàng quản trị và mở rộng.
