# Review delete

### Quản lý vòng đời trạng thái của đánh giá

Thay vì xóa vĩnh viễn dữ liệu khỏi cơ sở dữ liệu, hệ thống cần triển khai cơ chế xóa mềm để phục vụ việc đối soát và khôi phục khi cần thiết. Bài toán yêu cầu thiết kế các trạng thái khác nhau cho một đánh giá như đang hiển thị, đã bị người dùng xóa, hoặc bị admin ẩn do vi phạm. Bạn cần giải quyết vấn đề làm sao để các câu lệnh truy vấn lấy danh sách đánh giá không bị chậm đi khi bảng dữ liệu chứa cả các bản ghi đã xóa, đồng thời đảm bảo tính toàn vẹn dữ liệu khi người dùng muốn xóa rồi lại muốn đăng lại đánh giá cho cùng một sản phẩm.

### Kiểm soát quyền hạn và dấu vết thay đổi

Trong một hệ thống thương mại điện tử lớn, không chỉ người mua mà các nhân viên hỗ trợ khách hàng hoặc admin cũng có quyền can thiệp vào đánh giá. Bài toán đặt ra là phải phân quyền chi tiết ai được phép xóa cái gì và lưu lại nhật ký thay đổi. Nếu một admin xóa đánh giá của khách hàng, hệ thống phải ghi nhận lại lý do xóa, thời điểm xóa và ID của người thực hiện. Điều này giúp tránh việc nhân viên tự ý xóa các đánh giá tiêu cực của shop để trục lợi bất chính và cho phép cấp quản lý cao hơn kiểm tra lại các quyết định xóa này.

### Xử lý nhất quán dữ liệu thống kê và điểm xếp hạng

Mỗi khi một đánh giá bị xóa, điểm trung bình của sản phẩm và tổng số lượng đánh giá hiển thị trên giao diện người dùng cần được cập nhật ngay lập tức. Thử thách ở đây là làm sao để đảm bảo con số này luôn chính xác ngay cả khi có hàng nghìn người cùng xóa hoặc đăng đánh giá một lúc. Bạn cần tính toán xem nên tính lại điểm trung bình từ đầu (vốn rất tốn tài nguyên) hay sử dụng các kỹ thuật cộng dồn và trừ bớt, đồng thời xử lý các tình huống lỗi mạng khiến đánh giá đã xóa nhưng điểm số vẫn chưa được cập nhật lại.

### Cơ chế kháng nghị và khôi phục đánh giá bị xóa nhầm

Khi một hệ thống tự động quét từ khóa để xóa các đánh giá vi phạm chính sách, sẽ có tỷ lệ sai sót nhất định dẫn đến việc xóa nhầm các đánh giá hợp lệ. Bài toán yêu cầu thiết kế một quy trình cho phép người dùng gửi yêu cầu kháng nghị. Khi đó, đánh giá không được mất đi mà phải được chuyển vào một khu vực lưu trữ tạm thời. Admin sẽ xem xét yêu cầu và có khả năng khôi phục đánh giá đó về trạng thái ban đầu với đầy đủ các tương tác như lượt thích hoặc các phản hồi đi kèm mà không làm xáo trộn thứ tự hiển thị theo thời gian.

### Ràng buộc xóa theo phân cấp giữa đánh giá và phản hồi

Một đánh giá thường đi kèm với các phản hồi từ phía người bán hoặc các bình luận từ những người mua khác. Vấn đề nảy sinh là khi đánh giá gốc bị xóa bởi người mua hoặc admin, hệ thống sẽ xử lý các phản hồi con đó như thế nào. Bạn cần thiết kế logic để quyết định xem sẽ xóa trắng toàn bộ các phản hồi liên quan, hay giữ lại các phản hồi đó nhưng hiển thị dưới dạng đánh giá gốc không còn tồn tại. Điều này ảnh hưởng trực tiếp đến cấu trúc cây dữ liệu trong database và cách bạn thiết kế các API để lấy dữ liệu phân tầng.

