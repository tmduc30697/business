# Return rejection

### Kiểm soát thời hạn trả hàng theo danh mục sản phẩm

Hệ thống cần xử lý logic từ chối tự động khi khách hàng gửi yêu cầu quá thời gian quy định. Tuy nhiên, thời hạn này không cố định mà thay đổi tùy theo loại mặt hàng. Ví dụ, hàng điện tử chỉ cho phép trả trong vòng 7 ngày kể từ khi nhận hàng thành công, trong khi mặt hàng thời trang có thể lên đến 30 ngày. Bài toán yêu cầu bạn thiết kế cách lưu trữ cấu hình thời gian cho từng danh mục và logic so khớp giữa ngày cập nhật trạng thái đơn hàng thành công với ngày khởi tạo phiếu trả hàng để đưa ra quyết định từ chối ngay lập tức.

### Xác thực tình trạng hàng hóa qua hình ảnh và video minh chứng

Khi khách hàng yêu cầu trả hàng với lý do lỗi sản phẩm, họ phải cung cấp đầy đủ hình ảnh và video mở hộp làm bằng chứng. Nhân viên kho hoặc bộ phận chăm sóc khách hàng sẽ kiểm duyệt các tệp tin này. Nếu hình ảnh mờ, không rõ mã vận đơn hoặc video có dấu hiệu cắt ghép, yêu cầu sẽ bị từ chối. Bài toán này tập trung vào việc quản lý dữ liệu đa phương tiện, các trạng thái phê duyệt trung gian và lưu trữ lý do từ chối cụ thể để phản hồi lại cho khách hàng.

### Đối soát điều kiện tem nhãn và niêm phong sản phẩm

Một trong những lý do từ chối trả hàng phổ biến nhất là sản phẩm đã bị mất tem niêm phong hoặc đã qua sử dụng. Khi hàng được gửi ngược về kho, nhân viên kiểm định sẽ thực hiện đối chiếu mã barcode trên sản phẩm với dữ liệu xuất kho ban đầu. Nếu mã không khớp hoặc tem bảo hành bị rách, hệ thống phải ghi nhận biên bản kiểm định kèm theo các hạng mục vi phạm chính sách. Việc thiết kế cần chú trọng vào quy trình chuyển trạng thái từ yêu cầu đang xử lý sang từ chối sau khi có kết quả kiểm tra vật lý.

### Quản lý danh sách đen các sản phẩm không hỗ trợ đổi trả

Trong thực tế, có những mặt hàng thuộc nhóm hàng tiêu dùng nhanh, đồ lót, hoặc hàng hóa cá nhân hóa theo tên khách hàng sẽ không bao giờ được chấp nhận trả hàng trừ khi có lỗi kỹ thuật cực kỳ nghiêm trọng. Hệ thống phải ngăn chặn việc tạo phiếu trả hàng ngay từ giao diện người dùng dựa trên thuộc tính của sản phẩm trong đơn hàng. Bài toán này giúp bạn rèn luyện tư duy thiết kế các bảng thuộc tính sản phẩm và xây dựng các lớp lọc dữ liệu khi người dùng thao tác với giỏ hàng hoặc đơn hàng cũ.

### Xử lý từ chối trả hàng do lỗi chủ quan từ phía người mua

Nhiều trường hợp khách hàng muốn trả lại sản phẩm do thay đổi ý định hoặc chọn nhầm kích cỡ, nhưng chính sách của cửa hàng lại chỉ hỗ trợ trả hàng do lỗi của nhà sản xuất. Lúc này, hệ thống cần một bộ quy tắc logic để phân loại lý do trả hàng. Nếu lý do thuộc nhóm không được hỗ trợ, API phải trả về thông báo từ chối kèm theo trích dẫn điều khoản chính sách tương ứng. Đây là bài toán tốt để thiết kế bảng danh mục lý do và ánh xạ chúng với các hành động tương ứng trong hệ thống.

### Giới hạn số lần yêu cầu trả hàng trên một đơn hàng

Để tránh việc khách hàng spam hoặc gian lận, hệ thống thường quy định mỗi đơn hàng chỉ được phép tạo yêu cầu trả hàng một lần duy nhất cho một mã sản phẩm. Nếu yêu cầu đầu tiên đã bị từ chối do thiếu bằng chứng, khách hàng có thể được phép bổ sung hoặc bị khóa tính năng tùy theo cấu hình. Bài toán yêu cầu bạn kiểm soát chặt chẽ quan hệ giữa đơn hàng, chi tiết đơn hàng và các bản ghi trong bảng yêu cầu trả hàng để đảm bảo tính toàn vẹn và không xảy ra tình trạng hoàn tiền trùng lặp.

### Quy trình khiếu nại sau khi yêu cầu trả hàng bị từ chối

Sau khi hệ thống hoặc nhân viên đưa ra quyết định từ chối, khách hàng có thể có quyền khiếu nại lên cấp cao hơn trong một khoảng thời gian nhất định. Bài toán này yêu cầu thiết kế luồng công việc phức tạp hơn, nơi một yêu cầu bị từ chối có thể chuyển sang trạng thái đang khiếu nại. Bạn cần lưu trữ lịch sử thay đổi trạng thái, người thực hiện thay đổi và các ghi chú trao đổi giữa người mua và người bán để phục vụ mục đích kiểm soát sau này.

### Từ chối trả hàng dựa trên lịch sử hành vi của người dùng

Một số hệ thống thương mại điện tử lớn áp dụng điểm tín nhiệm cho người dùng. Nếu một tài khoản có tỷ lệ hoàn hàng bất thường hoặc thường xuyên gửi yêu cầu ảo, hệ thống sẽ tự động đưa vào danh sách hạn chế. Khi những người dùng này tạo yêu cầu trả hàng, hệ thống sẽ thực hiện kiểm tra chéo lịch sử và đưa ra quyết định từ chối dựa trên điểm rủi ro. Bài toán này hướng tới việc thiết kế các bảng thống kê hiệu suất người dùng và logic tích hợp giữa dịch vụ quản lý đơn hàng với dịch vụ đánh giá rủi ro.
