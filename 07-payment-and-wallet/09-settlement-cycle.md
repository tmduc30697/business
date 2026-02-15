# Settlement cycle

### Quản lý cấu hình chu kỳ thanh toán linh hoạt theo từng nhóm người bán

Trong một nền tảng Marketplace lớn, không phải tất cả người bán đều áp dụng chung một quy tắc nhận tiền. Hệ thống cần cho phép thiết lập các gói đối soát khác nhau như gói tiêu chuẩn T+7, gói ưu tiên T+3 cho các nhà bán hàng có uy tín cao, hoặc thậm chí là T+30 cho các sản phẩm dễ xảy ra tranh chấp. Bài toán đặt ra là làm thế nào để lưu trữ và áp dụng chính xác các cấu hình này vào hàng triệu giao dịch mỗi ngày mà vẫn đảm bảo tính nhất quán khi người bán thay đổi gói dịch vụ giữa chừng.

### Xử lý đối soát tự động cho các đơn hàng có trạng thái phức tạp

Chu kỳ thanh toán thường bắt đầu từ khi đơn hàng hoàn thành, nhưng thực tế có rất nhiều trường hợp phát sinh sau đó. Ví dụ, một đơn hàng T+7 đã giao thành công nhưng khách hàng yêu cầu trả hàng vào ngày thứ 6, hoặc đơn hàng bị khiếu nại và chuyển sang trạng thái tranh chấp. Hệ thống đối soát phải có cơ chế tạm giữ tiền (Hold) hoặc điều chỉnh ngày thanh toán dự kiến dựa trên các sự kiện thực tế từ đơn vị vận chuyển và bộ phận chăm sóc khách hàng để tránh thất thoát tiền cho nền tảng.

### Tính toán phí sàn và các khoản khấu trừ trước khi thanh toán

Số tiền thực nhận của người bán không bao giờ bằng tổng giá trị đơn hàng. Trước khi thực hiện lệnh chuyển tiền, hệ thống phải tự động tính toán và khấu trừ các loại phí bao gồm phí hoa hồng sàn, phí vận chuyển, phí thanh toán qua thẻ, và các khoản thuế thu nhập cá nhân theo quy định. Bài toán này đòi hỏi việc thiết kế bảng ghi nhật ký dòng tiền cực kỳ chi tiết để người bán có thể tra cứu chính xác tại sao họ nhận được con số cuối cùng như vậy.

### Đối soát dòng tiền đa tiền tệ và chênh lệch tỷ giá

Đối với các sàn giao dịch xuyên biên giới, người mua có thể thanh toán bằng USD nhưng người bán lại muốn nhận tiền bằng VND. Chu kỳ thanh toán T+14 vô tình tạo ra rủi ro về biến động tỷ giá trong khoảng thời gian chờ. Hệ thống cần xác định thời điểm chốt tỷ giá để chuyển đổi tiền tệ, đồng thời ghi nhận các khoản chênh lệch phát sinh vào báo cáo tài chính để đảm bảo số dư giữa tài khoản trung gian của sàn và số tiền thực tế chuyển cho người bán luôn khớp nhau.

### Xử lý truy thu và bù trừ công nợ từ các kỳ thanh toán trước

Có những trường hợp người bán bị phạt do vi phạm chính sách hoặc phát sinh hoàn tiền cho một đơn hàng đã được thanh toán từ kỳ trước. Khi đó, tài khoản của người bán sẽ có số dư âm. Hệ thống cần có cơ chế ghi nợ và tự động bù trừ số tiền này vào kỳ thanh toán tiếp theo khi có đơn hàng mới phát sinh. Nếu sau một thời gian nhất định người bán không có đơn hàng mới, hệ thống phải kích hoạt quy trình nhắc nợ hoặc xử lý công nợ xấu.

### Quản lý hạn mức thanh toán và gom lô chuyển tiền số lượng lớn

Việc chuyển tiền nhỏ lẻ cho từng đơn hàng ngay khi hết thời gian đối soát sẽ gây tốn kém chi phí giao dịch ngân hàng và quá tải hệ thống. Bài toán thực tế là phải gom tất cả các đơn hàng đủ điều kiện thanh toán của một người bán trong một chu kỳ (ví dụ gom tất cả đơn T+7 của tuần trước) thành một lệnh chuyển tiền duy nhất. Hệ thống cần quản lý các đợt thanh toán (Payout Batches), trạng thái phản hồi từ ngân hàng và xử lý các trường hợp lệnh chuyển tiền bị lỗi hoặc bị từ chối.

### Theo dõi lịch sử thay đổi trạng thái dòng tiền và kiểm toán

Để phục vụ mục đích minh bạch và kiểm toán, mọi thay đổi của một đồng tiền trong hệ thống từ lúc khách thanh toán cho đến lúc tiền rời khỏi tài khoản sàn đều phải được lưu vết. Bài toán yêu cầu thiết kế các bảng lưu trữ dưới dạng nhật ký sự kiện, cho phép truy xuất nhanh chóng trạng thái của một đơn hàng tại bất kỳ thời điểm nào: đang chờ đối soát, đã đủ điều kiện, đang xử lý chuyển tiền, hay đã thanh toán thành công.

### Xử lý đối soát thủ công và điều chỉnh sai lệch số dư

Dù hệ thống tự động đến đâu vẫn luôn có những trường hợp sai lệch số liệu giữa đơn vị vận chuyển, cổng thanh toán và sàn. Hệ thống cần cung cấp các công cụ cho nhân viên vận hành để tạo ra các điều chỉnh thủ công như cộng thêm tiền bồi thường cho người bán do mất hàng hoặc trừ tiền do sai lệch cân nặng. Các bút toán điều chỉnh này phải được ưu tiên xử lý trong kỳ đối soát gần nhất và có minh chứng đi kèm để đảm bảo tính pháp lý.
