# User management

### Quản lý thông tin hồ sơ và trạng thái hoạt động của tài khoản

Admin cần một giao diện danh sách để theo dõi toàn bộ người dùng trong hệ thống với các thông tin cơ bản như tên đăng nhập, email, số điện thoại và ngày tham gia. Quan trọng nhất là mỗi tài khoản phải gắn liền với một trạng thái cụ thể như đang hoạt động, bị khóa tạm thời hoặc chưa kích hoạt email. Hệ thống phải cho phép admin thay đổi trạng thái này ngay lập tức để ngăn chặn các tài khoản vi phạm truy cập vào ứng dụng.

### Tìm kiếm và lọc người dùng theo nhiều tiêu chí kết hợp

Trong một hệ thống có hàng vạn người dùng, việc tìm kiếm thủ công là không thể. Bài toán đặt ra là thiết kế một bộ lọc đa năng cho phép admin tìm kiếm theo từ khóa tên hoặc email, đồng thời lọc theo khoảng ngày đăng ký, theo hạng thành viên hoặc theo tỉnh thành cư trú. Dữ liệu trả về từ API cần được phân trang chặt chẽ để đảm bảo hiệu năng hệ thống không bị treo khi dữ liệu quá lớn.

### Phân quyền người dùng dựa trên vai trò và quyền hạn chi tiết

Hệ thống không chỉ có người dùng thông thường mà còn có nhiều cấp độ quản trị khác nhau như biên tập viên, quản lý kho hoặc chăm sóc khách hàng. Mỗi vai trò này chỉ được phép truy cập vào một số tính năng nhất định. Admin cấp cao nhất phải có khả năng tạo ra các vai trò mới, gán danh sách các quyền cụ thể cho vai trò đó và sau đó áp dụng vai trò này cho một hoặc nhiều người dùng trong hệ thống.

### Lưu vết lịch sử thay đổi thông tin và nhật ký hoạt động

Để đảm bảo tính minh bạch và bảo mật, mọi hành động chỉnh sửa thông tin người dùng của admin hoặc chính người dùng đó đều phải được ghi lại. Ví dụ, khi admin thay đổi số điện thoại của một khách hàng, hệ thống cần lưu lại ai là người thực hiện, thay đổi vào lúc nào, giá trị cũ là gì và giá trị mới là gì. Điều này giúp ích cho việc tra soát khi có sự cố hoặc tranh chấp xảy ra.

### Quản lý xác thực đa yếu tố và khôi phục mật khẩu từ phía quản trị

Khi người dùng gặp sự cố về đăng nhập như quên mật khẩu hoặc mất thiết bị xác thực hai lớp, admin cần có công cụ để hỗ trợ. Bài toán yêu cầu thiết kế các tính năng cho phép admin gửi email đặt lại mật khẩu thủ công, tạm thời tắt xác thực hai lớp cho một tài khoản cụ thể hoặc bắt buộc người dùng phải đổi mật khẩu trong lần đăng nhập kế tiếp vì lý do bảo mật.

### Quản lý liên kết tài khoản mạng xã hội và định danh duy nhất

Người dùng hiện nay thường đăng nhập thông qua Google, Facebook hoặc Apple ID. Hệ thống cần quản lý việc một tài khoản duy nhất có thể liên kết với nhiều phương thức đăng nhập khác nhau. Admin cần xem được tài khoản đó đang liên kết với những nền tảng nào và có khả năng hủy liên kết một nền tảng cụ thể nếu người dùng yêu cầu hoặc phát hiện dấu hiệu bị tấn công từ phía nền tảng thứ ba đó.

### Quản lý hạng thành viên và tích điểm thưởng tự động

Dựa trên hành vi mua hàng hoặc tương tác, người dùng sẽ được phân vào các hạng như Đồng, Bạc, Vàng. Admin cần có công cụ để xem tổng điểm tích lũy, lịch sử cộng trừ điểm và có quyền điều chỉnh điểm thủ công trong các trường hợp đặc biệt. Hệ thống cần tự động cập nhật hạng thành viên khi điểm đạt ngưỡng quy định, đồng thời cho phép admin thiết lập các quy tắc nâng hạng trong trang quản trị.

### Xử lý yêu cầu xóa tài khoản và quyền được quên theo quy định bảo mật

Theo các quy định về quyền riêng tư, người dùng có quyền yêu cầu xóa bỏ hoàn toàn thông tin cá nhân khỏi hệ thống. Tuy nhiên, các dữ liệu liên quan đến hóa đơn hoặc giao dịch tài chính vẫn phải giữ lại vì mục đích kế toán. Bài toán này yêu cầu thiết kế cơ chế xóa mềm hoặc ẩn danh hóa dữ liệu người dùng sao cho thông tin cá nhân biến mất nhưng cấu trúc dữ liệu của các báo cáo tài chính liên quan không bị phá vỡ.
