# Seller approval

### Quản lý các trạng thái trong vòng đời xét duyệt hồ sơ người bán

Khi một người dùng đăng ký trở thành người bán, hồ sơ của họ không được kích hoạt ngay lập tức mà phải trải qua nhiều giai đoạn khác nhau. Bắt đầu từ trạng thái nháp khi người dùng đang điền thông tin, sau đó chuyển sang trạng thái chờ xét duyệt khi họ nhấn gửi. Quản trị viên có thể chuyển hồ sơ sang trạng thái đang kiểm tra, yêu cầu bổ sung thông tin, từ chối hoặc chính thức phê duyệt. Hệ thống cần một cơ chế để quản lý chặt chẽ các bước chuyển đổi trạng thái này, đảm bảo không có bước nào bị nhảy cóc và lưu lại thời điểm chuyển trạng thái để đo lường hiệu suất làm việc của đội ngũ vận hành.

### Lưu trữ và đối soát phiên bản dữ liệu hồ sơ giữa các lần chỉnh sửa

Trong quá trình xét duyệt, người bán thường xuyên được yêu cầu cập nhật lại căn cước công dân hoặc giấy phép kinh doanh do thông tin cũ bị mờ hoặc hết hạn. Hệ thống cần có khả năng lưu trữ nhiều phiên bản khác nhau của cùng một bộ hồ sơ. Khi quản trị viên xem xét, họ phải biết được thông tin nào là mới nhất và có thể xem lại các bản cũ để so sánh sự thay đổi. Bài toán này đòi hỏi việc thiết kế cơ sở dữ liệu sao cho việc truy xuất thông tin hiện tại nhanh chóng nhưng vẫn bảo toàn được lịch sử thay đổi của từng trường dữ liệu cụ thể.

### Phân công hồ sơ cho đội ngũ nhân viên kiểm duyệt theo chuyên môn

Một sàn thương mại điện tử lớn có hàng nghìn hồ sơ đăng ký mỗi ngày, do đó cần phân phối công việc cho nhiều nhân viên kiểm duyệt khác nhau. Một số nhân viên chuyên duyệt hồ sơ cá nhân, trong khi những người khác chuyên về hồ sơ doanh nghiệp hoặc các ngành hàng đặc thù như thực phẩm, dược phẩm. Hệ thống cần cơ chế tự động hoặc thủ công để gán một hồ sơ cụ thể cho một nhân viên nhất định. Nhân viên đó sẽ là người duy nhất có quyền thao tác trên hồ sơ đó cho đến khi hoàn thành hoặc chuyển giao cho người khác, nhằm tránh tình trạng nhiều người cùng xử lý một hồ sơ gây xung đột dữ liệu.

### Quy trình xét duyệt theo cấp bậc đối với các ngành hàng rủi ro cao

Đối với các ngành hàng đặc biệt như điện tử điện máy hoặc mỹ phẩm, hồ sơ người bán cần được xét duyệt qua hai cấp. Sau khi nhân viên sơ cấp kiểm tra tính hợp lệ của giấy tờ, hồ sơ sẽ được đẩy lên cho cấp quản lý cao hơn để ký duyệt cuối cùng về năng lực kinh doanh. Hệ thống cần hỗ trợ luồng công việc đa tầng, trong đó mỗi cấp bậc có quyền hạn khác nhau. Hồ sơ chỉ được coi là thành công và người bán chỉ được phép đăng sản phẩm khi tất cả các cấp liên quan đã phê duyệt đầy đủ theo đúng trình tự quy định.

### Quản lý danh sách lý do từ chối hồ sơ và hướng dẫn khắc phục

Khi từ chối một hồ sơ, quản trị viên không thể chỉ nhấn nút từ chối chung chung mà phải cung cấp lý do cụ thể cho từng hạng mục như ảnh chụp chứng minh nhân dân không rõ nét, tên cửa hàng vi phạm quy định hoặc mã số thuế không tồn tại. Hệ thống cần quản lý một danh mục các lý do từ chối mẫu để nhân viên chọn nhanh, đồng thời cho phép nhập ghi chú chi tiết. Các lý do này phải được hiển thị chính xác cho người bán ở giao diện quản lý của họ để họ biết chính xác mình cần sửa đổi thông tin gì trước khi gửi lại hồ sơ lần sau.

### Tự động hóa kiểm tra thông tin qua tích hợp dịch vụ bên thứ ba

Để giảm tải cho nhân viên vận hành, hệ thống cần tự động gọi các dịch vụ bên ngoài ngay khi người bán nhấn gửi hồ sơ. Ví dụ, hệ thống sẽ gửi mã số thuế sang trang web của tổng cục thuế để kiểm tra trạng thái hoạt động của doanh nghiệp, hoặc kiểm tra xem số điện thoại và email có nằm trong danh sách đen hay không. Kết quả từ các dịch vụ này cần được lưu trữ lại cùng hồ sơ để nhân viên kiểm duyệt có thêm cơ sở ra quyết định. Đây là bài toán về thiết kế API và xử lý bất đồng bộ khi chờ kết quả từ các đơn vị bên thứ ba.

### Giới hạn quyền hạn của người bán theo từng giai đoạn phê duyệt

Trong khi chờ đợi được phê duyệt chính thức, người bán có thể được phép thực hiện một số hành động hạn chế để chuẩn bị trước cho gian hàng. Ví dụ, ngay khi tạo hồ sơ, họ có thể được vào trang quản trị để trang trí gian hàng hoặc đăng sản phẩm ở trạng thái nháp, nhưng không được phép xuất bản sản phẩm cho khách hàng nhìn thấy hoặc tham gia các chương trình khuyến mãi. Hệ thống phân quyền cần dựa trên trạng thái hiện tại của hồ sơ xét duyệt để mở khóa dần các tính năng tương ứng cho người bán, đảm bảo an toàn cho sàn.

### Nhật ký hoạt động chi tiết và kiểm tra dấu vết kiểm duyệt

Để phòng chống gian lận nội bộ hoặc xử lý khiếu nại của người bán, mọi hành động tác động lên hồ sơ đều phải được ghi lại chi tiết. Nhật ký này bao gồm ai là người đã xem hồ sơ, họ xem vào lúc nào, họ đã thay đổi những thông tin gì, và các bình luận nội bộ giữa các nhân viên kiểm duyệt với nhau. Dữ liệu này thường được lưu trữ dưới dạng danh sách sự kiện tuyến tính, gắn liền với định danh của hồ sơ, giúp quản trị viên cấp cao có thể tra cứu lại toàn bộ diễn biến của một trường hợp xét duyệt từ lúc bắt đầu cho đến khi kết thúc.
