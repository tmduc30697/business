# Related product

### Gợi ý thủ công theo bộ sưu tập của người quản trị

Trong các trang web thời trang cao cấp, người quản lý nội dung muốn tự tay chọn lựa các sản phẩm đi kèm để tạo thành một bộ trang phục hoàn chỉnh (lookbook). Ví dụ, khi khách hàng xem một chiếc áo sơ mi, hệ thống phải hiển thị chính xác chiếc quần tây và đôi giày mà người mẫu đang mặc trong ảnh. Bài toán này yêu cầu một cơ chế thiết lập mối quan hệ hai chiều hoặc một chiều giữa các mã sản phẩm cụ thể và khả năng sắp xếp thứ tự hiển thị của chúng theo ý đồ marketing.

### Tự động hiển thị sản phẩm cùng danh mục và thương hiệu

Để tăng tỷ lệ chuyển đổi, hệ thống cần tự động tìm kiếm các sản phẩm có cùng đặc điểm với sản phẩm hiện tại mà không cần sự can thiệp của con người. Nếu người dùng đang xem một chiếc laptop Gaming của hãng Dell, phần sản phẩm liên quan nên ưu tiên hiển thị các laptop Gaming khác trong cùng phân khúc giá hoặc các mẫu máy khác cùng dòng Alienware. Bài toán này đòi hỏi việc truy vấn dữ liệu dựa trên các thuộc tính phân loại và nhãn hàng để đảm bảo tính đồng nhất.

### Gợi ý phụ kiện đi kèm dựa trên lịch sử mua hàng

Đối với các thiết bị điện tử, việc bán kèm phụ kiện là rất quan trọng. Khi khách hàng xem một chiếc máy ảnh, hệ thống cần gợi ý ống kính, thẻ nhớ hoặc túi đựng tương thích. Dữ liệu này được trích xuất từ hành vi của những người dùng trước đó, cụ thể là những sản phẩm thường được mua cùng nhau trong một đơn hàng. Bạn cần giải quyết vấn đề lưu trữ các cặp sản phẩm có tần suất xuất hiện chung cao và cập nhật danh sách này định kỳ.

### Sản phẩm thay thế khi hết hàng

Khi một sản phẩm cụ thể rơi vào trạng thái hết hàng, trang chi tiết sản phẩm cần tập trung hiển thị các lựa chọn thay thế gần như tương đồng về chức năng và giá trị để giữ chân khách hàng. Ví dụ, nếu một mẫu tủ lạnh dung tích 300 lít của Samsung hết hàng, hệ thống phải ngay lập tức đề xuất các mẫu tủ lạnh 300 lít của LG hoặc Panasonic. Điều này yêu cầu một logic chấm điểm độ tương đồng giữa các sản phẩm dựa trên thông số kỹ thuật.

### Hệ thống gợi ý cá nhân hóa theo hành vi người dùng

Thay vì hiển thị sản phẩm liên quan giống nhau cho mọi người, hệ thống sẽ điều chỉnh dựa trên lịch sử xem trang và sở thích của từng cá nhân. Nếu hai người cùng xem một chiếc điện thoại, người thường xuyên mua đồ giá rẻ sẽ thấy các phụ kiện giá thấp, trong khi người hay mua đồ cao cấp sẽ thấy các thiết bị đeo thông minh đắt tiền. Bài toán này liên quan đến việc lưu trữ hành vi người dùng theo thời gian thực và tích hợp kết quả từ các bộ lọc gợi ý vào trang sản phẩm.

### Quản lý phiên bản và màu sắc của cùng một dòng sản phẩm

Một sản phẩm có thể có nhiều biến thể như màu sắc, kích cỡ hoặc bộ nhớ khác nhau. Trong phần sản phẩm liên quan, người bán muốn hiển thị các lựa chọn màu sắc khác của chính mẫu đó để khách hàng dễ dàng chuyển đổi. Thách thức ở đây là làm thế nào để phân biệt giữa sản phẩm tương tự (cùng loại) và sản phẩm biến thể (cùng gốc) trong sơ đồ cơ sở dữ liệu để tránh hiển thị trùng lặp hoặc gây rối mắt.

### Gợi ý sản phẩm dựa trên lượt xem chéo trong phiên làm việc

Trong một phiên truy cập, nếu người dùng liên tục chuyển qua lại giữa các mẫu xe đạp địa hình và xe đạp đường phố, hệ thống cần nhận diện được sự phân vân này để hiển thị các mẫu xe lai (hybrid) ở phần sản phẩm liên quan. Bài toán này tập trung vào việc xử lý dữ liệu dòng sự kiện (event stream) và cập nhật danh sách gợi ý một cách linh động theo diễn biến tâm lý khách hàng ngay trong phiên làm việc đó.

### Tối ưu hóa sản phẩm liên quan theo vùng địa lý và kho bãi

Để đảm bảo thời gian giao hàng nhanh nhất, hệ thống chỉ nên hiển thị các sản phẩm liên quan hiện đang có sẵn tại kho hàng gần vị trí của người dùng nhất. Nếu một sản phẩm tương tự rất phù hợp nhưng lại ở kho khác tỉnh thành, nó sẽ bị giảm ưu tiên hiển thị hoặc không xuất hiện. Bài toán này yêu cầu sự kết hợp giữa dữ liệu tồn kho theo vị trí và thông tin địa lý của người dùng khi truy vấn sản phẩm.

### Hiển thị sản phẩm liên quan theo các chương trình khuyến mãi chéo

Bộ phận vận hành muốn đẩy mạnh doanh số cho một nhãn hàng mới bằng cách gắn nó vào phần sản phẩm liên quan của các mặt hàng đang bán chạy nhất (best-seller). Ngay cả khi chúng không hoàn toàn liên quan về tính năng, chúng vẫn được xuất hiện do có chiến dịch marketing đi kèm. Bạn cần thiết kế một hệ thống quản lý chiến dịch có khả năng ghi đè hoặc xen kẽ các sản phẩm được tài trợ vào danh sách gợi ý tự nhiên.

### Theo dõi hiệu quả và tỷ lệ nhấp vào sản phẩm liên quan

Sau khi hiển thị các sản phẩm liên quan, hệ thống cần ghi lại dữ liệu về việc khách hàng có nhấn vào xem hay không và liệu họ có bỏ vào giỏ hàng từ đó không. Dữ liệu này sau đó được dùng để tự động điều chỉnh thứ tự hiển thị: sản phẩm nào được click nhiều sẽ được đẩy lên đầu, sản phẩm nào không hiệu quả sẽ bị loại bỏ. Bài toán này đòi hỏi thiết kế hệ thống logging và feedback loop để tối ưu hóa hiệu suất hiển thị một cách tự động.
