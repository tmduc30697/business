# Fraud scoring

### Quản lý dấu chân thiết bị và danh tính số

Bài toán này tập trung vào việc thu thập và đối soát các thông tin định danh không tên của người dùng. Hệ thống cần ghi lại các thuộc tính như địa chỉ IP, loại trình duyệt, độ phân giải màn hình, hệ điều hành và ID thiết bị duy nhất. Khi một đơn hàng mới được tạo, hệ thống phải truy vấn xem thiết bị này đã từng gắn liền với các tài khoản bị khóa trước đó hay chưa, hoặc kiểm tra xem có sự bất thường khi một thiết bị nhưng đăng nhập vào hàng chục tài khoản khác nhau trong thời gian ngắn hay không.

### Phân tích hành vi vận tốc giao dịch

Vấn đề cốt lõi ở đây là theo dõi tần suất hoạt động trong một khoảng thời gian nhất định để phát hiện các cuộc tấn công tự động hoặc hành vi chiếm đoạt tài khoản. Bạn cần thiết kế cách lưu trữ để tính toán nhanh số lượng giao dịch của một thẻ tín dụng hoặc một người dùng trong vòng 1 phút, 1 giờ hoặc 24 giờ qua. Nếu một người dùng bình thường chỉ mua sắm 1 lần mỗi tuần nhưng đột ngột phát sinh 10 giao dịch tại các vị trí địa lý khác nhau trong 30 phút, hệ thống sẽ tự động tăng điểm rủi ro.

### Đối soát tính nhất quán của dữ liệu vị trí

Bài toán yêu cầu kiểm tra sự logic giữa địa chỉ IP của người dùng, địa chỉ thanh toán của thẻ và địa chỉ giao hàng. Hệ thống cần xác định xem người dùng đang thực hiện giao dịch tại Việt Nam nhưng lại sử dụng thẻ phát hành tại một quốc gia châu Âu và yêu cầu giao hàng đến một kho bãi tại biên giới hay không. Việc xử lý dữ liệu địa lý và tính toán khoảng cách giữa các điểm này là yếu tố then chốt để đưa ra quyết định duyệt đơn.

### Xây dựng danh sách đen và danh sách trắng linh hoạt

Hệ thống cần một cơ chế để quản lý các thực thể đã bị xác định là gian lận hoặc hoàn toàn tin cậy. Dữ liệu không chỉ đơn thuần là ID người dùng mà còn bao gồm dải IP, đầu số thẻ tín dụng, email rác hoặc thậm chí là số điện thoại. Thách thức ở đây là thiết kế cơ sở dữ liệu sao cho việc tra cứu các danh sách này cực kỳ nhanh chóng trước khi chạy qua các bộ quy tắc phức tạp hơn, nhằm tối ưu hiệu năng cho hệ thống.

### Hệ thống chấm điểm dựa trên bộ quy tắc tùy biến

Thay vì viết cứng mã nguồn, bạn cần thiết kế một hệ thống cho phép quản trị viên tự cấu hình các luật. Ví dụ, nếu giá trị đơn hàng lớn hơn một mức nhất định và là khách hàng mới thì cộng thêm 50 điểm rủi ro. Nếu điểm tổng vượt ngưỡng 80 thì từ chối, từ 50 đến 80 thì đưa vào trạng thái chờ duyệt thủ công, dưới 50 thì cho phép thanh toán. Việc thiết kế bảng lưu trữ các quy tắc và lịch sử áp dụng quy tắc lên từng đơn hàng là rất quan trọng.

### Theo dõi lịch sử hoàn tiền và tranh chấp

Bài toán này hướng đến việc nhận diện những người dùng chuyên lợi dụng kẽ hở chính sách để trục lợi. Hệ thống cần lưu trữ lịch sử các lần khách hàng yêu cầu hoàn tiền hoặc báo cáo giao dịch giả mạo với ngân hàng. Nếu một tài khoản có tỉ lệ hoàn hàng hoặc tranh chấp cao bất thường so với tổng số giao dịch đã thực hiện, mọi đơn hàng trong tương lai của họ sẽ bị đánh dấu cảnh báo cao ngay lập tức.

### Phát hiện mạng lưới liên kết tài khoản

Đây là bài toán phức tạp về mối quan hệ giữa các đối tượng. Gian lận thường không đi đơn lẻ mà theo nhóm. Bạn cần thiết kế hệ thống sao cho có thể phát hiện ra các tài khoản khác nhau nhưng dùng chung một số điện thoại, hoặc các đơn hàng khác nhau nhưng có cùng một địa chỉ giao hàng và mã giảm giá. Việc truy xuất các mối liên hệ chéo này giúp chặn đứng các đường dây gian lận có tổ chức quy mô lớn.

### Lưu vết và giải trình quyết định rủi ro

Khi một đơn hàng bị từ chối hoặc giữ lại để kiểm tra, hệ thống phải cung cấp được lý do cụ thể cho đội ngũ vận hành. Bài toán này yêu cầu thiết kế dữ liệu để lưu lại trạng thái của tất cả các biến số tại thời điểm giao dịch diễn ra. Điều này không chỉ giúp nhân viên hỗ trợ giải thích cho khách hàng mà còn là nguồn dữ liệu quan trọng để các kỹ sư phân tích lại nhằm điều chỉnh các bộ quy tắc chấm điểm sao cho chính xác hơn trong tương lai.
