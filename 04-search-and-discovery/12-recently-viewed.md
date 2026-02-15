# Recently viewed

### Tối ưu hóa hiệu năng truy vấn cho sàn thương mại điện tử lớn

Trong một hệ thống có hàng triệu người dùng và hàng chục triệu lượt xem mỗi ngày, việc lưu trữ mọi hành động vào cơ sở dữ liệu quan hệ truyền thống sẽ gây ra nghẽn cổ chai nghiêm trọng. Bài toán đặt ra là thiết kế một hệ thống đệm sử dụng các cấu trúc dữ liệu lưu trữ trên RAM để ghi lại lịch sử xem của người dùng theo thời gian thực. Hệ thống cần đảm bảo tốc độ phản hồi dưới mười mil giây khi người dùng quay lại trang chủ, đồng thời phải có cơ chế đồng bộ dữ liệu ngược lại vào cơ sở dữ liệu chính một cách không đồng bộ để tránh mất dữ liệu khi hệ thống gặp sự cố.

### Quản lý giới hạn bộ nhớ và tự động dọn dẹp lịch sử

Mỗi người dùng thường chỉ quan tâm đến khoảng mười đến hai mươi sản phẩm xem cuối cùng. Việc lưu trữ vô hạn lịch sử xem không chỉ gây tốn tài nguyên mà còn làm giảm trải nghiệm người dùng vì thông tin bị loãng. Bạn cần thiết kế một logic lưu trữ theo dạng danh sách liên kết hoặc hàng đợi có kích thước cố định cho mỗi tài khoản. Khi danh sách đạt ngưỡng tối đa, hệ thống phải tự động loại bỏ phần tử cũ nhất để nhường chỗ cho sản phẩm mới. Điều này đòi hỏi thiết kế bảng dữ liệu hoặc cấu trúc lưu trữ sao cho việc chèn mới và xóa cũ diễn ra với độ phức tạp thấp nhất.

### Đồng bộ hóa trạng thái xem giữa người dùng ẩn danh và người dùng đăng nhập

Một kịch bản phổ biến là người dùng dạo quanh cửa hàng khi chưa đăng nhập, sau đó mới thực hiện đăng nhập vào hệ thống. Bài toán yêu cầu thiết kế cơ chế để hợp nhất danh sách các sản phẩm đã xem được lưu trữ tạm thời trong phiên trình duyệt hoặc cookie với danh sách đã lưu trong tài khoản chính thức. Bạn phải xử lý các trường hợp trùng lặp sản phẩm, sắp xếp lại thứ tự thời gian xem sao cho chính xác nhất và đảm bảo rằng trải nghiệm của người dùng không bị gián đoạn hay mất dấu vết những món đồ họ vừa quan tâm trước đó.

### Phân tích xu hướng và cá nhân hóa danh mục gợi ý

Dữ liệu về sản phẩm đã xem không chỉ dùng để hiển thị lại mà còn là đầu vào quan trọng cho các công cụ gợi ý. Bài toán ở đây là thiết kế cấu trúc dữ liệu sao cho có thể dễ dàng thống kê được tần suất một sản phẩm được xem trong một khoảng thời gian nhất định bởi các nhóm đối tượng khác nhau. Hệ thống cần hỗ trợ các truy vấn phức tạp để trích xuất hành vi người dùng, từ đó giúp bộ phận Marketing biết được sản phẩm nào đang thu hút sự chú ý nhưng chưa chuyển đổi được thành đơn hàng, phục vụ cho việc gửi thông báo khuyến mãi đích danh.

### Xử lý dữ liệu sản phẩm biến động về trạng thái và giá cả

Khi hiển thị danh sách đã xem, thông tin về sản phẩm như giá bán hoặc trạng thái còn hàng có thể đã thay đổi so với lúc người dùng xem lần đầu. Bài toán yêu cầu thiết kế API và Database sao cho danh sách trả về luôn phản ánh trạng thái mới nhất của sản phẩm thay vì dữ liệu cũ được lưu trong lịch sử. Bạn cần tính toán xem nên thực hiện việc kết nối các bảng dữ liệu ngay tại thời điểm truy vấn hay sử dụng kỹ thuật lưu trữ dữ liệu dư thừa để tăng tốc độ hiển thị, đồng thời xử lý kịch bản nếu một sản phẩm trong lịch sử đã bị xóa khỏi hệ thống.

