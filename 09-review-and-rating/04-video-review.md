# Video review

### Quản lý lưu trữ và phân phối video đa độ phân giải

Khi người dùng tải lên một video đánh giá từ điện thoại, tệp tin gốc thường có dung lượng rất lớn và định dạng không đồng nhất. Hệ thống cần một quy trình tiếp nhận video, sau đó thực hiện chuyển đổi sang nhiều định dạng và độ phân giải khác nhau như 480p, 720p hoặc 1080p để đảm bảo mọi thiết bị đều có thể xem mượt mà. Bài toán này yêu cầu bạn thiết kế cách lưu trữ các phiên bản video này trong database, quản lý đường dẫn URL từ CDN và xử lý trạng thái xử lý video từ lúc đang chờ đến khi sẵn sàng hiển thị.

### Hệ thống kiểm duyệt nội dung video tự động và thủ công

Video review có rủi ro chứa nội dung vi phạm chính sách, quảng cáo rác hoặc hình ảnh không phù hợp. Bạn cần thiết kế một quy trình kiểm duyệt gồm nhiều bước: ngay khi tải lên video sẽ ở trạng thái chờ, sau đó được gửi qua các công cụ nhận diện hình ảnh/âm thanh tự động và cuối cùng có thể cần nhân viên vận hành xác nhận lại. Cơ sở dữ liệu cần lưu vết lịch sử kiểm duyệt, lý do từ chối và thông tin người kiểm duyệt để đảm bảo tính minh bạch và quản lý chất lượng nội dung.

### Gắn thẻ sản phẩm và mốc thời gian trong video

Để tăng tính trải nghiệm, người xem muốn biết chính xác thời điểm nào trong video đang nói về tính năng cụ thể của sản phẩm. Bài toán đặt ra là cho phép người đánh giá tạo các điểm mốc thời gian kèm theo mô tả ngắn hoặc gắn thẻ các sản phẩm liên quan xuất hiện trong khung hình. Việc thiết kế API và Database phải đảm bảo truy xuất nhanh danh sách các điểm mốc này theo ID video và cho phép người dùng click vào mốc thời gian để nhảy đến đoạn video tương ứng.

### Tương tác và đo lường hiệu quả video review

Video review không chỉ để xem mà còn để tương tác thông qua việc thả tim, bình luận hoặc đánh giá tính hữu ích. Hệ thống cần ghi lại lượt xem thực tế, thời gian xem trung bình và các hành động tương tác để tính toán điểm uy tín cho người đánh giá. Thách thức ở đây là thiết kế hệ thống sao cho việc cập nhật các chỉ số thời gian thực như lượt xem không làm nghẽn cơ sở dữ liệu khi có một video review cực kỳ phổ biến đang được truy cập đồng thời bởi hàng triệu người.

### Chiến dịch thúc đẩy đánh giá kèm video thông qua khuyến mãi

Doanh nghiệp thường tặng xu hoặc voucher cho những khách hàng chịu khó quay video review chất lượng cao. Bài toán này yêu cầu thiết kế logic kiểm tra điều kiện: video phải đạt độ dài tối thiểu, phải được duyệt thành công thì hệ thống mới tự động cộng thưởng vào ví điện tử của người dùng. Bạn cần xử lý các vấn đề về giao dịch thanh toán, đối soát giữa bảng đánh giá và bảng lịch sử nhận thưởng để tránh việc người dùng nhận thưởng nhiều lần cho cùng một nội dung.

### Tìm kiếm và lọc đánh giá theo thuộc tính video

Người mua hàng thường ưu tiên xem các đánh giá có video trước khi quyết định xuống tiền. Hệ thống cần cung cấp bộ lọc chuyên sâu như chỉ xem các bài đánh giá có video, sắp xếp theo video mới nhất hoặc video được xem nhiều nhất. Điều này đòi hỏi thiết kế chỉ mục trong database hiệu quả để khi người dùng nhấn vào bộ lọc video trên trang sản phẩm có hàng nghìn đánh giá, kết quả phải trả về ngay lập tức mà không gây trễ cho giao diện người dùng.

### Quản lý quyền riêng tư và bản quyền video review

Người dùng có thể muốn xóa video đánh giá sau một thời gian hoặc chuyển trạng thái từ công khai sang riêng tư. Bên cạnh đó, hệ thống cần xử lý trường hợp video vi phạm bản quyền âm nhạc hoặc hình ảnh từ bên thứ ba. Bạn cần thiết kế cấu trúc dữ liệu để quản lý quyền sở hữu, trạng thái hiển thị và logic xóa mềm để có thể khôi phục dữ liệu khi cần thiết hoặc xử lý các khiếu nại liên quan đến quyền riêng tư cá nhân của người xuất hiện trong video.

### Phân tích xu hướng nội dung video bằng trí tuệ nhân tạo

Để hỗ trợ bộ phận marketing, hệ thống cần trích xuất dữ liệu từ video review như cảm xúc của người nói là tích cực hay tiêu cực, các từ khóa chính họ nhắc đến là gì. Bài toán này không chỉ là lưu trữ video mà còn là lưu trữ các kết quả phân tích metadata sau khi video được xử lý qua AI. Cấu trúc database phải linh hoạt để chứa các kết quả phân tích dạng JSON hoặc bảng quan hệ phức tạp nhằm phục vụ cho việc xuất báo cáo tổng hợp về mức độ hài lòng của khách hàng đối với từng dòng sản phẩm.
