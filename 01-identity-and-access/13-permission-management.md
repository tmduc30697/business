# Permission management

### Quản lý phân quyền cho hệ thống thương mại điện tử đa cửa hàng

Trong mô hình này, một hệ thống lớn chứa nhiều cửa hàng khác nhau. Bạn cần giải quyết bài toán làm sao để một người dùng có thể là chủ cửa hàng A với toàn quyền điều hành nhưng đồng thời chỉ là khách hàng bình thường ở cửa hàng B. Hệ thống phải phân tách được quyền hạn theo phạm vi thực thể, đảm bảo hành động xóa sản phẩm của người dùng tại cửa hàng này không ảnh hưởng đến dữ liệu của cửa hàng khác. Việc thiết kế cần chú trọng vào bảng trung gian kết hợp giữa người dùng, vai trò và định danh của cửa hàng.

### Hệ thống quản trị nội dung báo chí với quy trình phê duyệt nghiêm ngặt

Bài toán này tập trung vào các trạng thái của dữ liệu gắn liền với quyền hạn của từng vị trí như phóng viên, biên tập viên và tổng biên tập. Phóng viên chỉ có quyền tạo và chỉnh sửa bài viết của chính mình ở trạng thái nháp. Biên tập viên có quyền xem bài viết của tất cả phóng viên trong chuyên mục được giao nhưng không được phép xuất bản lên trang chủ. Tổng biên tập là người duy nhất có quyền nhấn nút xuất bản và gỡ bài. Điều này đòi hỏi thiết kế hệ thống quyền dựa trên cả chức năng lẫn trạng thái của đối tượng dữ liệu.

### Phân quyền linh hoạt cho ứng dụng quản lý dự án SaaS

Đây là bài toán về việc cho phép người dùng tự định nghĩa vai trò tùy chỉnh. Thay vì chỉ có các vai trò cứng như Quản trị viên hay Thành viên, chủ sở hữu dự án có thể tạo ra vai trò mới như Người xem tạm thời và tích chọn các quyền cụ thể như xem danh sách công việc, bình luận nhưng không được thay đổi thời hạn. Thách thức ở đây là cấu trúc database phải lưu trữ danh sách các quyền dưới dạng nguyên tử để dễ dàng kiểm tra ở tầng API trước khi thực hiện các tác vụ ghi vào cơ sở dữ liệu.

### Quản lý quyền truy cập tài liệu trong hệ thống lưu trữ đám mây nội bộ

Bài toán yêu cầu xử lý quyền thừa kế và chia sẻ chi tiết đến từng đối tượng cụ thể. Một thư mục cha có quyền truy cập dành cho phòng nhân sự, nhưng bên trong đó có một tệp tin bảng lương chỉ dành riêng cho trưởng phòng. Ngoài ra, người dùng có thể chia sẻ một tệp tin bất kỳ cho một đồng nghiệp khác ở phòng ban khác với thời hạn truy cập nhất định. Bạn cần thiết kế hệ thống có khả năng kiểm tra quyền theo cấu trúc cây và ưu tiên các quyền được thiết lập trực tiếp trên tài liệu so với quyền thừa kế từ thư mục.

### Hệ thống ngân hàng số với cơ chế xác thực đa cấp cho giao dịch lớn

Trong môi trường tài chính, việc quản lý quyền không chỉ dừng lại ở xem hay sửa mà còn là kiểm soát kép. Đối với các giao dịch chuyển tiền trên một hạn mức nhất định, hệ thống yêu cầu một người lập lệnh và một người khác có quyền phê duyệt lệnh đó. Người lập lệnh không thể tự phê duyệt chính giao dịch của mình. Bài toán này giúp bạn thực hành thiết kế logic phân quyền dựa trên sự phối hợp giữa nhiều tài khoản và ràng buộc điều kiện về giá trị của dữ liệu giao dịch.

### Phân quyền theo vị trí địa lý cho ứng dụng vận tải và logistics

Hệ thống cần quản lý quyền hạn của các điều phối viên dựa trên khu vực địa lý. Điều phối viên khu vực miền Bắc chỉ được xem và xử lý các đơn hàng có điểm đi hoặc điểm đến nằm trong danh sách các tỉnh thành được phân công. Khi một điều phối viên được điều chuyển công tác, hệ thống phải cập nhật quyền truy cập dữ liệu một cách tức thì mà không làm thay đổi cấu trúc vai trò chung của họ. Đây là bài toán điển hình về việc kết hợp giữa RBAC và thuộc tính dữ liệu để lọc kết quả trả về từ phía server.

### Quản trị hệ thống bệnh viện với bảo mật dữ liệu nhạy cảm

Bài toán yêu cầu sự kết hợp giữa vai trò chuyên môn và quyền truy cập tạm thời. Bác sĩ chuyên khoa có quyền xem bệnh án của bệnh nhân trong khoa mình, nhưng nếu một bác sĩ từ khoa khác được mời hội chẩn, họ cần được cấp quyền xem hồ sơ đó trong một khoảng thời gian ngắn. Y tá chỉ được xem thông tin hành chính và chỉ định thuốc nhưng không được xem chi tiết lịch sử tâm lý của bệnh nhân. Thiết kế cần đảm bảo tính bảo mật cực cao và có nhật ký ghi lại mọi lượt truy cập vào dữ liệu nhạy cảm để phục vụ kiểm toán.

### Hệ thống giáo dục trực tuyến với quyền hạn theo khóa học và lớp học

Trong nền tảng này, một giảng viên có thể dạy nhiều khóa học khác nhau và ở mỗi khóa học họ lại có những quyền trợ giảng hoặc giảng chính khác nhau. Sinh viên sau khi thanh toán mới được cấp quyền xem video bài giảng và tải tài liệu. Đặc biệt, hệ thống cần xử lý quyền xem điểm số sao cho sinh viên chỉ thấy điểm của mình, trong khi lớp trưởng có thể thấy danh sách tổng hợp nhưng không được sửa. Việc thiết kế ERD cần giải quyết được mối quan hệ nhiều-nhiều giữa người dùng, khóa học và các hành động cụ thể.
