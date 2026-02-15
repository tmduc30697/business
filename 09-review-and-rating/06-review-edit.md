# Review edit

### Quản lý vòng đời và thời gian hiệu lực của bản chỉnh sửa

Hệ thống cần kiểm soát việc người mua chỉ được phép sửa đánh giá trong vòng bảy ngày kể từ khi bài đánh giá gốc được đăng tải. Bài toán này yêu cầu bạn thiết kế logic để xác định trạng thái có thể chỉnh sửa của một bản ghi dựa trên dấu mốc thời gian. Bạn sẽ phải xử lý việc lưu trữ thời điểm tạo đơn hàng, thời điểm đánh giá lần đầu và tính toán thời gian còn lại theo thời gian thực để hiển thị nút Chỉnh sửa trên giao diện người dùng một cách chính xác.

### Lưu vết lịch sử thay đổi nội dung đánh giá

Khi người dùng thay đổi nội dung hoặc số sao, hệ thống không được ghi đè hoàn toàn dữ liệu cũ mà cần lưu trữ lại các phiên bản trước đó để phục vụ mục đích minh bạch. Bạn cần thiết kế cấu trúc dữ liệu sao cho có thể truy xuất nhanh chóng phiên bản hiện tại để hiển thị cho khách hàng, đồng thời vẫn giữ được danh sách các bản nháp cũ kèm theo lý do chỉnh sửa nếu có. Điều này rất quan trọng trong việc đối soát khi có tranh chấp xảy ra giữa người mua và người bán.

### Kiểm soát quy trình kiểm duyệt lại nội dung sau khi sửa

Mỗi khi người mua cập nhật nội dung mới, bài đánh giá đó có thể phải trải qua quy trình kiểm duyệt lại từ phía quản trị viên để đảm bảo không vi phạm quy định về ngôn từ hoặc hình ảnh nhạy cảm. Bài toán đặt ra là trạng thái của đánh giá sẽ thay đổi như thế nào trong lúc chờ duyệt. Bạn cần quyết định xem sẽ hiển thị nội dung cũ hay tạm ẩn bài đánh giá cho đến khi nội dung mới được phê duyệt, và làm thế nào để thông báo trạng thái này cho người dùng.

### Đồng bộ điểm xếp hạng trung bình của sản phẩm

Việc thay đổi số sao trong bản chỉnh sửa đánh giá sẽ tác động trực tiếp đến tổng điểm trung bình của sản phẩm và cửa hàng. Nếu một sản phẩm có hàng triệu đánh giá, việc tính toán lại điểm trung bình mỗi khi có người sửa đánh giá có thể gây áp lực lên hệ thống. Bạn cần thiết kế giải pháp để cập nhật điểm số này một cách hiệu quả, đảm bảo tính nhất quán dữ liệu mà không làm chậm tốc độ tải trang của người dùng khác.

### Quản lý tệp tin đa phương tiện trong bản chỉnh sửa

Người dùng không chỉ sửa văn bản mà còn có thể thêm mới, xóa bỏ hoặc thay thế các hình ảnh và video trong bài đánh giá của họ. Bài toán này yêu cầu bạn xử lý việc lưu trữ tệp tin vật lý trên máy chủ hoặc các dịch vụ lưu trữ đám mây. Bạn phải giải quyết vấn đề dọn dẹp các tệp tin cũ không còn được sử dụng để tối ưu không gian lưu trữ, đồng thời đảm bảo đường dẫn của các tệp tin mới được cập nhật chính xác trong cơ sở dữ liệu.

### Chặn sửa đánh giá sau khi người bán đã phản hồi

Để đảm bảo tính công bằng và tránh việc người mua thay đổi nội dung làm cho phản hồi trước đó của người bán trở nên vô nghĩa hoặc gây hiểu lầm, hệ thống cần có cơ chế khóa tính năng chỉnh sửa ngay khi người bán đã gửi lời phản hồi. Bạn cần thiết kế mối quan hệ giữa các bảng sao cho có thể kiểm tra nhanh điều kiện chặn này trước khi cho phép hành động sửa đổi được thực hiện ở phía máy chủ.

### Giới hạn số lần chỉnh sửa tối đa

Để ngăn chặn việc người dùng lạm dụng tính năng này để quấy rối người bán hoặc làm nhiễu loạn dữ liệu, hệ thống chỉ cho phép mỗi đánh giá được sửa tối đa ba lần. Bạn cần thiết kế một cơ chế đếm số lần thay đổi và lưu trữ vào cơ sở dữ liệu. Khi đạt đến giới hạn, hệ thống phải tự động vô hiệu hóa quyền truy cập vào API chỉnh sửa và hiển thị thông báo phù hợp cho người dùng trên ứng dụng.

### Xử lý tranh chấp và khôi phục phiên bản đánh giá

Trong một số trường hợp đặc biệt, quản trị viên hệ thống cần có quyền khôi phục lại một phiên bản đánh giá cũ nếu phát hiện phiên bản mới vi phạm chính sách hoặc bị báo cáo là gian lận. Bài toán này yêu cầu bạn thiết kế các API quản trị có khả năng duyệt qua lịch sử các phiên bản và thực hiện thao tác đảo ngược dữ liệu. Việc này đòi hỏi tính toàn vẹn dữ liệu cực cao để không làm sai lệch các thống kê liên quan đến sản phẩm.
