# Delete product

### Hệ thống thương mại điện tử đa kho hàng

Trong mô hình này, một sản phẩm có thể tồn tại ở nhiều kho hàng khác nhau với số lượng tồn kho riêng biệt. Bài toán đặt ra là khi người quản trị muốn xóa một sản phẩm, hệ thống cần kiểm tra xem sản phẩm đó có còn tồn kho ở bất kỳ chi nhánh nào không hoặc có đang nằm trong vận đơn nào đang giao hay không. Nếu sản phẩm đã từng phát sinh đơn hàng trong quá khứ, việc xóa hoàn toàn sẽ làm hỏng báo cáo doanh thu, do đó bạn cần thiết kế cách để sản phẩm biến mất khỏi gian hàng nhưng vẫn lưu lại dấu vết trong lịch sử giao dịch.

### Sàn giao dịch sản phẩm cũ C2C

Trên các nền tảng cho phép người dùng cá nhân đăng bán đồ cũ, người bán thường có thói quen xóa tin đăng ngay sau khi bán xong hoặc khi đổi ý. Thách thức ở đây là sản phẩm có thể đã được hàng nghìn người dùng khác lưu vào danh sách yêu thích hoặc đang nằm trong giỏ hàng của họ. Khi sản phẩm bị xóa hoàn toàn khỏi database, hệ thống cần xử lý trải nghiệm người dùng tại các màn hình đó sao cho không bị lỗi giao diện và thông báo khéo léo rằng sản phẩm không còn tồn tại.

### Quản lý thực đơn nhà hàng theo combo

Trong ngành F&B, một nguyên liệu hoặc món lẻ có thể là thành phần của nhiều combo khác nhau. Ví dụ, nếu bạn xóa món khoai tây chiên khỏi hệ thống, các combo như phần ăn gia đình hoặc phần ăn trẻ em chứa khoai tây chiên sẽ bị thiếu thành phần. Bài toán yêu cầu thiết kế database sao cho khi xóa một sản phẩm gốc, hệ thống phải truy quét tất cả các định mức nguyên liệu và cấu trúc combo liên quan để cảnh báo hoặc tự động cập nhật trạng thái của các bộ sản phẩm đó.

### Hệ thống bán vé máy bay hoặc sự kiện

Sản phẩm ở đây là các ghế ngồi hoặc suất diễn có thời gian cụ thể. Khi một chuyến bay bị hủy và cần xóa khỏi hệ thống bán vé, việc xóa không đơn thuần là mất đi một dòng dữ liệu mà kéo theo hệ quả về hoàn tiền và điều chuyển hành khách. Bạn cần thiết kế một cơ chế sao cho dữ liệu về sản phẩm bị xóa vẫn có thể truy xuất để thực hiện các nghiệp vụ hậu mãi nhưng không còn xuất hiện trong kết quả tìm kiếm chuyến bay mới.

### Quản lý thư viện ảnh và tài nguyên số

Đối với các nền tảng bán ảnh stock hoặc tài liệu số, sản phẩm thường đi kèm với các tệp tin có dung lượng lớn lưu trữ trên cloud. Khi lệnh xóa sản phẩm được thực thi, hệ thống không chỉ xóa bản ghi trong SQL mà còn phải kích hoạt các tiến trình ngầm để dọn dẹp tài nguyên vật lý trên server lưu trữ nhằm tối ưu chi phí. Việc thiết kế cần đảm bảo tính nhất quán giữa database và storage, tránh trường hợp bản ghi đã mất nhưng file vẫn tồn tại gây lãng phí.

### Hệ thống đấu giá trực tuyến

Sản phẩm trong hệ thống đấu giá có vòng đời rất đặc thù. Nếu một sản phẩm đang trong phiên đấu giá sôi nổi mà bị xóa đột ngột do vi phạm chính sách, hệ thống phải xử lý đồng thời việc hủy các lệnh đặt thầu, hoàn trả tiền đặt cọc cho người tham gia và gửi thông báo thời gian thực. Cấu trúc dữ liệu phải cho phép phân tách giữa thông tin sản phẩm và lịch sử đấu giá để phục vụ việc khiếu nại về sau dù sản phẩm đã bị gỡ bỏ hoàn toàn.

### Quản lý dược phẩm và thiết bị y tế

Sản phẩm y tế thường có số lô và hạn sử dụng gắn liền. Khi một lô hàng bị lỗi và cần xóa khỏi danh mục lưu hành, hệ thống phải đảm bảo rằng không một nhân viên nào có thể truy xuất sản phẩm đó cho các đơn thuốc mới. Tuy nhiên, vì lý do pháp lý và an toàn người bệnh, mọi thông tin về sản phẩm đã xóa phải được lưu trữ trong một phân vùng dữ liệu lưu trữ riêng biệt để phục vụ việc tra cứu lịch sử điều trị trong nhiều năm.

### Hệ thống Dropshipping và đồng bộ nhà cung cấp

Trong mô hình này, sản phẩm được lấy dữ liệu từ kho của nhà cung cấp bên thứ ba. Khi nhà cung cấp xóa sản phẩm trên hệ thống của họ, hệ thống của bạn phải tự động nhận diện và thực hiện lệnh xóa tương ứng trên các gian hàng của mình thông qua Webhook hoặc API. Bài toán thiết kế ở đây là làm sao xử lý độ trễ dữ liệu và đảm bảo việc xóa hàng loạt hàng nghìn sản phẩm không gây treo hệ thống hoặc làm gián đoạn trải nghiệm của khách mua hàng.
