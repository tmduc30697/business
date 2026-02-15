# AI chatbot

### Hệ thống phân luồng hỗ trợ đa kênh

Bài toán này tập trung vào việc tiếp nhận tin nhắn từ nhiều nguồn khách hàng khác nhau như Website, Facebook Fanpage và Zalo OA. Hệ thống cần định danh được khách hàng dù họ đến từ nguồn nào để hợp nhất lịch sử trò chuyện. Khi khách hàng nhắn tin, chatbot sẽ quét từ khóa trong cơ sở dữ liệu để đưa ra câu trả lời tương ứng. Nếu chatbot không thể giải quyết trong ba lần tương tác liên tiếp hoặc khách hàng yêu cầu gặp tư vấn viên, hệ thống phải tự động đánh dấu trạng thái chờ để nhân viên trực tổng đài tiếp quản cuộc trò chuyện trên giao diện quản trị.

### Quản lý kịch bản chăm sóc khách hàng tự động

Đây là bài toán thiết kế luồng hội thoại theo dạng cây quyết định. Người quản trị có thể tạo ra các kịch bản gồm nhiều bước, mỗi bước có các nút bấm lựa chọn cho khách hàng. Ví dụ, bước một là chọn loại dịch vụ, bước hai là chọn khu vực địa lý. Hệ thống cần lưu trữ cấu trúc các bước này, mối quan hệ cha con giữa các câu hỏi và các điều kiện chuyển hướng. Khi khách hàng nhấn vào một nút, hệ thống phải truy vấn để biết bước tiếp theo cần hiển thị là gì và lưu lại vết hành trình mà khách hàng đã đi qua trong kịch bản đó.

### Hệ thống đặt lịch hẹn và nhắc lịch tự động

Bài toán kết hợp giữa chatbot và quản lý thời gian thực. Khách hàng thông qua chatbot để kiểm tra các khung giờ còn trống của dịch vụ như phòng khám hoặc spa. Sau khi khách hàng chọn giờ và cung cấp số điện thoại, chatbot sẽ ghi nhận thông tin vào lịch hẹn và gửi tin nhắn xác nhận. Quan trọng hơn, hệ thống cần một cơ chế quét các lịch hẹn sắp đến hạn để tự động gửi tin nhắn nhắc nhở qua chatbot cho khách hàng trước một khoảng thời gian quy định, đồng thời cho phép khách hàng xác nhận tham gia hoặc hủy lịch trực tiếp trên khung chat.

### Quản lý thư viện câu hỏi thường gặp và kiến thức nền

Bài toán này giải quyết việc lưu trữ và phân loại hàng ngàn câu hỏi FAQ. Các câu hỏi được chia theo danh mục, mức độ ưu tiên và các từ khóa liên quan. Hệ thống cần hỗ trợ lưu trữ nhiều phiên bản câu trả lời cho cùng một câu hỏi để thực hiện kiểm thử xem câu trả lời nào hiệu quả hơn. Ngoài ra, dữ liệu này cần được cấu trúc sao cho API có thể dễ dàng tìm kiếm theo độ tương đồng của văn bản hoặc theo nhóm chủ đề để chatbot phản hồi nhanh chóng nhất.

### Theo dõi hiệu suất và phản hồi của người dùng

Sau mỗi lần chatbot hỗ trợ, hệ thống cần thu thập đánh giá của người dùng về chất lượng câu trả lời theo thang điểm hoặc biểu tượng cảm xúc. Bài toán yêu cầu lưu trữ chi tiết từng phiên làm việc, thời gian phản hồi của bot, tỷ lệ khách hàng rời bỏ giữa chừng và danh sách các câu hỏi mà bot không tìm thấy câu trả lời trong cơ sở dữ liệu. Dữ liệu này sẽ được dùng để thiết kế các báo cáo thống kê, giúp người quản trị biết được chatbot đang yếu ở mảng kiến thức nào để cập nhật kịp thời.

### Hệ thống phân quyền và quản lý hội thoại cho nhân viên

Trong một doanh nghiệp có nhiều phòng ban, bài toán đặt ra là làm thế nào để chuyển đúng cuộc hội thoại từ chatbot sang đúng nhân viên có chuyên môn. Hệ thống cần quản lý danh sách nhân viên, phòng ban chuyên trách và trạng thái online của họ. Khi có yêu cầu hỗ trợ trực tiếp, hệ thống sẽ kiểm tra nhân viên nào đang rảnh và có kỹ năng phù hợp để điều hướng cuộc chat. Nhân viên có thể xem lại toàn bộ lịch sử mà chatbot đã trò chuyện với khách hàng trước đó để nắm bắt ngữ cảnh mà không cần hỏi lại từ đầu.

### Tích hợp tra cứu đơn hàng và tình trạng vận chuyển

Đây là bài toán kết nối chatbot với dữ liệu kinh doanh. Khi khách hàng nhập mã đơn hàng vào khung chat, hệ thống API phải truy xuất dữ liệu từ bảng đơn hàng và bảng vận chuyển để trả về trạng thái hiện tại như đang đóng gói, đang giao hay đã hoàn thành. Chatbot cũng cần xử lý các tình huống như mã đơn hàng không tồn tại hoặc đơn hàng đang gặp sự cố, từ đó đưa ra hướng dẫn cụ thể cho khách hàng hoặc chuyển kết nối tới bộ phận xử lý khiếu nại.

### Quản lý chiến dịch gửi tin nhắn hàng loạt

Bài toán tập trung vào việc chủ động gửi tin nhắn từ hệ thống đến danh sách khách hàng mục tiêu. Người quản trị thiết kế một thông điệp quảng bá và chọn tệp khách hàng dựa trên các tiêu chí như lịch sử mua hàng hoặc lần cuối tương tác. Hệ thống cần lưu trữ trạng thái gửi của từng tin nhắn như đã gửi, đã xem hoặc gửi lỗi. Do việc gửi hàng loạt có thể gây nghẽn, kiến trúc hệ thống cần xem xét việc sử dụng hàng đợi tin nhắn để xử lý lần lượt và đảm bảo không vi phạm chính sách chống rác của các nền tảng nhắn tin.
