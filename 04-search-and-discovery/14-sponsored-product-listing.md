# Sponsored product listing

### Quản lý chiến dịch quảng cáo và ngân sách linh hoạt

Bài toán này tập trung vào việc cho phép người bán hàng tạo các chiến dịch quảng cáo cho danh mục sản phẩm của họ. Mỗi chiến dịch cần có ngày bắt đầu, ngày kết thúc và một mức ngân sách tổng hoặc ngân sách theo ngày. Hệ thống phải đảm bảo rằng khi ngân sách chạm ngưỡng giới hạn, các sản phẩm thuộc chiến dịch đó sẽ ngay lập tức ngừng hiển thị ở vị trí ưu tiên để tránh phát sinh chi phí ngoài ý muốn cho người bán.

### Đấu thầu từ khóa và xếp hạng hiển thị thời gian thực

Đây là bài toán cốt lõi về cơ chế hiển thị. Người bán sẽ đặt giá thầu cho các từ khóa cụ thể mà họ muốn sản phẩm của mình xuất hiện khi khách hàng tìm kiếm. Khi có một truy vấn tìm kiếm từ người dùng, hệ thống cần tính toán dựa trên mức giá thầu và điểm chất lượng của sản phẩm để quyết định sản phẩm nào được nằm ở các vị trí "vàng". Việc thiết kế phải tính đến chuyện hàng ngàn người cùng đấu thầu một từ khóa phổ biến.

### Theo dõi hành vi tương tác và tính phí theo lượt click

Hệ thống cần ghi lại chính xác mỗi khi một sản phẩm tài trợ được hiển thị và đặc biệt là khi người dùng nhấn vào sản phẩm đó. Bài toán này yêu cầu sự chính xác tuyệt đối trong việc ghi nhận dữ liệu để thực hiện trừ tiền từ ví của người bán theo mô hình trả phí cho mỗi lượt nhấp chuột. Ngoài ra, hệ thống cần có cơ chế phát hiện và ngăn chặn các hành vi gian lận như nhấn chuột ảo hoặc nhấn liên tục từ một địa chỉ mạng.

### Phân bổ vị trí hiển thị xen kẽ với kết quả tự nhiên

Trong một trang kết quả tìm kiếm hoặc trang danh mục, các sản phẩm quảng cáo không được chiếm toàn bộ không gian mà phải được phân bổ xen kẽ với các sản phẩm không quảng cáo theo một tỷ lệ nhất định. Bài toán đặt ra là làm sao để thiết kế API trả về danh sách sản phẩm sao cho các vị trí quảng cáo được đặt đúng quy tắc nhưng vẫn đảm bảo trải nghiệm người dùng không bị khó chịu bởi quá nhiều nội dung tài trợ.

### Hệ thống báo cáo hiệu suất chi tiết cho người bán

Người bán cần biết số tiền họ bỏ ra có mang lại hiệu quả hay không. Bài toán này yêu cầu thiết kế cấu trúc lưu trữ dữ liệu sao cho có thể truy xuất nhanh chóng các chỉ số như số lượt hiển thị, số lượt nhấn, tỷ lệ chuyển đổi thành đơn hàng và doanh thu mang lại từ quảng cáo. Dữ liệu cần được tổng hợp theo nhiều chiều thời gian khác nhau như theo giờ, theo ngày hoặc theo tháng để người bán tối ưu hóa chiến dịch.

### Quản lý ví điện tử và nạp tiền quảng cáo

Để quảng cáo được chạy, người bán cần có một tài khoản thanh toán hoặc ví điện tử nội bộ trong hệ thống. Bài toán này bao gồm việc thiết kế các luồng giao dịch nạp tiền, đóng băng tiền khi chiến dịch đang chạy và trừ tiền thực tế sau khi phát sinh tương tác. Mọi giao dịch tài chính phải được lưu vết rõ ràng để đối soát và xử lý khiếu nại, đồng thời phải đảm bảo tính nhất quán dữ liệu ở mức cao nhất.

### Tự động hóa việc chọn sản phẩm quảng cáo theo kho hàng

Một vấn đề thực tế là sản phẩm đang chạy quảng cáo có thể hết hàng trong kho. Bài toán yêu cầu hệ thống phải có sự kết nối chặt chẽ với quản lý kho vận. Nếu một sản phẩm không còn khả năng cung ứng, hệ thống quảng cáo phải tự động ẩn sản phẩm đó khỏi các vị trí ưu tiên và thông báo cho người bán, nhằm tránh việc lãng phí ngân sách quảng cáo cho những sản phẩm mà khách hàng không thể mua được.

### Đề xuất mức giá thầu thông minh dựa trên thị trường

Để hỗ trợ người bán mới, hệ thống cần cung cấp các gợi ý về mức giá thầu tối thiểu hoặc mức giá thầu cạnh tranh cho từng từ khóa hoặc ngành hàng. Bài toán này yêu cầu xử lý và phân tích dữ liệu lịch sử từ các phiên đấu thầu trước đó để đưa ra con số khuyến nghị. Hệ thống cần phản ánh được sự biến động của thị trường vào các dịp cao điểm như lễ tết khi nhu cầu quảng cáo tăng cao.
