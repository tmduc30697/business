# Escrow holding

### Sàn thương mại điện tử đa người bán

Trong mô hình này, người mua thanh toán đơn hàng nhưng tiền không chuyển ngay cho người bán. Hệ thống sẽ giữ tiền trong một tài khoản trung gian. Chỉ khi người mua xác nhận đã nhận hàng thành công và không có nhu cầu đổi trả, hoặc sau một số ngày quy định mà người mua không có phản hồi, tiền mới được giải ngân vào ví của người bán sau khi trừ đi phí sàn. Bài toán này đòi hỏi bạn xử lý logic về luồng tiền luân chuyển giữa nhiều trạng thái của đơn hàng.

### Thuê chuyên gia làm việc tự do

Trên các nền tảng tuyển dụng freelancer, khi một hợp đồng được ký kết, khách hàng phải nạp tiền vào hệ thống cho các cột mốc công việc cụ thể. Tiền sẽ bị khóa lại để đảm bảo khách hàng có đủ khả năng chi trả. Khi freelancer hoàn thành một giai đoạn và gửi sản phẩm, khách hàng kiểm tra và phê duyệt thì tiền mới được giải phóng. Nếu có tranh chấp về chất lượng sản phẩm, hệ thống phải giữ số tiền đó cho đến khi có sự can thiệp của quản trị viên để quyết định hoàn tiền cho khách hay thanh toán cho freelancer.

### Đặt cọc giữ chỗ dịch vụ lưu trú

Khi khách hàng đặt phòng khách sạn hoặc căn hộ, hệ thống sẽ thực hiện việc giữ một khoản tiền đặt cọc từ thẻ của khách. Khoản tiền này không thực sự bị trừ ngay mà được treo trên hệ thống thanh toán. Nếu khách hàng check-in và trả phòng đúng hạn mà không gây hư hại tài sản, khoản đặt cọc sẽ được giải tỏa. Ngược lại, nếu có phát sinh hư hỏng hoặc khách hủy phòng sát giờ, một phần hoặc toàn bộ số tiền ký quỹ sẽ được chuyển cho chủ nhà dựa trên chính sách hủy phòng đã thiết lập.

### Giao dịch mua bán tên miền trực tuyến

Vì tên miền là tài sản số có giá trị cao và dễ bị đánh cắp, việc mua bán cần một bên thứ ba giữ tiền. Người mua chuyển tiền vào hệ thống escrow, sau đó người bán bắt đầu quy trình chuyển quyền sở hữu tên miền (transfer code). Chỉ khi hệ thống xác nhận tên miền đã được chuyển sang tài khoản của người mua thành công thông qua kiểm tra bản ghi WHOIS hoặc API của nhà đăng ký, tiền mới được chuyển cho người bán để kết thúc giao dịch một cách an toàn cho cả hai phía.

### Mua chung bất động sản hoặc đầu tư nhóm

Một nhóm nhà đầu tư cùng góp tiền để mua một tài sản chung. Tiền của từng cá nhân sẽ được nộp vào một tài khoản ký quỹ tổng. Giao dịch mua tài sản chỉ thực sự diễn ra khi tổng số tiền ký quỹ đạt đến con số mục tiêu trong một khoảng thời gian nhất định. Nếu hết thời hạn mà không gom đủ tiền, hệ thống phải tự động thực hiện quy trình hoàn trả tiền từ tài khoản ký quỹ về lại ví cá nhân của từng nhà đầu tư mà không làm thất thoát số dư.

### Dịch vụ bảo trì và sửa chữa thiết bị tại nhà

Người dùng đặt lịch sửa chữa điện lạnh qua ứng dụng và thanh toán trước một khoản phí ước tính. Tiền này được giữ bởi hệ thống. Sau khi thợ đến nhà kiểm tra và cập nhật chi phí thực tế dựa trên linh kiện thay thế, người dùng sẽ xác nhận mức phí cuối cùng trên ứng dụng. Hệ thống sẽ điều chỉnh số tiền đang giữ, thực hiện thanh toán thêm hoặc hoàn trả phần chênh lệch cho người dùng, sau đó mới giải ngân cho thợ sửa chữa để đảm bảo thợ không thu thêm tiền ngoài luồng.

### Đấu giá ngược cho dự án cung ứng vật tư

Các doanh nghiệp tổ chức đấu giá để tìm nhà cung cấp vật tư với giá tốt nhất. Nhà cung cấp muốn tham gia đấu giá phải ký quỹ một khoản tiền bảo lãnh dự thầu. Khoản tiền này bị hệ thống khóa lại trong suốt quá trình đấu giá diễn ra. Đối với những nhà cung cấp không trúng thầu, tiền sẽ được trả lại ngay khi có kết quả. Đối với nhà cung cấp trúng thầu, tiền ký quỹ sẽ tiếp tục được giữ cho đến khi hợp đồng cung ứng chính thức được ký kết để đảm bảo tính cam kết của nhà thầu.

### Thanh toán theo tiến độ xây dựng công trình

Trong các hợp đồng xây dựng dân dụng, chủ nhà không trả hết tiền một lần mà chia làm nhiều đợt. Mỗi đợt thanh toán, chủ nhà chuyển tiền vào hệ thống ký quỹ. Tiền sẽ được giải ngân dần cho đơn vị thi công dựa trên các biên bản nghiệm thu giai đoạn được cả hai bên ký số trên hệ thống. Nếu một giai đoạn thi công không đạt yêu cầu kỹ thuật, tiền vẫn nằm trong tài khoản ký quỹ, buộc đơn vị thi công phải sửa chữa cho đến khi đạt chuẩn mới được nhận thanh toán cho giai đoạn đó.
