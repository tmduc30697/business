# Marketing banner CMS

### Lập lịch hiển thị tự động cho các chiến dịch quảng bá

Một hệ thống banner cần cho phép nhân viên marketing thiết lập trước thời gian bắt đầu và thời gian kết thúc cho từng hình ảnh quảng cáo. Ví dụ, banner khuyến mãi Tết phải tự động xuất hiện vào đúng 00:00 ngày mùng 1 và tự động gỡ bỏ vào 23:59 ngày mùng 5. Bài toán này yêu cầu thiết kế database có các trường dữ liệu về thời gian và logic truy vấn API chỉ lấy những banner đang nằm trong khoảng thời gian hiệu lực so với thời điểm hiện tại của hệ thống.

### Quản lý vị trí hiển thị đa dạng trên nhiều trang và nền tảng

Hệ thống không chỉ hiển thị một banner duy nhất mà phải quản lý nhiều vị trí khác nhau như banner chính đầu trang chủ, banner nhỏ ở trang danh mục sản phẩm, hoặc banner ở trang thanh toán. Ngoài ra, cùng một vị trí nhưng trên ứng dụng di động có thể cần kích thước hình ảnh khác so với trên trình duyệt máy tính. Bạn cần thiết kế cấu trúc dữ liệu để phân loại vị trí, định danh trang và hỗ trợ nhiều định dạng file hoặc liên kết hình ảnh tương ứng với từng loại thiết bị của người dùng.

### Ưu tiên hiển thị và sắp xếp thứ tự banner trong một vùng

Tại một vị trí hiển thị như slide đầu trang chủ, marketing thường muốn chạy cùng lúc 5 đến 7 banner khác nhau theo một thứ tự ưu tiên nhất định. Bài toán đặt ra là làm thế nào để quản lý số thứ tự hiển thị này trong database. Khi một banner mới được chèn vào giữa hoặc một banner cũ bị xóa đi, hệ thống cần có cơ chế cập nhật lại thứ tự của các banner còn lại để đảm bảo dữ liệu luôn nhất quán và API trả về đúng mảng dữ liệu đã được sắp xếp.

### Phân mục tiêu hiển thị banner theo nhóm đối tượng khách hàng

Để tối ưu hóa chuyển đổi, doanh nghiệp muốn hiển thị banner khác nhau cho các nhóm khách hàng khác nhau. Ví dụ, khách hàng chưa đăng nhập sẽ thấy banner mời đăng ký thành viên, còn khách hàng VIP sẽ thấy banner ưu đãi độc quyền. Điều này đòi hỏi thiết kế hệ thống phải có sự liên kết giữa bảng banner và bảng định nghĩa phân khúc khách hàng. API lấy banner lúc này cần nhận thêm tham số về định danh người dùng để thực hiện lọc các nội dung phù hợp nhất.

### Giới hạn số lượt hiển thị hoặc lượt nhấn cho mỗi banner

Một số chiến dịch quảng cáo chỉ được phép hiển thị tối đa 10.000 lần hoặc nhận đủ 500 lượt nhấn vào hình ảnh là phải dừng lại để bảo vệ ngân sách. Hệ thống cần một cơ chế để đếm và lưu trữ các chỉ số này theo thời gian thực. Đây là bài toán thú vị về việc thiết kế bảng lưu trữ số liệu thống kê và cách cập nhật dữ liệu liên tục mà không gây nghẽn hệ thống khi có lượng truy cập lớn đổ dồn vào cùng một lúc.

### Quản lý phiên bản và lịch sử thay đổi nội dung banner

Trong quá trình vận hành, nhân viên có thể thay đổi hình ảnh hoặc đường dẫn liên kết của banner nhiều lần. Hệ thống cần lưu lại lịch sử ai đã sửa gì vào lúc nào, hoặc cho phép khôi phục lại phiên bản banner của tuần trước nếu cần thiết. Việc thiết kế database để hỗ trợ lưu trữ phiên bản (versioning) sẽ giúp hệ thống trở nên chuyên nghiệp và an toàn hơn, tránh việc mất dữ liệu khi có sai sót trong thao tác quản trị.

### Điều hướng liên kết linh hoạt từ banner đến các trang đích

Mỗi banner khi nhấn vào có thể dẫn người dùng đến một sản phẩm cụ thể, một danh mục hàng hóa, một bài viết tin tức, hoặc thậm chí là một liên kết ngoài hệ thống. Bài toán thiết kế ở đây là làm sao để lưu trữ loại liên kết và giá trị đích một cách linh hoạt. Bạn cần xây dựng một cấu trúc dữ liệu cho phép định nghĩa loại đối tượng đích để phía ứng dụng hoặc website có thể xử lý điều hướng chính xác mà không cần phải viết code riêng cho từng banner.

### Thiết lập trạng thái phê duyệt nội dung trước khi xuất bản

Để tránh sai sót về mặt hình ảnh hoặc thông tin nhạy cảm, banner sau khi được nhân viên thiết kế tạo ra phải trải qua bước phê duyệt của cấp quản lý mới được chính thức hiển thị lên website. Hệ thống cần quản lý các trạng thái như Bản nháp, Chờ phê duyệt, Đã phê duyệt, hoặc Đã từ chối. Logic API trả về cho người dùng cuối tuyệt đối không được bao gồm các banner chưa ở trạng thái Đã phê duyệt, ngay cả khi chúng đang trong thời gian hiệu lực.
