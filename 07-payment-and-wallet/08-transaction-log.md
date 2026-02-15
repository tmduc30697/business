# Transaction log

### Truy vết nguồn gốc dòng tiền và tính nhất quán dữ liệu

Trong một hệ thống ví điện tử, một giao dịch thanh toán đơn hàng có thể kéo theo nhiều biến động số dư khác nhau như trừ tiền khách hàng, cộng tiền cho người bán, và trừ phí dịch vụ. Bài toán đặt ra là làm thế nào để thiết kế lịch sử giao dịch sao cho khi nhìn vào một mã giao dịch duy nhất, hệ thống có thể truy xuất ngược lại toàn bộ các dòng tiền liên quan của tất cả các bên. Bạn cần đảm bảo rằng tổng số tiền nạp vào và rút ra luôn cân bằng, không có tình trạng tiền tự sinh ra hoặc mất đi do lỗi hệ thống khi thực hiện các tác vụ ghi log đồng thời.

### Xử lý hoàn tiền một phần cho đơn hàng nhiều sản phẩm

Khách hàng thực hiện thanh toán một đơn hàng gồm nhiều món đồ khác nhau nhưng sau đó chỉ muốn hoàn trả một món duy nhất do bị lỗi. Hệ thống lúc này phải đối mặt với việc xử lý hoàn tiền một phần dựa trên giao dịch gốc đã thực hiện trước đó. Thách thức ở đây là việc ghi log phải thể hiện rõ mối liên kết giữa giao dịch hoàn tiền và giao dịch thanh toán ban đầu, đồng thời phải kiểm soát được giới hạn số tiền hoàn lại không được vượt quá số tiền thực tế đã chi trả sau khi trừ các loại khuyến mãi.

### Hệ thống đối soát tự động với ngân hàng và đối tác

Khi người dùng nạp tiền từ ngân hàng vào ví, thông tin giao dịch tồn tại ở cả hai hệ thống là ngân hàng và ví điện tử. Bài toán yêu cầu thiết kế một cơ chế log sao cho mỗi kỳ đối soát cuối ngày, hệ thống có thể tự động so khớp mã tham chiếu từ phía ngân hàng với mã giao dịch nội bộ. Việc này nhằm phát hiện các trường hợp giao dịch thành công ở phía ngân hàng nhưng ví chưa cộng tiền cho khách hoặc ngược lại, giúp bộ phận vận hành có đủ dữ liệu để xử lý khiếu nại.

### Phân bổ hoa hồng đa cấp cho đại lý bán hàng

Một hệ thống thanh toán có cơ chế chia sẻ doanh thu cho các bên trung gian hoặc đại lý theo nhiều cấp độ khác nhau. Khi một giao dịch thanh toán thành công, hệ thống cần tự động tính toán và ghi nhận các dòng log hoa hồng cho đại lý cấp một, đại lý cấp hai và các bên liên quan. Bạn cần thiết kế cấu trúc dữ liệu sao cho việc truy vấn tổng thu nhập của một đại lý trong một khoảng thời gian được thực hiện nhanh chóng mà không cần phải duyệt qua toàn bộ bảng log khổng lồ của hệ thống.

### Quản lý hạn mức giao dịch và cảnh báo gian lận

Để đảm bảo an toàn tài chính, hệ thống cần kiểm soát hạn mức nạp và rút tiền của người dùng theo ngày hoặc theo tháng. Bài toán đặt ra là dựa trên lịch sử giao dịch đã ghi lại, làm thế nào để thiết kế một quy trình kiểm tra điều kiện trước khi thực hiện giao dịch mới một cách tối ưu nhất. Ngoài ra, dữ liệu log cần cung cấp đủ thông tin về tần suất và hành vi bất thường như nạp rút liên tục số tiền lớn trong thời gian ngắn để hệ thống có thể gắn cờ cảnh báo rủi ro kịp thời.

### Hỗ trợ đa tiền tệ và biến động tỷ giá khi thanh toán quốc tế

Người dùng có thể nạp tiền bằng đơn vị tiền tệ này nhưng thực hiện thanh toán cho nhà cung cấp ở quốc gia khác bằng đơn vị tiền tệ khác. Hệ thống ghi log lúc này không chỉ lưu số tiền giao dịch mà còn phải lưu lại tỷ giá tại thời điểm đó, loại tiền tệ gốc và số tiền sau quy đổi. Điều này giúp cho việc báo cáo tài chính và hiển thị lịch sử giao dịch cho người dùng trở nên minh bạch, tránh tranh chấp khi tỷ giá thị trường thay đổi liên tục theo thời gian.

### Lưu trữ dữ liệu lịch sử và tối ưu hóa truy vấn dung lượng lớn

Theo thời gian, số lượng bản ghi trong bảng transaction log sẽ lên tới hàng tỷ dòng, gây chậm trễ cho việc tra cứu lịch sử của người dùng trên ứng dụng di động. Bài toán thực tế là làm thế nào để thiết kế phân vùng dữ liệu hoặc kiến trúc lưu trữ sao cho việc xem lại lịch sử giao dịch từ nhiều năm trước vẫn đảm bảo tốc độ phản hồi nhanh. Bạn cần cân nhắc giữa việc lưu trữ dữ liệu nóng để truy cập thường xuyên và dữ liệu nguội để lưu trữ lâu dài mà vẫn đảm bảo tính toàn vẹn của báo cáo.

### Cơ chế bù trừ giao dịch khi xảy ra lỗi hệ thống

Trong quá trình xử lý chuỗi giao dịch phức tạp, một bước cuối cùng có thể bị thất bại do mất kết nối mạng hoặc lỗi logic. Hệ thống cần một cơ chế ghi log trạng thái trung gian để có thể thực hiện các giao dịch bù hoặc đảo ngược lại các bước đã thành công trước đó nhằm trả lại trạng thái cân bằng cho ví. Việc thiết kế các trạng thái giao dịch trong log như đang xử lý, thành công, thất bại, hoặc đã đảo ngược là cực kỳ quan trọng để đảm bảo hệ thống không rơi vào trạng thái không xác định.
