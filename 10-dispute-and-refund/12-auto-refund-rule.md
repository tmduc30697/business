# Auto refund rule

### Hoàn tiền khi người bán vi phạm thời gian xác nhận đơn hàng

Trong mô hình Marketplace, khi khách hàng đặt xong một đơn hàng, hệ thống sẽ đặt ra một mốc thời gian phản hồi theo cam kết dịch vụ (SLA) thường là 24 giờ. Nếu trong khoảng thời gian này người bán không nhấn nút xác nhận đơn hoặc không chuyển trạng thái sang chuẩn bị hàng, hệ thống sẽ tự động hủy đơn và hoàn tiền lại cho người khách. Bài toán này yêu cầu bạn quản lý trạng thái đơn hàng theo thời gian thực và một cơ chế quét các đơn hàng quá hạn để kích hoạt lệnh hoàn tiền mà không cần sự can thiệp thủ công từ quản trị viên.

### Tự động xử lý khi khiếu nại trả hàng bị bỏ qua

Khách hàng yêu cầu trả hàng và hoàn tiền vì sản phẩm lỗi, sau đó hệ thống chuyển yêu cầu này đến người bán để đối soát. Quy tắc định sẵn là nếu người bán không đưa ra phản hồi đồng ý hoặc từ chối khiếu nại trong vòng 3 ngày làm việc, hệ thống sẽ mặc định người bán chấp nhận lỗi và tự động thực hiện lệnh hoàn tiền từ ví của người bán sang cho khách hàng. Kịch bản này đòi hỏi thiết kế cơ sở dữ liệu có khả năng lưu trữ các mốc thời gian của từng bước khiếu nại và các cấu hình thời gian linh hoạt cho từng loại ngành hàng khác nhau.

### Hoàn tiền dựa trên dữ liệu cập nhật từ đơn vị vận chuyển

Một đơn hàng được đánh dấu là đang giao nhưng dữ liệu từ phía đối tác vận chuyển cho thấy bưu kiện đã bị thất lạc hoặc không có cập nhật mới trong suốt 7 ngày liên tiếp. Hệ thống sẽ dựa trên API của bên vận chuyển để xác định rủi ro và tự động kích hoạt quy trình hoàn tiền cho khách hàng để đảm bảo trải nghiệm người dùng. Bạn sẽ cần thiết kế các bảng lưu trữ lịch sử vận chuyển (tracking logs) và các bộ quy tắc để trigger hành động hoàn tiền khi các điều kiện về thời gian và trạng thái vận chuyển được thỏa mãn.

### Hủy đơn và hoàn tiền tự động khi hết hàng trong kho

Khách hàng đã thanh toán trước qua thẻ tín dụng nhưng khi hệ thống xử lý kho vận phát hiện sản phẩm bị lỗi hoặc hết hàng thực tế tại kho vật lý. Thay vì chờ nhân viên chăm sóc khách hàng gọi điện, hệ thống sẽ tự động gửi thông báo xin lỗi và thực hiện hoàn tiền ngay lập tức dựa trên thông tin tồn kho vừa cập nhật. Bài toán này tập trung vào sự đồng bộ giữa hệ thống quản lý kho (WMS) và hệ thống thanh toán (Payment Gateway).

### Hoàn tiền một phần tự động khi dịch vụ không đạt chất lượng

Trong các ứng dụng giao đồ ăn, nếu đơn hàng bị giao trễ so với thời gian cam kết ban đầu quá 30 phút, hệ thống sẽ tự động tính toán một tỷ lệ phần trăm đền bù (ví dụ hoàn lại 10% giá trị đơn hàng) vào ví điện tử của khách hàng. Việc này diễn ra tự động ngay khi tài xế nhấn nút hoàn tất đơn hàng và hệ thống nhận thấy thời gian thực tế lớn hơn thời gian dự kiến. Điều này yêu cầu thiết kế logic tính toán linh hoạt và khả năng xử lý giao dịch hoàn tiền một phần.

### Xử lý hoàn tiền tự động cho các gói đăng ký dịch vụ bị lỗi kích hoạt

Khách hàng thanh toán nâng cấp gói thành viên trên một nền tảng học trực tuyến hoặc xem phim, tuy nhiên do lỗi kỹ thuật phía hệ thống mà tài khoản không được nâng cấp thành công sau 15 phút từ lúc thanh toán. Quy tắc tự động sẽ kiểm tra đối chiếu giữa giao dịch thành công tại cổng thanh toán và trạng thái quyền hạn của người dùng trên hệ thống, nếu có sự sai lệch sẽ tự động hoàn trả tiền để tránh khiếu nại. Bạn sẽ cần thiết kế cơ chế đối soát (reconciliation) tự động giữa các service.

### Hoàn tiền khi đơn hàng không được đơn vị vận chuyển tiếp nhận

Sau khi người bán xác nhận đơn hàng và in vận đơn, nếu trong vòng 48 giờ mà đơn vị vận chuyển vẫn chưa quét mã lấy hàng (Pick-up), hệ thống sẽ nhận diện đây là đơn hàng ảo hoặc người bán không có hàng sẵn. Lúc này, quy tắc sẽ tự động chuyển trạng thái đơn hàng về mức hủy và hoàn tiền lại cho khách hàng để giải phóng số tiền đang bị treo. Bài toán này giúp bạn luyện tập cách thiết kế các trigger dựa trên sự kiện (event-driven) giữa nhiều bên liên quan.

### Tự động hoàn tiền cọc khi kết thúc dịch vụ thuê tài sản

Trong các ứng dụng thuê xe điện hoặc thuê pin dự phòng, khách hàng phải đặt cọc một khoản tiền trước. Khi thiết bị được trả lại vào trạm và hệ thống kiểm tra tình trạng thiết bị không có hư hại, lệnh hoàn tiền cọc sẽ được kích hoạt tự động mà không cần sự phê duyệt của con người. Bài toán này đòi hỏi việc quản lý các loại giao dịch đặt cọc và khả năng tích hợp chặt chẽ với dữ liệu phần cứng (IoT) để quyết định việc hoàn tiền.
