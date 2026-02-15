# Funnel tracking

### Phân tích tỷ lệ rơi rụng theo từng bước của chiến dịch marketing

Hệ thống cần ghi lại hành trình của người dùng bắt đầu từ lúc họ nhấn vào một quảng cáo cụ thể cho đến khi hoàn tất đơn hàng. Các bước bao gồm xem trang sản phẩm, thêm vào giỏ hàng, điền thông tin giao hàng và thanh toán thành công. Bài toán đặt ra là làm sao để lưu trữ nguồn gốc của người dùng và đối chiếu với các hành động tiếp theo của họ để tìm ra bước nào đang có tỷ lệ khách hàng rời bỏ cao nhất. Điều này giúp đội ngũ vận hành biết được liệu trang sản phẩm chưa hấp dẫn hay quy trình thanh toán quá phức tạp.

### Theo dõi thời gian hoàn thành giữa các bước trong phễu

Ngoài việc biết người dùng dừng lại ở đâu, hệ thống cần đo lường khoảng thời gian trung bình để một người dùng chuyển từ bước này sang bước kế tiếp. Ví dụ, một khách hàng có thể mất 2 phút để xem sản phẩm nhưng mất tới 2 ngày mới quyết định nhấn nút thanh toán sau khi đã thêm vào giỏ hàng. Việc thiết kế database phải cho phép tính toán sự chênh lệch thời gian giữa các sự kiện khác nhau của cùng một phiên làm việc để xác định các điểm nghẽn về mặt tâm lý hoặc kỹ thuật.

### Phân tích phễu chuyển đổi dựa trên thiết bị và hệ điều hành

Hành vi người dùng thường khác nhau giữa các nền tảng như ứng dụng di động và trình duyệt máy tính. Bài toán yêu cầu hệ thống phải ghi nhận thông tin về thiết bị, phiên bản hệ điều hành và trình duyệt cho mỗi bước trong phễu. Mục tiêu là phát hiện xem có phải tỷ lệ rơi rụng ở bước thanh toán trên một phiên bản iPhone cụ thể cao bất thường hay không, từ đó giúp bộ phận kỹ thuật khoanh vùng các lỗi hiển thị hoặc lỗi tính năng chỉ xuất hiện trên một số thiết bị nhất định.

### Xử lý dữ liệu phễu với người dùng ẩn danh và người dùng đã đăng nhập

Đây là bài toán khó về thiết kế định danh khách hàng. Một người dùng có thể xem sản phẩm khi chưa đăng nhập, nhưng sau đó mới đăng nhập để thanh toán. Hệ thống cần có cơ chế liên kết (stitch) các sự kiện ẩn danh trước đó vào hồ sơ của người dùng chính thức sau khi họ đăng nhập thành công. Điều này đảm bảo hành trình được ghi lại là một chuỗi liên tục thay vì bị chia cắt thành hai phễu rời rạc, giúp việc báo cáo dữ liệu chính xác hơn.

### Phân tích phễu theo đặc tính sản phẩm hoặc danh mục hàng hóa

Tỷ lệ chuyển đổi của ngành hàng thời trang thường khác hoàn toàn với ngành hàng điện tử giá trị cao. Bài toán yêu cầu thiết kế hệ thống tracking sao cho có thể lọc phễu theo loại sản phẩm hoặc giá trị đơn hàng. Ví dụ, hệ thống phải cho phép xem phễu chuyển đổi riêng cho các sản phẩm có giá trên mười triệu đồng để thấy được khách hàng thường phân vân ở bước nào nhất đối với các món đồ xa xỉ, từ đó đề xuất các tính năng hỗ trợ như trả góp hoặc tư vấn trực tuyến.

### Theo dõi tác động của các chương trình khuyến mãi đến phễu chuyển đổi

Khi áp dụng một mã giảm giá, hành vi của người dùng trong phễu có thể thay đổi rõ rệt. Bài toán đặt ra là ghi lại trạng thái có áp dụng coupon hay không tại bước giỏ hàng và theo dõi xem liệu việc có mã giảm giá có thực sự thúc đẩy người dùng đi đến bước thanh toán cuối cùng hay không. Hệ thống cần so sánh được hai phễu: một phễu của những người có mã giảm giá và một phễu của những người không có để đánh giá hiệu quả thực sự của chiến dịch khuyến mãi.

### Ghi nhận và xử lý sự kiện trùng lặp trong hành trình người dùng

Trong thực tế, người dùng có thể nhấn nút thêm vào giỏ hàng nhiều lần hoặc tải lại trang thanh toán liên tục do mạng yếu. Nếu hệ thống ghi nhận mỗi lần nhấn là một bước trong phễu, dữ liệu sẽ bị sai lệch hoàn toàn. Bài toán yêu cầu thiết kế API và Database có khả năng xử lý trùng lặp hoặc gộp các sự kiện tương tự nhau trong một khoảng thời gian ngắn để đảm bảo mỗi bước trong phễu chỉ phản ánh đúng một trạng thái chuyển đổi thực của khách hàng.

### Phân tích phễu quay lại sau khi giỏ hàng bị bỏ quên

Hệ thống cần theo dõi những người dùng đã dừng lại ở bước thêm vào giỏ hàng nhưng không thanh toán, sau đó quay lại trang web thông qua một email nhắc nhở hoặc tin nhắn thông báo. Bài toán này đòi hỏi việc thiết kế hệ thống phải có sự kết nối giữa các sự kiện trong quá khứ và các lượt truy cập mới. Việc xác định người dùng quay lại và hoàn tất phễu cũ hay bắt đầu một phễu hoàn toàn mới là cực kỳ quan trọng để đánh giá mức độ giữ chân khách hàng của hệ thống.
