# Risk dashboard

### Theo dõi tỷ lệ bồi hoàn và khiếu nại thanh toán theo thời gian thực

Hệ thống thanh toán cần giám sát tỷ lệ các giao dịch bị khách hàng yêu cầu hoàn tiền hoặc khiếu nại thông qua ngân hàng. Admin cần nhìn thấy biểu đồ diễn biến của tỷ lệ này theo từng giờ hoặc từng ngày để phát hiện sớm các đợt tấn công thanh toán bằng thẻ giả mạo. Bài toán đặt ra yêu cầu về việc lưu trữ trạng thái giao dịch từ lúc khởi tạo đến khi phát sinh tranh chấp và tính toán tỷ lệ phần trăm rủi ro dựa trên tổng doanh số trong một khoảng thời gian nhất định.

### Phát hiện các tài khoản có hành vi đăng nhập bất thường từ nhiều vị trí

Hệ thống cần ghi nhận và phân tích lịch sử đăng nhập của người dùng bao gồm địa chỉ IP, loại thiết bị và vị trí địa lý. Một bài toán thực tế là hiển thị danh sách các tài khoản có dấu hiệu bị chiếm quyền điều khiển khi phát sinh đăng nhập từ hai quốc gia khác nhau trong một khoảng thời gian ngắn mà về mặt vật lý con người không thể di chuyển kịp. Dashboard phải cung cấp công cụ để admin lọc theo mức độ nghiêm trọng và thực hiện khóa tài khoản tạm thời ngay lập tức.

### Giám sát các giao dịch có giá trị đột biến so với lịch sử chi tiêu

Mỗi người dùng thường có một ngưỡng chi tiêu trung bình dựa trên lịch sử hoạt động. Bài toán ở đây là thiết kế một công cụ giám sát tự động gắn cờ các giao dịch có giá trị cao bất thường, ví dụ một tài khoản bình thường chỉ chi tiêu vài trăm nghìn nhưng đột ngột thực hiện giao dịch hàng chục triệu đồng. Admin cần một giao diện hiển thị các giao dịch nghi vấn này kèm theo thông tin so sánh với mức chi tiêu trung bình của chính người dùng đó trong quá khứ để quyết định phê duyệt hay chặn giao dịch.

### Quản lý danh sách đen các thực thể có nguy cơ gian lận cao

Trong quản trị rủi ro, việc duy trì một cơ sở dữ liệu về các địa chỉ email, số điện thoại, hoặc ID thiết bị đã từng tham gia vào các hành vi gian lận là rất quan trọng. Bài toán yêu cầu thiết kế hệ thống cho phép admin tra cứu nhanh một đối tượng xem có nằm trong danh sách đen hay không, đồng thời tự động đánh dấu các tài khoản mới đăng ký có thông tin trùng khớp với dữ liệu trong danh sách đen để ngăn chặn thiệt hại từ sớm.

### Phân tích mạng lưới liên kết giữa các tài khoản gian lận

Kẻ gian thường tạo nhiều tài khoản ảo nhưng dùng chung một số thông tin như số tài khoản ngân hàng nhận tiền hoặc cùng một địa chỉ MAC thiết bị. Bài toán thực tế là dashboard cần hiển thị được mối liên hệ giữa các tài khoản này dưới dạng danh sách hoặc sơ đồ kết nối. Khi một tài khoản bị xác định là gian lận, hệ thống phải giúp admin tìm ra tất cả các tài khoản vệ tinh khác đang có chung đặc điểm nhận dạng để xử lý đồng loạt.

### Theo dõi ngưỡng an toàn cho các chương trình khuyến mãi và ví điện tử

Các chiến dịch tặng tiền hoặc mã giảm giá thường bị lợi dụng bởi các công cụ tự động (bot). Admin cần một bảng điều khiển hiển thị tốc độ tiêu thụ ngân sách khuyến mãi. Nếu tốc độ này tăng nhanh một cách phi mã trong vài phút, hệ thống phải cảnh báo về khả năng đang bị tấn công bởi botnet. Bài toán này tập trung vào việc thiết kế các bảng lưu trữ số liệu tổng hợp theo phút và cơ chế cấu hình ngưỡng báo động linh hoạt cho từng chiến dịch khác nhau.

### Đánh giá điểm tín nhiệm rủi ro cho hồ sơ người dùng

Hệ thống cần tổng hợp nhiều chỉ số như tuổi đời tài khoản, số lượng đơn hàng thành công, số lần vi phạm chính sách để tính toán ra một con số gọi là điểm rủi ro. Trên dashboard, admin sẽ quản lý danh sách người dùng được sắp xếp theo điểm rủi ro từ cao xuống thấp. Việc thiết kế database ở đây phải đảm bảo có thể cập nhật điểm số này thường xuyên mỗi khi người dùng có hành động mới mà không làm treo hệ thống do khối lượng tính toán lớn.

### Quản lý quy trình xử lý vi phạm và lưu vết lịch sử kiểm duyệt

Khi một rủi ro được phát hiện, quá trình xử lý của admin (như gọi điện xác minh, yêu cầu cung cấp giấy tờ, hoặc khóa vĩnh viễn) cần được ghi lại đầy đủ. Bài toán là thiết kế một hệ thống quản lý các ticket rủi ro, cho phép admin thay đổi trạng thái xử lý và lưu lại bằng chứng. Điều này giúp cấp quản lý cao hơn có thể kiểm soát được hiệu quả làm việc của đội ngũ rủi ro và đảm bảo tính minh bạch trong việc xử lý khách hàng.
