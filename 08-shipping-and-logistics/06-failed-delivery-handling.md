# Failed delivery handling

### Quản lý nỗ lực giao lại tự động và giới hạn số lần giao

Trong thực tế, một đơn hàng không bao giờ bị hủy ngay chỉ sau một lần giao thất bại. Hệ thống cần ghi nhận lý do thất bại cụ thể từ shipper để quyết định xem có nên tự động lên lịch giao lại vào ngày tiếp theo hay không. Bài toán yêu cầu thiết lập cấu hình số lần giao hàng tối đa cho phép cho mỗi loại mặt hàng hoặc khu vực. Bạn cần xử lý việc cập nhật trạng thái đơn hàng qua từng lần thử và chuyển trạng thái sang chờ xử lý chuyên sâu khi vượt quá ngưỡng quy định.

### Quy trình xác thực lý do giao hàng thất bại bằng bằng chứng hình ảnh

Để tránh việc shipper gian lận hoặc báo cáo sai sự thật, hệ thống yêu cầu mỗi lần cập nhật trạng thái giao không thành công phải đi kèm với tọa độ GPS, hình ảnh chụp thực tế tại địa chỉ giao hàng và mã lý do chuẩn hóa. Bài toán này tập trung vào việc lưu trữ vết lịch sử các lần nỗ lực giao hàng, đối soát vị trí của shipper với địa chỉ của khách hàng trên bản đồ và quản lý tệp tin đa phương tiện đính kèm cho mỗi biên bản giao hàng lỗi.

### Thay đổi thông tin nhận hàng và thời gian hẹn lại từ khách hàng

Khi một đơn hàng không thể giao do khách hàng vắng nhà hoặc sai số điện thoại, hệ thống cần cung cấp một giao diện hoặc quy trình cho phép khách hàng cập nhật lại số điện thoại mới hoặc chọn một khung giờ nhận hàng khác phù hợp hơn. Bài toán đặt ra thách thức về việc đồng bộ dữ liệu giữa thông tin gốc của đơn hàng và thông tin điều chỉnh sau thất bại, đồng thời phải thông báo kịp thời cho đơn vị vận chuyển về sự thay đổi này để tối ưu lộ trình.

### Điều phối lưu kho tạm thời và chuyển hoàn đơn hàng

Khi đơn hàng đã thử giao nhiều lần thất bại, nó sẽ được đưa về kho gần nhất để lưu trữ trong một khoảng thời gian chờ xử lý thay vì chuyển hoàn ngay lập tức về người gửi. Bài toán yêu cầu quản lý vị trí lưu kho tạm thời, thời gian lưu kho tối đa và logic chuyển đổi trạng thái từ lưu kho sang lệnh chuyển hoàn chính thức. Điều này đòi hỏi việc quản lý vòng đời đơn hàng giữa các kho trung chuyển và kho của người bán.

### Tính toán và phân bổ chi phí vận chuyển phát sinh khi giao lại

Mỗi lần giao lại hoặc chuyển hoàn đều phát sinh chi phí nhân công và xăng xe. Bài toán yêu cầu hệ thống phải xác định xem chi phí cho lần giao thứ hai, thứ ba sẽ do người mua, người bán hay đơn vị vận chuyển chịu trách nhiệm dựa trên lý do thất bại. Bạn cần thiết kế logic để tính toán phí ship phát sinh, cập nhật vào tổng tiền thanh toán của đơn hàng hoặc tạo ra các phiếu thu bổ sung để phục vụ công tác đối soát tài chính sau này.

### Xử lý quy trình chuyển hoàn và kiểm kê hàng trả về

Khi một đơn hàng chính thức bị chuyển hoàn, quy trình không kết thúc ở việc hàng rời khỏi kho vận chuyển. Hệ thống cần theo dõi lộ trình hàng quay về kho của người bán, ghi nhận trạng thái hàng hóa khi trả về có còn nguyên vẹn hay không. Bài toán này bao gồm việc tạo vận đơn ngược, quản lý xác nhận nhận hàng trả về từ phía người bán và xử lý các tranh chấp phát sinh nếu hàng hóa bị hư hỏng trong quá trình vận chuyển qua lại.

### Hệ thống thông báo và tương tác thời gian thực giữa các bên

Để giảm thiểu tỷ lệ chuyển hoàn, hệ thống cần có cơ chế gửi thông báo tự động qua tin nhắn hoặc ứng dụng cho cả người mua và người bán ngay khi một nỗ lực giao hàng thất bại. Bài toán yêu cầu thiết kế luồng gửi tin thông báo lý do chi tiết, cung cấp nút bấm để người mua xác nhận giao lại ngay lập tức và cho phép người bán theo dõi tỷ lệ giao hàng lỗi của từng khu vực để đưa ra quyết định can thiệp kịp thời.

### Phân tích và dự báo tỷ lệ giao hàng không thành công theo khu vực

Dựa trên dữ liệu lịch sử về các đơn hàng không thành công, hệ thống cần cung cấp dữ liệu đầu vào để phân tích các điểm nóng có tỷ lệ giao lỗi cao. Bài toán này yêu cầu cấu trúc dữ liệu cho phép truy vấn nhanh theo mã bưu điện, loại lý do thất bại phổ biến và hiệu suất của từng nhân viên giao hàng. Đây là cơ sở để thiết kế các thuật toán gợi ý cảnh báo sớm cho người bán trước khi họ gửi hàng đi đến những khu vực có rủi ro giao thất bại cao.
