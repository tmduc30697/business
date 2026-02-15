# Search history

### Quản lý lịch sử tìm kiếm cá nhân trên sàn thương mại điện tử

Trong một ứng dụng mua sắm, hệ thống cần lưu lại các từ khóa mà người dùng đã nhập vào thanh tìm kiếm để hiển thị lại trong danh sách tìm kiếm gần đây. Bài toán yêu cầu lưu trữ theo thời gian thực, giới hạn số lượng bản ghi hiển thị ví dụ chỉ hiện 10 mục gần nhất và cho phép người dùng xóa từng mục hoặc xóa toàn bộ lịch sử. Bạn cần tính đến việc đồng bộ lịch sử này khi người dùng đăng nhập trên nhiều thiết bị khác nhau như điện thoại và máy tính.

### Gợi ý từ khóa thông minh dựa trên xu hướng tìm kiếm chung

Thay vì chỉ lưu lịch sử của riêng một cá nhân, hệ thống cần tổng hợp dữ liệu từ tất cả người dùng để xác định những từ khóa nào đang được tìm kiếm nhiều nhất trong một khoảng thời gian nhất định. Bài toán này đòi hỏi việc thiết kế bảng dữ liệu sao cho có thể đếm tần suất xuất hiện của từ khóa một cách hiệu quả. Hệ thống sẽ lấy ra danh sách các từ khóa phổ biến để gợi ý cho người dùng ngay cả khi họ chưa nhập bất kỳ ký tự nào vào ô tìm kiếm.

### Hệ thống lưu vết tìm kiếm có phân loại danh mục sản phẩm

Khi người dùng tìm kiếm trong một danh mục cụ thể như Điện thoại hoặc Thời trang, hệ thống cần lưu lại từ khóa kèm theo ngữ cảnh của danh mục đó. Điều này giúp khi người dùng quay lại danh mục Điện thoại, hệ thống sẽ ưu tiên hiển thị các tìm kiếm cũ liên quan đến đồ điện tử thay vì hiển thị tràn lan tất cả lịch sử. Việc thiết kế database ở đây cần chú trọng vào mối quan hệ giữa từ khóa, người dùng và các thực thể danh mục sản phẩm.

### Tối ưu hóa bộ nhớ đệm cho lịch sử tìm kiếm tốc độ cao

Đối với các ứng dụng có hàng triệu người dùng truy cập cùng lúc, việc truy vấn lịch sử tìm kiếm từ cơ sở dữ liệu quan hệ truyền thống sẽ gây ra độ trễ lớn. Bài toán đặt ra là thiết kế một lớp lưu trữ đệm trung gian để phản hồi kết quả tìm kiếm gần đây ngay lập tức khi người dùng chạm vào thanh tìm kiếm. Bạn cần xây dựng cơ chế để dữ liệu mới nhất luôn được cập nhật vào bộ nhớ đệm và các dữ liệu cũ không còn giá trị sẽ tự động bị loại bỏ để tiết kiệm tài nguyên.

### Phân tích hành vi tìm kiếm để cá nhân hóa quảng cáo

Dữ liệu lịch sử tìm kiếm không chỉ để phục vụ người dùng mà còn là nguồn tài nguyên quý giá cho bộ phận marketing. Bài toán yêu cầu lưu trữ thêm các thông tin chi tiết như thời điểm tìm kiếm, vị trí địa lý của người dùng và liệu sau khi tìm kiếm họ có nhấn vào sản phẩm nào không. Từ bảng dữ liệu này, hệ thống sẽ phân loại người dùng vào các nhóm sở thích khác nhau để hiển thị các biểu ngữ quảng cáo phù hợp với nhu cầu thực tế của họ.

### Tính năng tự động hoàn thiện từ khóa từ lịch sử và kho dữ liệu

Khi người dùng bắt đầu gõ những chữ cái đầu tiên, hệ thống cần đối soát nhanh chóng trong kho lịch sử tìm kiếm của chính người dùng đó và kho dữ liệu chung của hệ thống để đưa ra các gợi ý hoàn thiện từ khóa. Bài toán này tập trung vào việc thiết kế API và cấu trúc dữ liệu sao cho việc tìm kiếm theo tiền tố diễn ra cực nhanh, đồng thời phải sắp xếp thứ tự ưu tiên cho các từ khóa mà người dùng thường xuyên sử dụng nhất.

### Quản lý quyền riêng tư và tự động dọn dẹp dữ liệu cũ

Theo quy định về bảo mật dữ liệu, hệ thống không được phép lưu giữ lịch sử tìm kiếm của người dùng vĩnh viễn nếu không cần thiết. Bài toán yêu cầu thiết kế một cơ chế tự động quét và xóa các bản ghi lịch sử đã quá hạn một khoảng thời gian nhất định, ví dụ sau 30 ngày. Ngoài ra, hệ thống cần hỗ trợ chế độ tìm kiếm ẩn danh, nơi mà các từ khóa tìm kiếm sẽ hoàn toàn không được ghi lại vào cơ sở dữ liệu trong suốt phiên làm việc đó.

### Đồng bộ hóa lịch sử tìm kiếm giữa phiên khách và tài khoản chính thức

Người dùng thường tìm kiếm sản phẩm khi chưa đăng nhập, sau đó mới tiến hành đăng nhập vào hệ thống. Bài toán đặt ra là làm thế nào để gộp toàn bộ lịch sử tìm kiếm trong phiên ẩn danh trước đó vào tài khoản chính thức ngay sau khi hành động đăng nhập thành công. Việc này yêu cầu thiết kế database phải quản lý được các mã định danh tạm thời cho trình duyệt và thiết lập quy trình chuyển đổi dữ liệu chính xác để không làm mất thông tin của người dùng.
