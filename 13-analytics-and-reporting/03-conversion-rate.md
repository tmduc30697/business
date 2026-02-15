# Conversion rate

### Theo dõi phễu bán hàng đa bước trong thương mại điện tử

Hệ thống cần ghi lại hành trình của người dùng qua các bước cụ thể bao gồm xem sản phẩm, thêm vào giỏ hàng, nhập thông tin thanh toán và cuối cùng là xác nhận đặt hàng thành công. Bài toán đặt ra là làm thế nào để thiết kế cơ sở dữ liệu lưu trữ các sự kiện này theo thời gian thực sao cho có thể truy vấn được tỷ lệ người dùng rơi rụng tại mỗi bước. Việc này giúp doanh nghiệp xác định được bước nào trong quy trình đang gây khó khăn cho khách hàng để tối ưu hóa giao diện hoặc kỹ thuật.

### Đo lường hiệu quả chuyển đổi của từng chiến dịch quảng cáo

Doanh nghiệp chạy nhiều chiến dịch marketing từ các nguồn khác nhau như Facebook, Google và Email. Khi người dùng truy cập vào website thông qua các đường dẫn có chứa tham số theo dõi, hệ thống phải ghi nhận nguồn gốc của người dùng đó và gắn thẻ cho các hành động chuyển đổi phát sinh sau đó. Thử thách ở đây là thiết kế hệ thống định danh người dùng và phiên truy cập để báo cáo chính xác chiến dịch nào mang lại tỷ lệ mua hàng cao nhất so với chi phí bỏ ra.

### Tỷ lệ chuyển đổi dựa trên thử nghiệm phân tách giao diện người dùng

Để tối ưu hóa trải nghiệm, đội ngũ phát triển thực hiện hiển thị hai phiên bản giao diện khác nhau cho hai nhóm người dùng ngẫu nhiên. Hệ thống cần ghi nhận phiên bản mà người dùng đã thấy và theo dõi xem phiên bản nào dẫn đến hành động đăng ký tài khoản nhiều hơn. Bài toán này yêu cầu thiết kế database có khả năng phân đoạn người dùng và đối chiếu kết quả chuyển đổi giữa các nhóm thử nghiệm mà không làm ảnh hưởng đến hiệu năng tải trang.

### Theo dõi tỷ lệ chuyển đổi từ khách vãng lai sang khách hàng đăng ký

Nhiều nền tảng nội dung cho phép người dùng xem thử một số bài viết trước khi yêu cầu đăng ký tài khoản. Hệ thống cần lưu vết các hoạt động của một người dùng chưa đăng nhập thông qua cookie hoặc mã định danh thiết bị. Khi người dùng đó quyết định tạo tài khoản, toàn bộ lịch sử truy cập trước đó phải được liên kết với ID tài khoản mới để tính toán chính xác hành vi nào đã thúc đẩy họ thực hiện việc đăng ký chính thức.

### Phân tích tỷ lệ chuyển đổi theo thời gian thực cho sự kiện Flash Sale

Trong các sự kiện giảm giá chớp nhoáng, lượng truy cập tăng đột biến và doanh nghiệp cần biết ngay lập tức tỷ lệ khách truy cập đang chốt đơn là bao nhiêu để điều chỉnh chiến lược vận hành hoặc hạ tầng máy chủ. Bài toán này tập trung vào việc thiết kế API thu thập sự kiện với độ trễ thấp và hệ thống xử lý dòng dữ liệu để cập nhật các chỉ số chuyển đổi lên bảng điều khiển quản trị theo từng giây hoặc từng phút.

### Đo lường chuyển đổi ngoại tuyến từ các mã QR tại cửa hàng

Một chuỗi cửa hàng bán lẻ đặt các mã QR tại quầy kệ để khách hàng quét và nhận thông tin ưu đãi trực tuyến, sau đó khách dùng ưu đãi đó để mua hàng tại quầy. Hệ thống cần kết nối dữ liệu từ việc quét mã trên điện thoại với dữ liệu hóa đơn tại hệ thống quản lý bán hàng của cửa hàng vật lý. Việc thiết kế database cần giải quyết được sự kết nối giữa hành vi kỹ thuật số và giao dịch thực tế để đánh giá hiệu quả của việc quảng cáo tại điểm bán.

### Tỷ lệ chuyển đổi của hệ thống gợi ý sản phẩm thông minh

Hệ thống đề xuất các sản phẩm liên quan ở cuối mỗi trang chi tiết sản phẩm. Doanh nghiệp muốn biết có bao nhiêu người thực sự nhấn vào các sản phẩm được gợi ý và sau đó tiến hành mua chúng. Bài toán yêu cầu thiết kế database và API sao cho mỗi khi một sản phẩm được hiển thị, nó phải được đánh dấu là có nguồn gốc từ thuật toán gợi ý, từ đó phân tách được doanh thu đến từ việc khách tự tìm kiếm và doanh thu đến từ hệ thống tự động.

### Theo dõi tỷ lệ chuyển đổi đăng ký dịch vụ theo mô hình dùng thử

Đối với các ứng dụng phần mềm dịch vụ, bước chuyển đổi quan trọng nhất là từ người dùng thử miễn phí sang người dùng trả phí sau 7 hoặc 30 ngày. Hệ thống phải quản lý được vòng đời của người dùng qua nhiều trạng thái khác nhau và ghi nhận thời điểm chuyển đổi chính xác. Thiết kế hệ thống cần xử lý được việc đối soát dữ liệu thanh toán từ các bên thứ ba để cập nhật trạng thái chuyển đổi và tính toán tỷ lệ duy trì khách hàng trong dài hạn.
