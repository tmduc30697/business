# Escalation

### Hệ thống quản lý khiếu nại khách hàng tại ngân hàng

Trong kịch bản này, một giao dịch bị lỗi khiến khách hàng mất tiền. Nhân viên hỗ trợ tầng 1 có thời hạn 4 giờ để phản hồi. Nếu sau 4 giờ chưa có phương án giải quyết hoặc khách hàng không đồng ý với bồi thường, hệ thống tự động đẩy yêu cầu lên Trưởng phòng vận hành. Nếu số tiền tranh chấp vượt quá 50 triệu đồng, vụ việc phải được chuyển thẳng đến bộ phận Kiểm soát rủi ro thay vì đi theo cấp bậc thông thường. Bạn cần quản lý trạng thái, thời gian phản hồi (SLA) và lịch sử chuyển giao giữa các phòng ban.

### Điều phối sự cố hạ tầng công nghệ thông tin (ITSM)

Khi một máy chủ dịch vụ quan trọng bị sập, kỹ sư trực ca sẽ nhận thông báo. Nếu trong 15 phút kỹ sư không xác nhận, hệ thống sẽ thực hiện leo thang chức năng bằng cách gọi điện cho quản lý nhóm kỹ thuật. Nếu sau 1 tiếng lỗi vẫn chưa được khắc phục (Workaround), vụ việc được chuyển thành sự cố nghiêm trọng (Major Incident) và kích hoạt sự tham gia của Giám đốc công nghệ. Bài toán này tập trung vào việc quản lý lịch trực (On-call schedule), các mức độ ưu tiên và thông báo đa kênh.

### Quy trình phê duyệt tín dụng doanh nghiệp

Một hồ sơ vay vốn bắt đầu từ nhân viên quan hệ khách hàng. Nếu điểm tín dụng của doanh nghiệp nằm trong vùng rủi ro hoặc hạn mức vay vượt quá thẩm quyền của chi nhánh, hồ sơ phải được chuyển lên Hội đồng thẩm định hội sở. Tại đây, việc leo thang không chỉ là chuyển cấp mà còn là yêu cầu bổ sung hồ sơ từ các bên liên quan. Bạn cần thiết kế hệ thống có khả năng phân quyền chặt chẽ dựa trên giá trị khoản vay và vết lịch sử phê duyệt của từng cá nhân.

### Xử lý vi phạm nội dung trên mạng xã hội

Khi người dùng báo cáo một bài viết vi phạm tiêu chuẩn cộng đồng, hệ thống AI sẽ phân loại bước đầu. Nếu nội dung nhạy cảm liên quan đến pháp luật hoặc chính trị mà AI không tự quyết định được, nó sẽ chuyển cho đội ngũ kiểm duyệt viên thủ công. Trong trường hợp kiểm duyệt viên bị quá tải hoặc gặp nội dung phức tạp, vụ việc sẽ được đẩy lên nhóm chuyên gia pháp lý. Hệ thống cần lưu trữ các bằng chứng, lý do chuyển cấp và đảm bảo tính bảo mật của nội dung trong suốt quá trình xử lý.

### Quản lý bảo hành và sửa chữa thiết bị điện máy

Khách hàng mang sản phẩm lỗi đến trung tâm bảo hành. Kỹ thuật viên kiểm tra và báo giá. Nếu khách hàng khiếu nại về chất lượng bảo hành nhiều lần cho cùng một thiết bị, hệ thống phải nhận diện đây là vụ việc cần leo thang lên bộ phận Chăm sóc khách hàng cấp cao để thực hiện chính sách đổi trả đặc biệt. Bài toán yêu cầu theo dõi dòng đời sản phẩm, số lần bảo hành lặp lại và các quy tắc kích hoạt leo thang dựa trên tần suất khiếu nại.

### Hệ thống đấu thầu và giải quyết tranh chấp nhà thầu

Trong một dự án xây dựng, khi nhà thầu phụ và nhà thầu chính không thống nhất được khối lượng nghiệm thu, họ sẽ yêu cầu sự can thiệp của Tư vấn giám sát. Nếu tư vấn giám sát vẫn không đưa ra được quyết định cuối cùng trong 7 ngày làm việc, tranh chấp sẽ được gửi lên Ban quản lý dự án của chủ đầu tư. Thiết kế cần tập trung vào việc lưu trữ các biên bản hiện trường, bằng chứng hình ảnh và các mốc thời gian phản biện của mỗi bên.

### Điều phối cấp cứu và hội chẩn y tế từ xa

Tại một bệnh viện tuyến dưới, khi gặp ca bệnh vượt quá khả năng chuyên môn, bác sĩ điều trị sẽ phát lệnh yêu cầu hỗ trợ từ bệnh viện tuyến trên. Quy trình leo thang ở đây mang tính khẩn cấp cao. Hệ thống phải theo dõi được danh sách chuyên gia đang rảnh, chuyển hồ sơ bệnh án điện tử tức thời và ghi lại toàn bộ quá trình hội chẩn để phục vụ hậu kiểm. Điều quan trọng là việc phân cấp dựa trên độ khẩn cấp của tình trạng bệnh nhân.

### Xử lý hoàn trả đơn hàng trên sàn thương mại điện tử

Người mua yêu cầu trả hàng nhưng người bán từ chối với lý do sản phẩm đã bị sử dụng. Sau hai lần thương thảo không thành công qua hệ thống chat, nút khiếu nại lên sàn sẽ được kích hoạt. Lúc này, một nhân viên điều phối của sàn thương mại điện tử (Admin) sẽ vào cuộc để xem xét bằng chứng từ hai phía và đưa ra phán quyết cuối cùng. Bài toán này cần giải quyết việc lưu trữ tệp tin bằng chứng, quản lý luồng tranh luận và thực hiện các giao dịch hoàn tiền tự động sau khi có kết luận.
