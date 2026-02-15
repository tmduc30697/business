# A/B testing

### Phân chia lưu lượng truy cập và duy trì tính nhất quán người dùng

Hệ thống cần chia người dùng vào các nhóm thử nghiệm khác nhau khi họ truy cập vào trang chủ. Ví dụ, 50 phần trăm người dùng thấy nút mua hàng màu đỏ và 50 phần trăm thấy nút màu xanh. Thử thách ở đây là đảm bảo một người dùng cụ thể, dù thoát ra và quay lại sau nhiều ngày trên cùng một thiết bị hoặc tài khoản, vẫn phải luôn thấy đúng phiên bản màu sắc mà họ đã được phân loại ban đầu để tránh gây nhầm lẫn và làm sai lệch kết quả đo lường.

### Thử nghiệm đa biến cho cấu hình giá gói dịch vụ

Một ứng dụng phần mềm muốn thử nghiệm xem mức giá nào sẽ thu hút nhiều lượt đăng ký nhất. Họ tạo ra ba phiên bản: gói cơ bản giá 9 đô la, gói cơ bản giá 12 đô la kèm thêm tính năng phụ, và gói cơ bản giá 15 đô la nhưng cho dùng thử miễn phí một tháng. Bài toán yêu cầu hệ thống phải quản lý được nhiều biến thể cùng lúc trong một chiến dịch, đồng thời ghi nhận chính xác doanh thu tương ứng từ mỗi nhóm để tính toán giá trị trung bình trên mỗi người dùng.

### Phân đoạn đối tượng mục tiêu cho các thử nghiệm đặc thù

Thay vì thử nghiệm trên toàn bộ người dùng, doanh nghiệp chỉ muốn chạy A/B testing nội dung quảng cáo mới cho nhóm khách hàng nữ, độ tuổi từ 18 đến 25 và đang sinh sống tại các thành phố lớn. Hệ thống cần có khả năng lọc điều kiện người dùng trước khi quyết định đưa họ vào nhóm thử nghiệm hay giữ họ ở nhóm mặc định. Điều này đòi hỏi database và API phải kết nối chặt chẽ với thông tin định danh và hành vi của khách hàng.

### Ghi nhận sự kiện chuyển đổi và hành trình hành vi

Để biết phiên bản nào hiệu quả hơn, hệ thống không chỉ ghi lại việc người dùng đã xem phiên bản nào mà còn phải theo dõi chuỗi hành động sau đó. Ví dụ, sau khi xem tiêu đề bài viết phiên bản B, người dùng có nhấn vào đọc chi tiết không, họ có ở lại trang lâu hơn không, và cuối cùng họ có nhấn đăng ký bản tin hay không. Việc thiết kế bảng lưu trữ sự kiện cần tối ưu để có thể truy vấn nhanh chóng mối quan hệ giữa phiên bản thử nghiệm và các hành động chuyển đổi.

### Quản lý vòng đời và trạng thái của các chiến dịch thử nghiệm

Trong thực tế, một hệ thống có thể chạy hàng chục cuộc thử nghiệm cùng lúc trên các trang khác nhau. Bạn cần thiết kế cơ chế để quản lý trạng thái của từng cuộc thử nghiệm như: đang chờ kích hoạt, đang chạy, đã tạm dừng hoặc đã kết thúc. Khi một chiến dịch kết thúc và xác định được phiên bản chiến thắng, hệ thống cần có cơ chế để áp dụng phiên bản đó cho toàn bộ người dùng mà không cần thay đổi mã nguồn ứng dụng một cách thủ công.

### Tránh xung đột giữa các cuộc thử nghiệm chồng chéo

Giả sử có hai nhóm Marketing cùng chạy thử nghiệm trên cùng một trang: một nhóm thử nghiệm màu sắc nút bấm, nhóm kia thử nghiệm nội dung lời chào. Nếu một người dùng rơi vào cả hai thử nghiệm cùng lúc, kết quả đo lường có thể bị nhiễu vì không biết sự chuyển đổi đến từ màu sắc hay từ lời chào. Bài toán đặt ra là thiết kế logic phân lớp hoặc loại trừ để đảm bảo các thử nghiệm không gây ảnh hưởng tiêu cực đến dữ liệu của nhau.

### Phân phối lưu lượng linh hoạt theo thời gian thực

Ban đầu, hệ thống chia đều 50-50 cho hai phiên bản. Tuy nhiên, sau một ngày chạy, phiên bản A tỏ ra kém hiệu quả rõ rệt và gây mất mát doanh thu. Người quản lý muốn điều chỉnh tỷ lệ ngay lập tức xuống còn 10-90 để giảm thiểu rủi ro trong khi vẫn tiếp tục thu thập thêm dữ liệu cho đến khi đủ ý nghĩa thống kê. Hệ thống cần hỗ trợ việc cập nhật cấu hình phân phối lưu lượng mà không cần khởi động lại dịch vụ hoặc làm gián đoạn trải nghiệm người dùng.

### Thu thập dữ liệu kỹ thuật và môi trường thực hiện thử nghiệm

Hiệu quả của một giao diện có thể khác nhau giữa người dùng điện thoại và người dùng máy tính. Bài toán yêu cầu hệ thống A/B testing phải thu thập kèm theo các siêu dữ liệu như loại trình duyệt, hệ điều hành, độ phân giải màn hình và tốc độ mạng tại thời điểm người dùng tiếp cận phiên bản thử nghiệm. Việc này giúp các nhà phân tích dữ liệu có cái nhìn sâu hơn về lý do tại sao một phiên bản lại hoạt động tốt trên môi trường này nhưng lại thất bại trên môi trường khác.
