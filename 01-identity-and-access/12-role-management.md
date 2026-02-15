# Role management

### Hệ thống quản thương mại điện tử đa kênh

Trong mô hình này, hệ thống cần phân biệt rõ nhóm người mua hàng, người bán hàng cá nhân và đội ngũ quản trị sàn. Người mua chỉ có quyền xem sản phẩm và quản lý đơn hàng của chính mình. Người bán được phép đăng tải sản phẩm, quản lý kho hàng và xem báo cáo doanh thu của gian hàng họ sở hữu. Trong khi đó, Admin tổng có quyền kiểm duyệt sản phẩm của tất cả các người bán, khóa tài khoản vi phạm và thiết lập các mã giảm giá áp dụng toàn sàn.

### Quản lý bệnh viện và hồ sơ y tế điện tử

Bài toán này đòi hỏi sự phân quyền cực kỳ nghiêm ngặt để đảm bảo quyền riêng tư. Bác sĩ có quyền xem bệnh án và kê đơn thuốc cho bệnh nhân. Y tá có quyền cập nhật các chỉ số sinh tồn và thực hiện y lệnh nhưng không được thay đổi chẩn đoán ban đầu. Nhân viên lễ tân chỉ được tiếp cận thông tin hành chính để làm thủ tục nhập viện và thanh toán viện phí. Ngoài ra, bệnh nhân cũng là một role trong hệ thống với quyền xem kết quả xét nghiệm và lịch hẹn của bản thân.

### Hệ thống quản lý nội dung tòa soạn báo điện tử

Đây là một quy trình làm việc theo chuỗi với các vai trò khác nhau. Phóng viên có quyền tạo bản thảo và sửa bài viết của mình nhưng không được tự xuất bản. Biên tập viên có quyền chỉnh sửa bài viết của phóng viên và gửi lên cấp cao hơn. Tổng biên tập là người duy nhất có quyền phê duyệt cuối cùng để bài viết hiển thị công khai trên trang chủ. Ngoài ra còn có role kỹ thuật viên chuyên quản lý bố cục trang web và role cộng tác viên với các giới hạn về số lượng bài viết được tạo trong tháng.

### Nền tảng học trực tuyến Learning Management System

Hệ thống cần quản lý sự tương tác giữa học viên, giảng viên và quản lý đào tạo. Học viên chỉ được truy cập vào các khóa học mà họ đã thanh toán hoặc đăng ký. Giảng viên có quyền tải lên bài giảng, tạo bài kiểm tra và chấm điểm cho học viên trong lớp học mà họ phụ trách. Quản lý đào tạo có quyền xem báo cáo tổng quan về tiến độ học tập của tất cả các lớp, tạo danh mục khóa học mới và chỉ định giảng viên vào các lớp học cụ thể.

### Hệ thống quản lý dự án và phân quyền theo phòng ban

Trong một công ty, mỗi nhân viên có thể thuộc một phòng ban nhưng tham gia vào nhiều dự án khác nhau. Trưởng phòng có quyền xem tất cả các dự án của nhân viên dưới quyền. Quản lý dự án có toàn quyền điều phối công việc và nhân sự trong phạm vi dự án đó. Thành viên dự án chỉ thấy các nhiệm vụ được giao cho mình. Một điểm khó của bài toán này là việc xử lý các quyền hạn chồng chéo khi một nhân viên vừa là thành viên của dự án này vừa là quản lý của dự án khác.

### Ứng dụng quản lý chuỗi cửa hàng nhượng quyền

Hệ thống này cần quản lý theo phân cấp từ trung ương đến địa phương. Chủ sở hữu chuỗi có quyền xem báo cáo tài chính tổng hợp từ tất cả các chi nhánh. Quản lý cửa hàng chỉ xem được dữ liệu bán hàng, tồn kho và danh sách nhân viên tại đúng chi nhánh của mình. Nhân viên bán hàng tại quầy chỉ được sử dụng chức năng tạo hóa đơn và kiểm tra giá sản phẩm. Khi một nhân viên được điều chuyển từ cửa hàng này sang cửa hàng khác, hệ thống phải cho phép cập nhật lại phạm vi truy cập dữ liệu một cách nhanh chóng.

### Phần mềm quản trị doanh nghiệp ERP cho quy trình mua sắm

Bài toán tập trung vào việc phê duyệt theo cấp bậc và hạn mức tài chính. Nhân viên mua hàng có quyền tạo yêu cầu mua sắm thiết bị. Nếu giá trị yêu cầu dưới một ngưỡng nhất định, chỉ cần trưởng bộ phận phê duyệt. Nếu giá trị lớn, yêu cầu phải được chuyển tiếp đến giám đốc tài chính để xem xét. Kế toán có vai trò xác nhận thanh toán sau khi hàng đã về kho. Mỗi bước trong quy trình đều yêu cầu vai trò tương ứng phải ký duyệt điện tử và hệ thống cần lưu lại lịch sử thay đổi để phục vụ kiểm toán.

### Nền tảng SaaS quản lý dịch vụ khách hàng

Đây là mô hình phân quyền cho dịch vụ thuê phần mềm dưới dạng dịch vụ. Một tài khoản doanh nghiệp đăng ký sử dụng sẽ có vai trò là chủ sở hữu tổ chức với quyền thiết lập cấu hình hệ thống và thanh toán hóa đơn. Chủ sở hữu này có thể tạo ra các nhóm hỗ trợ khách hàng và chỉ định các trưởng nhóm. Nhân viên hỗ trợ chỉ được tiếp cận các yêu cầu hỗ trợ được phân bổ cho nhóm của mình. Đặc biệt, hệ thống cần hỗ trợ việc tùy chỉnh quyền để khách hàng có thể tự tạo ra các vai trò mới phù hợp với cấu trúc nhân sự riêng của họ.
