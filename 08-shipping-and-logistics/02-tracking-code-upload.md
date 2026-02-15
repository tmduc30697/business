# Tracking code upload

### Quản lý mã vận đơn cho đơn hàng được tách thành nhiều kiện

Trong thực tế kinh doanh, một đơn hàng khách đặt có thể bao gồm nhiều sản phẩm cồng kềnh hoặc nằm ở các kho khác nhau. Điều này dẫn đến việc một đơn hàng (Order) không chỉ có một mã vận đơn duy nhất mà phải được chia thành nhiều gói hàng (Packages). Hệ thống cần cho phép cập nhật từng mã vận đơn riêng biệt cho mỗi gói hàng, đồng thời theo dõi trạng thái giao hàng của từng phần để thông báo cho khách hàng chính xác kiện hàng nào đang đến đâu.

### Đồng bộ mã vận đơn tự động từ API của đơn vị vận chuyển

Thay vì nhập tay, các hệ thống lớn thường kết nối trực tiếp với các đơn vị vận chuyển như Giao Hàng Nhanh, Viettel Post hoặc FedEx. Khi seller bấm xác nhận gửi hàng, hệ thống phải gọi API sang bên vận chuyển để lấy mã vận đơn và tự động lưu ngược lại vào cơ sở dữ liệu. Bài toán này đòi hỏi xử lý các kịch bản như lỗi kết nối API, mã vận đơn bị trùng lặp hoặc việc thay đổi đơn vị vận chuyển vào phút chót sau khi đã lấy mã.

### Cập nhật mã vận đơn hàng loạt qua file Excel

Đối với các seller có hàng trăm đơn hàng mỗi ngày, việc nhập từng mã là không khả thi. Họ thường xuất danh sách đơn hàng ra file Excel, điền mã vận đơn sau khi đóng gói xong rồi tải ngược lên hệ thống. Hệ thống cần có cơ chế kiểm tra tính hợp lệ của dữ liệu trong file, khớp đúng mã đơn hàng với mã vận đơn tương ứng, xử lý các trường hợp mã đơn hàng không tồn tại hoặc đơn hàng đã có mã vận đơn từ trước đó.

### Lịch sử thay đổi và điều chỉnh mã vận đơn

Trong quá trình vận hành, seller có thể nhập nhầm mã vận đơn hoặc bưu cục yêu cầu đổi mã mới do sự cố nhãn dán. Hệ thống không được đơn giản là ghi đè dữ liệu cũ mà cần lưu lại lịch sử thay đổi bao gồm mã cũ, mã mới, thời gian thay đổi và người thực hiện. Điều này giúp bộ phận chăm sóc khách hàng có thể tra cứu lại khi có tranh chấp hoặc khi khách hàng thắc mắc tại sao mã vận đơn của họ lại bị thay đổi liên tục.

### Theo dõi hành trình đơn hàng từ mã vận đơn của bên thứ ba

Sau khi mã vận đơn được upload, hệ thống không chỉ lưu trữ nó như một đoạn văn bản mà còn phải định kỳ kiểm tra trạng thái từ phía đơn vị vận chuyển. Bài toán đặt ra là thiết kế một worker hoặc dịch vụ chạy ngầm để lấy dữ liệu hành trình từ phía vận chuyển rồi cập nhật vào bảng trạng thái trong database của mình. Việc này giúp khách hàng có thể xem trực tiếp lộ trình đơn hàng ngay trên app của seller mà không cần sang trang web của bên vận chuyển.

### Quản lý mã vận đơn cho mô hình Dropshipping và Cross-border

Trong mô hình này, hàng hóa được gửi từ nhà cung cấp nước ngoài về kho trung chuyển rồi mới đến tay khách hàng. Một đơn hàng có thể có hai loại mã vận đơn: mã vận đơn quốc tế và mã vận đơn nội địa. Hệ thống cần cấu trúc dữ liệu sao cho có thể liên kết hai loại mã này với nhau, giúp seller quản lý được toàn bộ chuỗi cung ứng và biết được thời điểm chính xác khi nào hàng về đến biên giới để chuyển đổi thông tin vận đơn cho khách.

### Cơ chế webhook thông báo trạng thái vận đơn cho đối tác

Khi mã vận đơn được cập nhật hoặc có sự thay đổi về trạng thái giao hàng, các hệ thống vệ tinh khác như hệ thống kế toán hoặc hệ thống CRM cần nhận được thông tin ngay lập tức. Thay vì các hệ thống này phải liên tục truy vấn database, hệ thống quản lý vận đơn cần thiết kế một cơ chế Webhook để chủ động đẩy thông báo sang cho các bên liên quan mỗi khi có sự kiện upload hoặc cập nhật mã vận đơn mới thành công.

### Ràng buộc quy trình thanh toán dựa trên mã vận đơn

Đối với các sàn thương mại điện tử, việc upload mã vận đơn là điều kiện tiên quyết để chuyển trạng thái đơn hàng từ Đang xử lý sang Đang giao hàng. Điều này ảnh hưởng trực tiếp đến dòng tiền và thời gian đối soát tiền COD. Hệ thống cần thiết kế các ràng buộc logic chặt chẽ để đảm bảo không có việc gian lận cập nhật mã giả nhằm mục đích rút tiền sớm, cũng như tự động tính toán thời gian dự kiến nhận hàng dựa trên thời điểm upload mã.