### Giới hạn thời gian và điều kiện để người dùng tự xóa

Để tránh việc người mua thay đổi ý kiến liên tục hoặc bị người bán tác động để xóa các đánh giá thật, hệ thống thường áp dụng các quy tắc kinh doanh nghiêm ngặt. Ví dụ, người dùng chỉ được xóa đánh giá trong vòng 7 ngày kể từ khi đăng, hoặc không được phép xóa nếu đánh giá đó đã được admin xác thực là đánh giá hữu ích. Bài toán này tập trung vào việc thiết kế các bộ lọc và logic kiểm tra điều kiện trước khi thực thi lệnh xóa trên API, đảm bảo tính minh bạch và khách quan cho hệ thống xếp hạng uy tín của sàn.

### Xóa đánh giá hàng loạt và quản lý hàng chờ xử lý

Trong các chiến dịch dọn dẹp dữ liệu rác hoặc khi một tài khoản bị xác định là chuyên đi đánh giá ảo, admin cần thực hiện xóa hàng triệu đánh giá cùng lúc. Việc thực thi các lệnh xóa này trực tiếp trên database chính có thể gây treo hệ thống hoặc làm chậm các giao dịch mua bán khác. Bài toán yêu cầu bạn thiết kế một cơ chế xử lý bất đồng bộ, sử dụng hàng đợi tin nhắn để tách biệt việc tiếp nhận yêu cầu xóa và việc thực thi xóa thực tế trong database, đảm bảo hệ thống vẫn hoạt động mượt mà dưới tải trọng lớn.

### Đồng bộ hóa dữ liệu đánh giá trên các hệ thống lưu trữ đệm

Thông thường, để tăng tốc độ tải trang, thông tin đánh giá được lưu trữ ở nhiều nơi như database quan hệ, search engine như Elasticsearch và các lớp caching như Redis. Khi một đánh giá bị xóa, thách thức lớn nhất là làm sao để dữ liệu biến mất đồng thời ở tất cả các lớp lưu trữ này. Nếu không xử lý tốt, người dùng có thể vẫn tìm thấy đánh giá cũ thông qua thanh tìm kiếm mặc dù nó đã bị xóa ở trang chi tiết sản phẩm. Bạn cần thiết kế chiến lược thu hồi bộ nhớ đệm và cập nhật chỉ mục tìm kiếm sao cho độ trễ là thấp nhất.

### Quản lý tài nguyên hình ảnh và video đi kèm đánh giá

Đánh giá hiện đại thường đi kèm với rất nhiều tệp đa phương tiện dung lượng lớn được lưu trữ trên các dịch vụ lưu trữ đám mây. Khi một bản ghi đánh giá bị xóa trong database, các tệp hình ảnh và video liên quan cũng cần được dọn dẹp để tiết kiệm chi phí lưu trữ và đảm bảo quyền riêng tư của người dùng. Bài toán đặt ra là thiết kế một quy trình dọn dẹp rác định kỳ hoặc các webhook để xóa tệp trên cloud storage sau khi chắc chắn rằng đánh giá đó không còn khả năng khôi phục lại.

### Bảo mật và ngăn chặn tấn công thông qua yêu cầu xóa

Các API xóa đánh giá thường là mục tiêu của các cuộc tấn công nếu không được bảo mật kỹ lưỡng. Kẻ xấu có thể tìm cách thay đổi ID trong yêu cầu để xóa đánh giá của người khác hoặc admin có thể vô tình xóa nhầm toàn bộ dữ liệu nếu câu lệnh không có điều kiện lọc chính xác. Bạn cần thiết kế các lớp bảo mật kiểm tra quyền sở hữu bản ghi một cách chặt chẽ ở mức middleware và xây dựng các cơ chế xác thực đa lớp để đảm bảo rằng một yêu cầu xóa chỉ được thực thi khi nó thực sự hợp lệ và đến từ người có thẩm quyền.
