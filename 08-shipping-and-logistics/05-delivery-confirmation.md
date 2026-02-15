# Delivery confirmation

### Hệ thống xác thực bằng mã OTP và chữ ký số

Trong bài toán này, đơn hàng chỉ được coi là thành công khi shipper nhập đúng mã OTP do người mua cung cấp tại thời điểm giao hàng. Ngoài ra, hệ thống cần lưu trữ tọa độ GPS của shipper lúc nhấn xác nhận và hình ảnh chữ ký số của người mua trên ứng dụng di động. Bạn cần giải quyết việc đối soát giữa tọa độ thực tế và địa chỉ giao hàng dự kiến để phát hiện các trường hợp gian lận giao hàng khống.

### Xử lý webhook từ các đơn vị vận chuyển trung gian

Khi tích hợp với nhiều hãng vận chuyển khác nhau như GHTK, GHN hay Viettel Post, hệ thống của bạn nhận các gói dữ liệu webhook thông báo trạng thái. Bài toán đặt ra là làm thế nào để chuẩn hóa các trạng thái khác nhau từ nhiều bên về một trạng thái duy nhất trong hệ thống của bạn. Đồng thời, hệ thống phải xử lý được tình trạng webhook gửi đến sai thứ tự hoặc bị gửi lặp lại nhiều lần mà không làm sai lệch lịch sử hành trình đơn hàng.

### Quy trình khiếu nại và hoàn trả khi giao hàng thất bại

Không phải lúc nào cập nhật giao hàng thành công từ shipper cũng chính xác. Bài toán này tập trung vào luồng phản hồi từ người mua nếu họ nhận được thông báo thành công nhưng thực tế chưa nhận được hàng. Bạn cần thiết kế logic để tạm dừng việc thanh toán cho nhà bán hàng, mở một phiên khiếu nại, và cho phép các bên đăng tải bằng chứng bằng hình ảnh hoặc video để bộ phận CSKH phân xử.

### Xác nhận giao hàng tự động cho sản phẩm kỹ thuật số

Đối với các mặt hàng như thẻ cào, mã phần mềm hoặc khóa học trực tuyến, việc giao hàng diễn ra ngay lập tức qua email hoặc tin nhắn. Bài toán yêu cầu hệ thống phải tự động xác nhận giao hàng thành công ngay khi hệ thống bên thứ ba phản hồi mã code đã được gửi đi. Bạn cần chú trọng vào việc thiết kế các trạng thái chờ xử lý và xử lý ngoại lệ khi hệ thống gửi code bị lỗi nhưng tiền của người dùng đã bị trừ.

### Hệ thống xác nhận giao hàng cho mô hình Dropshipping

Trong mô hình này, người bán không giữ hàng mà đơn hàng được chuyển thẳng từ kho của nhà cung cấp đến người mua. Bài toán yêu cầu sự đồng bộ trạng thái giữa ba bên: Nhà cung cấp cập nhật vận đơn, đơn vị vận chuyển cập nhật hành trình, và hệ thống của người bán phải cập nhật tiến độ cho khách hàng. Thách thức nằm ở việc quản lý ID đơn hàng chéo giữa các hệ thống và cập nhật trạng thái thời gian thực.

### Quản lý giao hàng chặng cuối và xác nhận tại điểm nhận hàng

Thay vì giao tận nhà, người mua chọn nhận hàng tại các điểm tập kết hoặc tủ đồ thông minh. Bài toán yêu cầu hệ thống ghi nhận xác nhận giao hàng thành công theo hai giai đoạn: Giai đoạn một khi shipper bỏ hàng vào tủ, và giai đoạn hai khi người dùng nhập mã mở tủ để lấy hàng. Việc thiết kế database phải tách biệt được thời điểm hàng đến điểm nhận và thời điểm khách hàng thực sự sở hữu món hàng.

### Đối soát tài chính sau khi xác nhận giao thành công

Sau khi đơn hàng được xác nhận thành công, hệ thống cần kích hoạt luồng đối soát dòng tiền. Tiền từ đơn vị vận chuyển thu hộ (COD) phải được đối chiếu với doanh thu của người bán sau khi trừ đi phí vận chuyển, phí sàn và thuế. Bạn cần thiết kế các bảng lưu trữ giao dịch tài chính sao cho có thể truy xuất ngược lại đúng mã vận đơn và thời điểm xác nhận giao hàng để phục vụ việc kiểm toán hàng tháng.

### Theo dõi hiệu suất giao hàng và cam kết thời gian (SLA)

Bài toán này yêu cầu hệ thống ghi lại mốc thời gian xác nhận giao hàng thành công để so sánh với thời gian cam kết ban đầu. Nếu việc xác nhận diễn ra chậm hơn dự kiến, hệ thống phải tự động tính toán mức bồi thường cho khách hàng hoặc trừ điểm uy tín của đơn vị vận chuyển. Bạn cần thiết kế cách lưu trữ dữ liệu lịch sử sao cho việc truy vấn báo cáo hiệu suất theo tuần, tháng của hàng nghìn đơn hàng vẫn đạt tốc độ tối ưu.
