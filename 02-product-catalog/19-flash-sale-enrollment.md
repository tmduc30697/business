# Flash sale enrollment

### Quản lý chu kỳ đăng ký và phê duyệt hàng loạt

Hệ thống cần cho phép quản trị viên tạo ra các chiến dịch lớn theo mùa. Mỗi chiến dịch sẽ có các khung giờ mở bán khác nhau trong ngày và các tiêu chí bắt buộc dành cho người bán như điểm uy tín tối thiểu hoặc tỉ lệ phản hồi khách hàng. Người bán sẽ gửi danh sách hàng loạt sản phẩm muốn tham gia, sau đó bộ phận vận hành sẽ tiến hành phê duyệt hoặc từ chối từng sản phẩm dựa trên mức giá giảm so với giá gốc trong lịch sử.

### Kiểm soát tồn kho ảo và giới hạn đặt mua

Trong một sự kiện giảm giá sâu, việc quản lý kho hàng trở nên cực kỳ nhạy cảm. Bài toán đặt ra là khi người bán đăng ký, họ phải cam kết một lượng tồn kho riêng biệt dành cho Flash Sale mà không ảnh hưởng đến tồn kho bán lẻ thông thường. Đồng thời, hệ thống cần có cơ chế thiết lập giới hạn mỗi khách hàng chỉ được mua tối đa một số lượng sản phẩm nhất định trong suốt thời gian diễn ra chương trình để tránh tình trạng đầu cơ.

### Điều phối khung giờ và tránh xung đột sản phẩm

Một sản phẩm không thể xuất hiện trong hai khung giờ Flash Sale trùng nhau hoặc quá gần nhau để đảm bảo tính công bằng và hiệu quả marketing. Hệ thống cần một logic kiểm tra chặt chẽ khi người bán đăng ký: nếu sản phẩm A đã được duyệt vào khung giờ mười hai giờ trưa, thì các yêu cầu đăng ký cho sản phẩm đó vào khung giờ một giờ chiều cùng ngày phải bị hệ thống tự động chặn lại hoặc cảnh báo xung đột.

### Theo dõi biến động giá và bảo vệ người tiêu dùng

Để tránh tình trạng người bán nâng giá gốc lên cao rồi mới giảm giá Flash Sale, hệ thống cần lưu trữ lịch sử giá của sản phẩm trong vòng ba mươi ngày gần nhất. Khi người bán thực hiện đăng ký tham gia chương trình, API sẽ thực hiện tính toán so sánh giá đăng ký với giá trung bình trong quá khứ. Nếu mức giảm giá không đạt tối thiểu mười lăm phần trăm hoặc giá đăng ký cao hơn giá bán thường nhật, yêu cầu đăng ký sẽ bị loại bỏ ngay lập tức.

### Phân tầng ưu tiên cho người bán kim cương

Hệ thống cần phân loại các đối tác bán hàng thành nhiều cấp bậc khác nhau như người bán mới, người bán tích cực và người bán kim cương. Những người bán ở cấp độ cao sẽ có quyền đăng ký sản phẩm vào các khung giờ vàng có lượng truy cập lớn nhất. Ngược lại, những người bán mới có thể bị giới hạn số lượng sản phẩm đăng ký mỗi ngày hoặc chỉ được tham gia vào các khung giờ thấp điểm để làm quen với quy trình vận hành.

### Hệ thống thông báo và trạng thái đăng ký theo thời gian thực

Quy trình từ lúc người bán nhấn nút đăng ký, chờ duyệt, đến khi sản phẩm chính thức lên sàn là một luồng trạng thái phức tạp. Bài toán yêu cầu thiết kế một cơ chế cập nhật trạng thái liên tục để người bán biết được sản phẩm của mình đang ở bước nào. Khi một khung giờ Flash Sale sắp bắt đầu, hệ thống phải tự động gửi thông báo nhắc nhở cho người bán kiểm tra lại tồn kho và chuẩn bị vận hành để tránh tình trạng đơn hàng bị hủy sau khi khách hàng thanh toán.

### Quản lý hiệu suất sau chương trình và dữ liệu lịch sử

Sau khi kết thúc mỗi đợt Flash Sale, dữ liệu về số lượng đơn hàng thành công, số lượng hàng tồn dư và doanh thu thực tế cần được tổng hợp lại và gắn liền với bản đăng ký ban đầu. Việc này phục vụ cho mục đích báo cáo và giúp hệ thống tự động đánh giá hiệu quả của người bán. Nếu một người bán đăng ký số lượng lớn nhưng tỷ lệ hoàn thành đơn hàng quá thấp, hệ thống sẽ tự động hạn chế quyền đăng ký của họ trong các chiến dịch tiếp theo.

### Tự động hóa kết thúc và hoàn trả tồn kho

Khi đồng hồ đếm ngược của khung giờ Flash Sale trở về không, toàn bộ các sản phẩm trong phiên đó phải được chuyển trạng thái về giá bán thường hoặc ẩn khỏi trang khuyến mãi. Một vấn đề kỹ thuật quan trọng là xử lý phần tồn kho chưa bán hết. Hệ thống cần có logic tự động cộng hoàn lại số lượng tồn kho Flash Sale còn dư vào kho bán lẻ chính thức của người bán để họ tiếp tục kinh doanh mà không cần thao tác thủ công.
