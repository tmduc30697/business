# File sharing

### Quản lý phiên bản tài liệu trong dự án xây dựng

Trong các dự án kỹ thuật, một bản vẽ thiết kế có thể bị chỉnh sửa nhiều lần. Khi kiến trúc sư gửi một tệp tin mới lên cuộc trò chuyện, hệ thống cần ghi nhận đây là phiên bản tiếp theo của một tệp đã tồn tại thay vì một tệp hoàn toàn độc lập. Người dùng cần theo dõi được ai là người đã tải lên phiên bản cụ thể, thời gian tải lên và có khả năng truy xuất lại các bản cũ để đối chiếu sự thay đổi. Việc này đòi hỏi cách tổ chức dữ liệu sao cho các tệp tin có mối quan hệ cha con hoặc theo chuỗi thời gian.

### Hệ thống hóa đơn và chứng từ cho ứng dụng kế toán

Khi nhân viên gửi ảnh chụp hóa đơn hoặc tệp PDF quyết toán vào nhóm chat của phòng tài chính, hệ thống cần phân loại và gắn nhãn tự động cho các tệp này. Bài toán đặt ra là làm thế nào để quản lý các siêu dữ liệu đi kèm như mã số thuế, tổng số tiền hoặc loại chi phí được trích xuất từ tệp. Ngoài ra, các tệp này cần có cơ chế bảo mật nghiêm ngặt để chỉ những người có thẩm quyền mới được phép xem hoặc tải về, ngay cả khi họ có đường dẫn trực tiếp đến tệp tin đó.

### Thu hồi và xóa tệp tin có điều kiện trong ứng dụng nhắn tin doanh nghiệp

Trong môi trường doanh nghiệp, đôi khi người dùng gửi nhầm tài liệu nhạy cảm và cần thu hồi. Bài toán yêu cầu thiết kế hệ thống sao cho khi một tệp bị xóa hoặc thu hồi từ phía người gửi, tệp đó phải được xử lý triệt để trên máy chủ lưu trữ hoặc bị vô hiệu hóa quyền truy cập đối với người nhận. Bạn cần tính đến trường hợp tệp đã được chuyển tiếp sang nhiều cuộc hội thoại khác nhau, dẫn đến việc phải quản lý tham chiếu tệp để tránh xóa nhầm dữ liệu vẫn đang được sử dụng ở nơi khác.

### Xem trước nội dung tệp đa phương tiện (Media Thumbnail & Preview)

Khi một tệp video dung lượng lớn hoặc một tệp tài liệu nhiều trang được gửi đi, người nhận không nhất thiết phải tải toàn bộ tệp về để biết nội dung. Hệ thống cần có quy trình xử lý hậu kỳ sau khi tệp được tải lên thành công để tạo ra các bản thu nhỏ, bản nén dung lượng thấp hoặc các trang xem trước. Bài toán này tập trung vào việc thiết kế luồng xử lý bất đồng bộ, quản lý nhiều định dạng lưu trữ cho cùng một thực thể tệp tin và cách trả về URL phù hợp với thiết bị của người dùng.

### Giới hạn băng thông và dung lượng lưu trữ theo gói thành viên

Một nền tảng SaaS thường cung cấp các mức dung lượng lưu trữ khác nhau cho người dùng miễn phí và người dùng trả phí. Bài toán yêu cầu bạn thiết kế cơ chế kiểm soát dung lượng tổng mà một cá nhân hoặc một tổ chức đã sử dụng trong thời gian thực. Hệ thống phải ngăn chặn việc tải lên nếu vượt quá hạn mức, đồng thời kiểm soát tốc độ tải về hoặc kích thước tệp tối đa cho mỗi lần gửi dựa trên cấu hình gói dịch vụ đã mua.

### Phân quyền truy cập tệp tin trong nhóm trò chuyện mở rộng

Trong các nhóm chat lớn có hàng ngàn thành viên, việc quản lý ai được xem tệp nào trở nên phức tạp. Khi một thành viên mới gia nhập nhóm, họ có được phép xem các tệp đã gửi trước đó hay không? Ngược lại, khi một thành viên rời nhóm, quyền truy cập của họ vào các tệp cũ sẽ được xử lý như thế nào? Bài toán này giúp bạn luyện tập cách thiết kế bảng phân quyền (ACL) và cách tối ưu hóa truy vấn để kiểm tra quyền hạn mỗi khi có yêu cầu tải tệp.

### Quản lý tệp tin đính kèm cho hệ thống hỗ trợ khách hàng (Ticket System)

Trong hệ thống chăm sóc khách hàng, tệp tin đính kèm thường đi kèm với các yêu cầu hỗ trợ. Một tệp có thể được gửi bởi khách hàng qua email, sau đó được nhân viên phản hồi qua cổng chat trực tuyến. Bài toán yêu cầu sự đồng bộ về dữ liệu tệp tin giữa nhiều kênh liên lạc khác nhau nhưng vẫn phải đảm bảo tệp đó gắn liền với một mã yêu cầu nhất định. Việc tổ chức thư mục lưu trữ vật lý trên server cũng cần được tính toán để dễ dàng sao lưu và phục hồi theo từng giai đoạn thời gian.

### Tìm kiếm và lọc tệp tin nâng cao trong kho lưu trữ chung

Sau một thời gian dài trao đổi, số lượng tệp tin trong một cuộc hội thoại có thể lên đến hàng vạn. Người dùng cần một giao diện để lọc nhanh các tệp theo định dạng (như hình ảnh, tài liệu, video), theo người gửi hoặc theo khoảng thời gian cụ thể. Bài toán này đòi hỏi việc thiết kế chỉ mục (indexing) dữ liệu hiệu quả và cách lưu trữ thông tin tệp sao cho việc tìm kiếm từ khóa trong tên tệp hoặc các thẻ đánh dấu đạt tốc độ cao nhất mà không làm quá tải cơ sở dữ liệu chính.