### Phân vùng dữ liệu theo thời gian để lưu trữ lịch sử dài hạn

Đối với các hệ thống yêu cầu lưu trữ lịch sử xem trong vòng một năm để phục vụ báo cáo cuối năm, dung lượng dữ liệu sẽ tăng trưởng cực kỳ nhanh. Bài toán là thiết kế kiến trúc cơ sở dữ liệu theo dạng phân mảnh hoặc chia nhỏ các bảng theo tháng hoặc theo quý. Việc này giúp cho các thao tác đọc và ghi hằng ngày chỉ diễn ra trên các bảng nhỏ gọn, trong khi vẫn cho phép các tác vụ phân tích dữ liệu lớn có thể quét qua toàn bộ lịch sử mà không làm ảnh hưởng đến hiệu năng chung của toàn bộ trang web.

### Theo dõi thời gian xem và mức độ tương tác chi tiết

Đôi khi việc chỉ lưu mã sản phẩm là chưa đủ, hệ thống cần biết người dùng đã dừng lại ở sản phẩm đó bao lâu hoặc họ có thực hiện hành động phóng to ảnh hay đọc bình luận hay không. Bài toán yêu cầu thiết kế một lược đồ dữ liệu linh hoạt để lưu trữ các thuộc tính bổ sung này. Điều này giúp hệ thống xác định được mức độ quan tâm thực sự của người dùng để sắp xếp thứ tự ưu tiên trong danh sách xem gần đây, ví dụ như đưa những sản phẩm được xem lâu hơn hoặc có tương tác nhiều hơn lên đầu danh sách.

### Bảo mật và quyền riêng tư dữ liệu hành vi người dùng

Dữ liệu về lịch sử xem sản phẩm được coi là thông tin nhạy cảm về thói quen tiêu dùng. Bài toán đặt ra là thiết kế hệ thống phân quyền và mã hóa dữ liệu sao cho ngay cả khi cơ sở dữ liệu bị lộ, thông tin hành vi của người dùng vẫn được bảo vệ. Ngoài ra, hệ thống cần có chức năng cho phép người dùng chủ động xóa từng mục hoặc toàn bộ lịch sử xem của mình. Bạn cần thiết kế logic xóa sao cho dữ liệu được loại bỏ triệt để khỏi các tầng bộ nhớ đệm lẫn cơ sở dữ liệu vật lý để tuân thủ các quy định về quyền riêng tư.

### Tích hợp đa nền tảng và đồng bộ thời gian thực

Người dùng có thể xem sản phẩm trên ứng dụng di động nhưng sau đó lại quay lại bằng máy tính cá nhân. Bài toán là thiết kế một hệ thống Backend tập trung và các Webhook hoặc cơ chế đẩy thông báo để đảm bảo rằng danh sách sản phẩm đã xem luôn đồng nhất trên mọi thiết bị ngay lập tức. Bạn cần xử lý xung đột dữ liệu khi người dùng mở ứng dụng trên hai thiết bị cùng một lúc và thực hiện các hành động xem sản phẩm khác nhau, đảm bảo trình tự thời gian cuối cùng là chính xác nhất.

### Hiển thị danh sách theo ngữ cảnh và bộ lọc danh mục

Thay vì chỉ hiển thị một danh sách phẳng gồm tất cả sản phẩm, người dùng muốn lọc lại những sản phẩm đã xem thuộc một danh mục cụ thể như đồ điện tử hoặc thời trang. Bài toán yêu cầu thiết kế API hỗ trợ các tham số lọc và phân trang mạnh mẽ dựa trên lịch sử xem. Bạn cần cấu trúc các chỉ mục trong cơ sở dữ liệu sao cho việc tìm kiếm và lọc trong hàng nghìn bản ghi lịch sử của một người dùng diễn ra nhanh chóng, ngay cả khi kết hợp với các điều kiện về thương hiệu, tầm giá hoặc đánh giá của sản phẩm đó.
