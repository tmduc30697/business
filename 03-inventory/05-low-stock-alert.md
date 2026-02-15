# Low stock alert

### Quản lý ngưỡng tồn kho đa cấp độ theo biến thể sản phẩm

Trong thực tế, một sản phẩm thường có nhiều phiên bản khác nhau như kích thước hoặc màu sắc. Bài toán đặt ra là hệ thống phải cho phép cấu hình ngưỡng báo động riêng biệt cho từng biến thể thay vì áp dụng một con số chung cho toàn bộ sản phẩm. Ví dụ, một chiếc áo thun size L có tốc độ bán nhanh hơn size S, nên người quản lý cần đặt mức cảnh báo cho size L cao hơn để kịp thời nhập hàng. Bạn cần thiết kế cách lưu trữ cấu hình này sao cho linh hoạt và tối ưu khi truy vấn kiểm tra trạng thái kho hàng của hàng ngàn biến thể cùng lúc.

### Cảnh báo tồn kho theo địa điểm kho hàng đa chi nhánh

Đối với các doanh nghiệp có chuỗi cửa hàng hoặc nhiều kho bãi, việc tồn kho tổng thấp không quan trọng bằng việc tồn kho tại một chi nhánh cụ thể bị cạn kiệt. Bài toán yêu cầu hệ thống phải theo dõi số lượng hàng tại từng kho riêng lẻ và gửi cảnh báo dựa trên ngưỡng thiết lập cho từng địa điểm đó. Thách thức ở đây là việc xử lý logic khi một mặt hàng hết ở kho này nhưng vẫn còn ở kho khác, và làm thế nào để thông báo đúng cho quản lý của chi nhánh có liên quan thay vì gửi thông báo rác cho toàn bộ hệ thống.

### Dự báo ngưỡng an toàn dựa trên tốc độ bán hàng trung bình

Thay vì để người dùng nhập một con số cố định một cách cảm tính, hệ thống cần tính toán ngưỡng tồn kho tối thiểu dựa trên dữ liệu bán hàng lịch sử và thời gian chờ nhập hàng từ nhà cung cấp. Bài toán này đòi hỏi việc lưu trữ các chỉ số về tốc độ tiêu thụ hàng ngày và thời gian quay vòng vốn. Hệ thống sẽ tự động cập nhật hoặc gợi ý cấu hình lại ngưỡng cảnh báo khi xu hướng thị trường thay đổi, giúp tránh tình trạng đọng vốn do đặt ngưỡng quá cao hoặc đứt hàng do đặt ngưỡng quá thấp.

### Hệ thống hàng đợi xử lý thông báo và tránh spam cảnh báo

Khi một sản phẩm chạm ngưỡng tối thiểu, nếu mỗi đơn hàng mới phát sinh đều kích hoạt một thông báo thì người bán sẽ bị ngập trong email hoặc tin nhắn. Bài toán thực tế là thiết kế một cơ chế kiểm soát trạng thái cảnh báo để chỉ gửi thông báo lần đầu khi kho xuống dưới ngưỡng, và chỉ gửi lại sau khi hàng đã được nhập thêm hoặc sau một khoảng thời gian nhất định. Điều này liên quan trực tiếp đến việc thiết kế các bảng lưu vết trạng thái thông báo và quản lý hàng đợi gửi tin (queue) để không làm treo hệ thống khi có biến động kho hàng lớn.

### Phân quyền và kênh nhận thông báo tùy chỉnh cho nhân sự

Trong một doanh nghiệp lớn, không phải ai cũng cần nhận mọi cảnh báo kho. Bài toán yêu cầu thiết kế hệ thống phân quyền sao cho nhân viên phụ trách nhóm hàng nào thì chỉ nhận cảnh báo về nhóm hàng đó. Ngoài ra, người dùng có thể tùy chọn nhận thông báo qua nhiều kênh khác nhau như email, tin nhắn ứng dụng, hoặc webhook đẩy về các nền tảng quản lý nội bộ như Slack hay Telegram. Việc thiết kế database phải thể hiện được mối quan hệ giữa người dùng, danh mục sản phẩm quản lý và các phương thức liên lạc tương ứng.

### Xử lý tồn kho ảo và giữ hàng trong giỏ hàng

Một vấn đề nhức nhối trong thương mại điện tử là hàng vẫn còn trên kệ nhưng đã bị khách hàng thêm vào giỏ hàng hoặc đang chờ thanh toán. Bài toán yêu cầu hệ thống cảnh báo phải phân biệt được giữa tồn kho vật lý và tồn kho khả dụng. Cảnh báo cần được kích hoạt dựa trên số lượng hàng thực tế có thể bán sau khi đã trừ đi các đơn hàng đang treo. Điều này đòi hỏi thiết kế cơ sở dữ liệu phải quản lý chặt chẽ các trạng thái giữ hàng (lock) và thời gian hết hạn của giỏ hàng để đảm bảo tính chính xác của dữ liệu thời gian thực.

### Tích hợp quy trình đặt hàng tự động từ nhà cung cấp

Khi cảnh báo tồn kho thấp được kích hoạt, bước tiếp theo thường là tạo đơn nhập hàng. Bài toán thực tế là kết nối hệ thống cảnh báo với danh mục nhà cung cấp để tự động soạn thảo một đơn mua hàng (Purchase Order) với số lượng bù đắp đủ mức tồn kho an toàn. Bạn cần thiết kế các bảng liên kết giữa sản phẩm, nhà cung cấp, đơn giá nhập gần nhất và quy chuẩn đóng gói để hệ thống có thể tự động điền các thông tin cần thiết ngay khi gửi cảnh báo cho bộ phận thu mua.

### Theo dõi lịch sử thay đổi ngưỡng và hiệu quả cảnh báo

Để tối ưu hóa vận hành, chủ doanh nghiệp cần biết ai đã thay đổi ngưỡng cảnh báo và liệu ngưỡng đó có hiệu quả hay không. Bài toán này tập trung vào việc thiết kế hệ thống log (audit trail) chi tiết về các thay đổi cấu hình và thống kê số lần sản phẩm bị rơi vào tình trạng hết hàng dù đã có cảnh báo. Dữ liệu này giúp doanh nghiệp đánh giá được độ trễ của bộ phận kho và tính chính xác của các thiết lập hiện tại, từ đó cải thiện quy trình vận hành trong tương lai.
