# Backorder support

### Quản lý thứ tự ưu tiên trả hàng Backorder cho khách hàng VIP

Trong kịch bản này, một cửa hàng thời trang cao cấp cho phép tất cả khách hàng đặt hàng khi sản phẩm hết kho. Tuy nhiên, khi lô hàng mới được nhập về, hệ thống không thể chỉ áp dụng nguyên tắc ai đến trước được phục vụ trước. Bạn cần xử lý logic phân phối hàng dựa trên cấp độ thành viên của khách hàng và thời gian đặt hàng. Bài toán yêu cầu thiết kế cách lưu trữ hàng đợi chờ xử lý sao cho khi kho cập nhật số lượng dương, hệ thống tự động gán sản phẩm cho các đơn hàng Backorder theo trọng số ưu tiên đã định nghĩa.

### Theo dõi lộ trình nhập hàng từ nhà cung cấp cho đơn hàng chờ

Khi khách hàng đặt một sản phẩm đang hết kho, họ thường muốn biết chính xác bao lâu nữa hàng sẽ về. Bài toán này yêu cầu kết nối thực thể đơn hàng Backorder với các thực thể đơn mua hàng từ nhà cung cấp (Purchase Orders). Hệ thống phải tính toán được đơn hàng khách khách đang chờ thuộc về lô hàng nhập nào, trạng thái của lô hàng đó đang là đang sản xuất, đang vận chuyển hay đang kiểm kho, từ đó đưa ra ngày giao hàng dự kiến chính xác nhất cho khách.

### Tách đơn hàng và xử lý giao hàng từng phần

Một khách hàng mua một giỏ hàng gồm 5 món, trong đó có 3 món còn hàng và 2 món phải chờ Backorder. Bài toán đặt ra là hệ thống phải quyết định tách đơn hàng này thành các kiện hàng khác nhau như thế nào để tối ưu chi phí vận chuyển. Bạn cần thiết kế logic để khách hàng có thể lựa chọn: nhận những gì có sẵn trước (giao nhiều lần) hoặc đợi đầy đủ tất cả các món mới giao một lần (giao một lần). Việc này ảnh hưởng trực tiếp đến cách quản lý trạng thái đơn hàng và hóa đơn tài chính.

### Quản lý hạn ngạch Backorder tối đa để tránh rủi ro tồn kho ảo

Không phải sản phẩm nào cũng có thể cho phép đặt Backorder vô hạn. Bài toán này yêu cầu thiết kế một hệ thống quản lý ngưỡng (threshold). Ví dụ, dựa trên năng lực sản xuất của nhà máy, một sản phẩm chỉ được phép nhận tối đa 100 đơn hàng Backorder. Khi đạt đến con số này, nút đặt hàng phải tự động chuyển về trạng thái hết hàng hoàn toàn. Hệ thống cần xử lý được các tranh chấp dữ liệu khi có hàng nghìn người cùng nhấn đặt hàng tại giây cuối cùng của hạn ngạch.

### Tự động hủy đơn và hoàn tiền khi quá hạn cam kết nhập hàng

Trong các chiến dịch mở bán sản phẩm công nghệ, cửa hàng cam kết hàng sẽ về trong vòng 14 ngày. Nếu sau 14 ngày mà nhà cung cấp vẫn không giao hàng cho kho, hệ thống cần có cơ chế tự động quét các đơn hàng Backorder quá hạn, chuyển trạng thái sang hủy và kích hoạt quy trình hoàn tiền qua cổng thanh toán. Bài toán này tập trung vào việc thiết kế các tiến trình chạy ngầm và xử lý giao dịch tài chính an toàn khi quy trình cung ứng bị đứt gãy.

### Điều phối hàng hóa giữa các kho vật lý cho đơn hàng Backorder

Một chuỗi cửa hàng có nhiều kho ở các thành phố khác nhau. Khi khách hàng đặt Backorder tại kho A nhưng kho B lại vừa nhập hàng về, hệ thống cần một bộ quy tắc điều phối để quyết định: sẽ chuyển hàng từ kho B sang kho A để trả đơn, hay sẽ giao trực tiếp từ kho B cho khách. Bài toán này yêu cầu bạn thiết kế bảng ánh xạ vị trí địa lý, chi phí vận chuyển giữa các kho và trạng thái tồn kho ảo trên toàn hệ thống để tối ưu hóa tốc độ trả hàng.

### Thay đổi giá và khuyến mãi cho sản phẩm đặt chờ

Sản phẩm Backorder thường có thời gian chờ đợi lâu, và trong khoảng thời gian đó, giá thị trường hoặc các chương trình khuyến mãi có thể thay đổi. Bài toán yêu cầu thiết kế hệ thống sao cho giá trị đơn hàng được chốt tại thời điểm khách đặt mua, nhưng nếu đến lúc hàng về mà có chương trình giảm giá sâu hơn, hệ thống có thể áp dụng mã giảm giá bù đắp hoặc tặng voucher để giữ chân khách hàng. Điều này đòi hỏi cấu trúc dữ liệu linh hoạt để lưu trữ lịch sử giá và các áp dụng khuyến mãi bắc cầu.

### Thông báo đa kênh và xác nhận lại nhu cầu mua hàng

Sau một thời gian chờ đợi hàng Backorder dài ngày, nhu cầu của khách hàng có thể thay đổi. Bài toán đặt ra là khi hàng thực tế đã về đến kho, hệ thống không giao ngay mà gửi thông báo qua Email, SMS hoặc App Push để yêu cầu khách hàng nhấn xác nhận vẫn muốn nhận hàng trong vòng 24 giờ. Nếu khách không xác nhận, suất hàng đó sẽ được chuyển cho người tiếp theo trong hàng đợi. Bạn cần thiết kế trạng thái chờ xác nhận và các logic hết hạn phản hồi trong quy trình xử lý đơn hàng.
