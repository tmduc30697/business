# Disaster recovery

### Đồng bộ hóa dữ liệu thời gian thực giữa hai vùng Cloud khác nhau

Một nền tảng thương mại điện tử hoạt động chính tại vùng Singapore nhưng cần có một vùng dự phòng tại Tokyo để đề phòng trường hợp toàn bộ trung tâm dữ liệu tại Singapore gặp sự cố vật lý. Bài toán đặt ra là làm thế nào để mọi thay đổi dữ liệu từ đơn hàng, thông tin người dùng đến số lượng tồn kho được sao chép sang vùng dự phòng với độ trễ thấp nhất. Bạn cần thiết kế một hệ thống sao cho khi vùng chính gặp sự cố, vùng dự phòng đã có sẵn dữ liệu gần như mới nhất để sẵn sàng tiếp quản mà không làm mất quá nhiều giao dịch của khách hàng.

### Cơ chế tự động chuyển hướng truy cập khi server chính ngừng hoạt động

Hệ thống ngân hàng số yêu cầu tính sẵn sàng cực cao nên cần một cơ chế phát hiện sự cố tự động. Khi các máy chủ ở cụm chính không phản hồi trong một khoảng thời gian ngắn, một thành phần điều hướng thông minh phải tự động chuyển toàn bộ lưu lượng truy cập của người dùng sang cụm máy chủ dự phòng. Bài toán này yêu cầu bạn thiết kế các kịch bản kiểm tra sức khỏe hệ thống và cấu hình các bản ghi mạng sao cho việc chuyển đổi diễn ra mượt mà, người dùng cuối không cảm thấy bị gián đoạn dịch vụ quá lâu.

### Phục hồi dữ liệu từ bản sao lưu định kỳ sau khi bị tấn công mã hóa

Một doanh nghiệp bị tấn công bởi mã độc khiến toàn bộ dữ liệu hiện tại bị khóa và không thể truy cập. Chiến lược phục hồi lúc này dựa vào các bản sao lưu được thực hiện hàng ngày và hàng giờ được lưu trữ tách biệt hoàn toàn với hệ thống đang chạy. Bạn cần thiết kế quy trình để nhanh chóng khởi tạo lại môi trường mới từ các bản sao lưu này, kiểm tra tính toàn vẹn của dữ liệu và xác định thời điểm gần nhất dữ liệu còn sạch để đưa hệ thống quay trở lại hoạt động bình thường.

### Quản lý phiên đăng nhập của người dùng khi xảy ra sự cố chuyển vùng

Khi toàn bộ hệ thống chuyển từ vùng bị lỗi sang vùng dự phòng, một vấn đề lớn phát sinh là hàng triệu người dùng đang đăng nhập có thể bị văng ra ngoài do máy chủ mới không giữ thông tin phiên làm việc của họ. Bài toán yêu cầu thiết kế kiến trúc lưu trữ thông tin đăng nhập sao cho chúng được phân tán hoặc đồng bộ liên tục giữa các vùng. Mục tiêu là khi hệ thống thực hiện chuyển vùng dự phòng, khách hàng vẫn có thể tiếp tục sử dụng ứng dụng mà không cần phải thực hiện đăng nhập lại từ đầu.

### Chiến lược ưu tiên phục hồi các dịch vụ cốt lõi trong hệ thống microservices

Trong một hệ thống có hàng trăm dịch vụ nhỏ khác nhau, khi xảy ra sự cố nghiêm trọng, việc khôi phục tất cả cùng một lúc là không khả thi do giới hạn về tài nguyên và nhân lực. Bạn cần thiết kế một sơ đồ phụ thuộc giữa các dịch vụ để xác định đâu là những dịch vụ trọng yếu phải hoạt động trước như thanh toán, đăng nhập và đâu là những dịch vụ có thể khôi phục sau như gợi ý sản phẩm hay báo cáo thống kê. Bài toán này giúp luyện tập tư duy về thiết kế hệ thống có khả năng chịu lỗi và phục hồi từng phần.

### Xử lý xung đột dữ liệu khi hệ thống chính hoạt động trở lại

Sau khi sự cố tại vùng chính được khắc phục, hệ thống cần được chuyển ngược trở lại từ vùng dự phòng về vùng chính để giảm chi phí hoặc tối ưu tốc độ. Tuy nhiên, trong thời gian vùng dự phòng hoạt động, đã có rất nhiều dữ liệu mới được sinh ra. Bài toán đặt ra là làm thế nào để đồng bộ ngược các dữ liệu mới này về lại vùng chính mà không gây ra xung đột hoặc ghi đè mất dữ liệu, đảm bảo hai bên hoàn toàn khớp nhau trước khi chính thức chuyển lưu lượng truy cập quay về.

### Hệ thống lưu trữ tập tin phân tán chống mất mát dữ liệu vật lý

Một ứng dụng mạng xã hội lưu trữ hàng tỷ hình ảnh và video của người dùng. Nếu một phân vùng lưu trữ cứng bị hỏng, dữ liệu có nguy cơ mất vĩnh viễn. Bài toán yêu cầu thiết kế kiến trúc lưu trữ sao cho mỗi tập tin khi tải lên sẽ được tự động nhân bản ra nhiều vị trí vật lý khác nhau. Hệ thống phải có khả năng tự phát hiện khi một bản sao bị hỏng và tự động tạo ra bản sao mới từ các nguồn còn lại để duy trì đủ số lượng bản dự phòng theo quy định.

### Kiểm tra định kỳ kịch bản thảm họa bằng môi trường giả lập

Để đảm bảo kế hoạch dự phòng thực sự hoạt động khi có biến cố, doanh nghiệp cần thực hiện các cuộc diễn tập tắt thử hệ thống đang chạy. Bài toán yêu cầu thiết kế một môi trường giả lập có cấu trúc giống hệt hệ thống thật để đội ngũ kỹ thuật có thể thực hiện các thao tác phá hủy thử nghiệm và đo lường thời gian phục hồi thực tế. Điều này giúp tinh chỉnh các kịch bản vận hành, cấu hình lại các thông số kết nối cơ sở dữ liệu và đảm bảo mọi thành viên đều nắm rõ quy trình xử lý khi có sự cố thật xảy ra.
