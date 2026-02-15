# Background job queue

### Gửi email xác nhận đăng ký và bản tin khuyến mãi hàng loạt

Khi người dùng đăng ký tài khoản thành công, hệ thống cần gửi một email xác thực ngay lập tức. Thay vì bắt người dùng chờ đợi trình duyệt tải xong sau khi hệ thống kết nối với máy chủ email bên thứ ba, ứng dụng sẽ chỉ ghi nhận thông tin đăng ký vào cơ sở dữ liệu và đẩy một thông điệp vào hàng đợi. Một tiến trình chạy ngầm sẽ lấy thông điệp đó ra để thực hiện việc gửi email. Bài toán này đòi hỏi bạn thiết kế cách quản lý trạng thái của email như đang chờ, đã gửi, hoặc gửi lỗi để có thể thực hiện gửi lại nếu cần thiết.

### Xử lý hậu kỳ video và hình ảnh sau khi người dùng tải lên

Trong một ứng dụng mạng xã hội, khi người dùng tải lên một video dung lượng lớn hoặc hình ảnh chất lượng cao, hệ thống cần thực hiện nhiều tác vụ như nén dung lượng, tạo ảnh thu nhỏ, và chuyển đổi định dạng video sang nhiều độ phân giải khác nhau. Các thao tác này tốn rất nhiều tài nguyên máy tính và thời gian. Hệ thống cần phản hồi cho người dùng rằng tệp đang được xử lý và đẩy các yêu cầu này vào hàng đợi để các máy chủ chuyên dụng xử lý dần mà không làm treo ứng dụng chính.

### Trích xuất dữ liệu báo cáo tài chính định kỳ từ tập dữ liệu lớn

Một hệ thống quản lý bán hàng cần cho phép chủ cửa hàng xuất báo cáo doanh thu chi tiết của cả năm dưới dạng tệp Excel hoặc PDF. Việc truy vấn hàng triệu dòng dữ liệu và định dạng tệp tin có thể mất vài phút. Thay vì để yêu cầu HTTP bị hết thời gian chờ, hệ thống sẽ tiếp nhận yêu cầu, cấp một mã tra cứu cho người dùng và thực hiện việc tạo báo cáo dưới nền. Sau khi tệp tin được tạo xong và tải lên kho lưu trữ đám mây, hệ thống sẽ cập nhật trạng thái để người dùng có thể tải về.

### Đồng bộ hóa dữ liệu tồn kho giữa website và các sàn thương mại điện tử

Khi một đơn hàng được thanh toán thành công trên website chính thức, hệ thống cần cập nhật số lượng tồn kho mới lên tất cả các sàn thương mại điện tử khác mà doanh nghiệp đang kinh doanh. Việc kết nối qua API tới nhiều bên thứ ba cùng lúc tiềm ẩn rủi ro về mạng và độ trễ cao. Bài toán này yêu cầu thiết kế một hệ thống hàng đợi có khả năng xử lý tuần tự hoặc song song các yêu cầu đồng bộ, đảm bảo rằng nếu một sàn bị lỗi kết nối thì không ảnh hưởng đến việc cập nhật của các sàn còn lại.

### Quét và kiểm tra nội dung vi phạm bằng trí tuệ nhân tạo

Đối với các nền tảng cho phép đăng tải nội dung tự do, mọi bài viết hoặc bình luận mới cần được kiểm duyệt qua các bộ lọc tự động để phát hiện ngôn từ thù ghét hoặc hình ảnh nhạy cảm. Quá trình kiểm tra này sử dụng các mô hình học máy phức tạp và mất thời gian xử lý. Hệ thống sẽ cho phép nội dung hiển thị tạm thời hoặc để ở trạng thái chờ duyệt, trong khi các worker chạy ngầm thực hiện việc phân tích dữ liệu và cập nhật lại trạng thái hiển thị của nội dung đó dựa trên kết quả kiểm tra.

### Thu thập dữ liệu web và cập nhật giá thị trường tự động

Một ứng dụng so sánh giá cần thu thập thông tin từ hàng trăm website đối thủ theo định kỳ hàng giờ. Việc truy cập và bóc tách dữ liệu từ các trang web này không thể thực hiện trực tiếp từ yêu cầu của người dùng. Hệ thống cần một bộ lập lịch để đẩy hàng loạt các địa chỉ web cần thu thập vào hàng đợi. Các tiến trình worker sẽ nhận nhiệm vụ, thực hiện cào dữ liệu, xử lý nhiễu và cập nhật giá mới vào cơ sở dữ liệu chính để người dùng luôn thấy thông tin mới nhất khi truy cập ứng dụng.

### Xử lý hoàn tiền và đối soát giao dịch ngân hàng

Trong các hệ thống thanh toán, việc xử lý hoàn tiền thường không diễn ra tức thì do phải làm việc qua nhiều lớp trung gian tài chính. Khi người dùng bấm nút hoàn tiền, hệ thống chỉ ghi nhận yêu cầu và đưa vào hàng đợi đối soát. Các tác vụ nền sẽ thực hiện việc gọi vào API của ngân hàng, theo dõi phản hồi và cập nhật số dư ví cho người dùng. Thiết kế ở đây cần chú trọng vào tính chính xác, đảm bảo mỗi tác vụ hoàn tiền chỉ được thực hiện đúng một lần duy nhất để tránh thất thoát tài chính.

### Tự động hóa quy trình chăm sóc khách hàng dựa trên hành vi

Hệ thống cần theo dõi nếu một người dùng đã thêm hàng vào giỏ nhưng không thanh toán sau 2 tiếng, thì tự động gửi một thông báo đẩy kèm mã giảm giá để nhắc nhở. Đây là dạng tác vụ nền dựa trên điều kiện thời gian và sự kiện. Bạn cần thiết kế một cơ chế để quản lý các tác vụ có thời gian thực thi trễ trong tương lai, cho phép hủy bỏ tác vụ nếu người dùng quay lại thanh toán trước khi thời gian chờ kết thúc.
