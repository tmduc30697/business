# Chargeback handling

### Quản lý vòng đời và trạng thái của khiếu nại

Hệ thống cần theo dõi một giao dịch từ khi nhận thông báo khiếu nại từ ngân hàng phát hành cho đến khi có kết quả cuối cùng. Một quy trình chargeback thường trải qua nhiều giai đoạn như tiếp nhận yêu cầu, đang điều tra, đã nộp bằng chứng phản hồi, chờ ngân hàng xét duyệt, và cuối cùng là thắng hoặc thua khiếu nại. Việc thiết kế cần đảm bảo tính nhất quán về trạng thái để các bộ phận liên quan như kế toán hoặc chăm sóc khách hàng có thể theo dõi thời gian thực và biết được thời hạn còn lại để phản hồi trước khi bị xử thua tự động.

### Lưu trữ và quản lý tài liệu minh chứng

Khi xảy ra khiếu nại, người bán phải cung cấp các bằng chứng để chứng minh giao dịch là hợp lệ. Bài toán này yêu cầu hệ thống quản lý các loại tệp tin khác nhau như hóa đơn vận chuyển, ảnh chụp màn hình lịch sử chat, biên nhận ký tên hoặc logs đăng nhập của người dùng. Mỗi loại lý do khiếu nại như giao dịch gian lận hoặc hàng hóa không đúng mô tả sẽ yêu cầu một bộ tài liệu minh chứng khác nhau. Hệ thống cần phân loại và liên kết các tài liệu này với mã khiếu nại tương ứng để sẵn sàng trích xuất khi gửi sang cổng thanh toán.

### Đối soát dòng tiền và phí phạt chargeback

Một giao dịch bị khiếu nại không chỉ đơn thuần là việc hoàn trả số tiền gốc. Ngân hàng và các cổng thanh toán thường thu thêm các khoản phí xử lý khiếu nại bất kể người bán thắng hay thua. Bài toán đặt ra là phải hạch toán chính xác số tiền bị tạm giữ, số tiền thực tế bị trừ từ tài khoản người bán, và các khoản phí phát sinh. Điều này đòi hỏi thiết kế database phải tách biệt giữa giá trị giao dịch gốc và các thực thể tài chính phát sinh trong quá trình xử lý tranh chấp để phục vụ báo cáo tài chính.

### Hệ thống cảnh báo ngưỡng rủi ro và tỉ lệ khiếu nại

Các tổ chức thẻ như Visa hay Mastercard có quy định nghiêm ngặt về tỉ lệ chargeback trên tổng số giao dịch. Nếu tỉ lệ này vượt quá một ngưỡng nhất định (ví dụ 1%), tài khoản người bán có thể bị khóa hoặc phạt nặng. Hệ thống cần tính toán tỉ lệ này theo thời gian thực hoặc theo tháng, đồng thời gửi thông báo cảnh báo sớm khi các chỉ số chạm ngưỡng nguy hiểm. Việc này giúp doanh nghiệp kịp thời điều chỉnh chính sách bán hàng hoặc kiểm tra lại các lỗ hổng bảo mật thanh toán.

### Tự động hóa phản hồi dựa trên lý do khiếu nại

Mỗi khiếu nại đi kèm với một mã lý do cụ thể từ ngân hàng (Reason Code). Bài toán ở đây là xây dựng một hệ thống quy tắc để tự động hóa việc thu thập dữ liệu phản hồi. Ví dụ, nếu lý do là chưa nhận được hàng, hệ thống phải tự động truy vấn thông tin từ API của đơn vị vận chuyển để lấy trạng thái giao hàng thành công. Nếu lý do là giao dịch không được ủy quyền, hệ thống cần trích xuất địa chỉ IP và lịch sử xác thực hai lớp của người dùng để làm bằng chứng phản hồi nhanh chóng mà không cần con người can thiệp thủ công.

### Quản lý danh sách đen và ngăn chặn tái phạm

Sau khi một giao dịch bị xác định là chargeback gian lận, hệ thống cần có cơ chế lưu trữ các đặc điểm nhận dạng của người mua đó để ngăn chặn các giao dịch trong tương lai. Các thông tin cần quản lý bao gồm số thẻ đã mã hóa, địa chỉ email, số điện thoại, và vân tay thiết bị. Bài toán này tập trung vào việc thiết kế một cơ chế lọc và đối soát dữ liệu đầu vào của mỗi đơn hàng mới với danh sách đen đã có để từ chối thanh toán ngay lập tức, giảm thiểu rủi ro lặp lại.

### Phân quyền và theo dõi vết hoạt động của nhân viên vận hành

Quy trình xử lý khiếu nại thường có sự tham gia của nhiều bộ phận như đội ngũ rủi ro, đội ngũ hỗ trợ khách hàng và quản lý cấp cao. Hệ thống cần một cơ chế phân quyền chặt chẽ để xác định ai có quyền phê duyệt bằng chứng trước khi gửi đi hoặc ai có quyền cập nhật kết quả tài chính. Đồng thời, mọi thay đổi về trạng thái hoặc chỉnh sửa tài liệu đều phải được ghi lại dưới dạng nhật ký hệ thống để phục vụ công tác kiểm tra lại khi có sai sót xảy ra.

### Liên kết giao dịch gốc và các phiên bản sửa đổi

Một đơn hàng có thể có nhiều giao dịch thanh toán và một giao dịch có thể bị khiếu nại một phần hoặc toàn bộ số tiền. Bài toán yêu cầu hệ thống phải duy trì mối liên kết chặt chẽ giữa mã đơn hàng, mã giao dịch và mã khiếu nại. Ngoài ra, trong trường hợp người bán chủ động hoàn tiền (Refund) để tránh khiếu nại leo thang, hệ thống phải xử lý được sự xung đột giữa lệnh hoàn tiền tự nguyện và lệnh hoàn tiền cưỡng bức từ ngân hàng để tránh việc mất tiền hai lần cho cùng một giao dịch.

### Phân tích xu hướng và báo cáo hiệu quả xử lý

Để tối ưu hóa kinh doanh, doanh nghiệp cần biết lý do chargeback nào đang chiếm tỉ trọng cao nhất và tỉ lệ thắng kiện của từng loại là bao nhiêu. Bài toán này tập trung vào việc tổng hợp dữ liệu để xuất các báo cáo phân tích theo sản phẩm, theo khu vực địa lý hoặc theo cổng thanh toán. Dữ liệu này giúp bộ phận kinh doanh nhận diện được các sản phẩm kém chất lượng hoặc các thị trường có tỉ lệ gian lận cao để đưa ra các quyết định điều chỉnh chiến lược phù hợp.

### Tích hợp Webhook và đồng bộ dữ liệu với cổng thanh toán

Thông tin về khiếu nại thường đến từ phía cổng thanh toán thông qua các thông báo bất đồng bộ. Hệ thống cần một kiến trúc xử lý Webhook tin cậy để tiếp nhận thông tin, xác thực chữ ký số nhằm đảm bảo an toàn, và cập nhật ngay lập tức vào cơ sở dữ liệu nội bộ. Thách thức ở đây là xử lý việc nhận tin nhắn trùng lặp hoặc tin nhắn đến sai thứ tự thời gian, đảm bảo rằng trạng thái cuối cùng của khiếu nại trong hệ thống luôn khớp với thực tế tại ngân hàng.
