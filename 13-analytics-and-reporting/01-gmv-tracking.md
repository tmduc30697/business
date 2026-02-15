# GMV tracking

### Tính toán GMV thời gian thực trên Dashboard quản trị

Hệ thống cần hiển thị tổng giá trị giao dịch đang phát sinh ngay lập tức khi có đơn hàng mới được tạo trong ngày. Thách thức ở đây là khi số lượng giao dịch lên đến hàng triệu đơn mỗi ngày, việc thực hiện lệnh cộng tổng trực tiếp trên bảng hóa đơn sẽ gây chậm trễ cho cơ sở dữ liệu. Bạn cần thiết kế một giải pháp để lưu trữ các giá trị cộng dồn hoặc sử dụng các bảng thống kê trung gian để đảm bảo Dashboard luôn cập nhật số liệu mới nhất mà không làm treo hệ thống.

### Phân biệt GMV theo trạng thái thanh toán và vòng đời đơn hàng

Một đơn hàng từ khi khởi tạo đến khi hoàn tất trải qua nhiều trạng thái như Chờ thanh toán, Đã thanh toán, Đang giao, Đã nhận và Hủy đơn. Bài toán đặt ra là phải định nghĩa được thời điểm nào giá trị đơn hàng được tính vào GMV. Nếu tính ngay khi đặt hàng, GMV sẽ rất cao nhưng ảo vì có nhiều đơn ảo hoặc đơn hủy. Nếu tính khi hoàn tất, số liệu sẽ bị trễ. Hệ thống cần lưu vết các mốc thời gian thay đổi trạng thái để báo cáo GMV theo nhiều kịch bản khác nhau như GMV tiềm năng và GMV thực thu.

### Theo dõi GMV theo từng nhà bán hàng và phân loại ngành hàng

Trên một sàn thương mại điện tử đa đối tác, quản trị viên cần biết nhà bán hàng nào đang đóng đóng góp doanh số cao nhất và ngành hàng nào như điện tử hay thời trang đang tăng trưởng tốt. Điều này đòi hỏi thiết kế cơ sở dữ liệu phải có sự liên kết chặt chẽ giữa chi tiết đơn hàng, sản phẩm, danh mục và thông tin người bán. Hệ thống API cần hỗ trợ lọc và phân nhóm dữ liệu linh hoạt để xuất ra báo cáo GMV theo từng đối tượng cụ thể trong một khoảng thời gian tùy chỉnh.

### Xử lý hoàn tiền và điều chỉnh GMV sau giao dịch

Trong thực tế, khách hàng có thể trả hàng hoặc yêu cầu hoàn tiền một phần sau khi đơn hàng đã được tính vào GMV của tháng trước. Hệ thống cần một cơ chế ghi nhận các giao dịch điều chỉnh hoặc đảo ngược để số liệu GMV không bị sai lệch. Bài toán này yêu cầu thiết kế các bảng ghi nhật ký giao dịch tài chính sao cho có thể truy xuất được giá trị GMV gốc và giá trị thực tế sau khi đã trừ đi các khoản hoàn trả, giúp kế toán đối soát chính xác.

### Thống kê GMV theo các chiến dịch tiếp thị và mã giảm giá

Doanh nghiệp thường chạy các chương trình quảng cáo hoặc KOL để kéo khách hàng. Hệ thống cần ghi nhận mỗi đơn hàng phát sinh từ nguồn nào hoặc mã giảm giá nào để tính toán GMV mang lại từ chiến dịch đó. Đặc biệt, bạn cần phân biệt giữa GMV trước giảm giá và GMV sau giảm giá để tính toán hiệu quả của chi phí marketing. Thiết kế database cần lưu trữ thông tin nguồn dẫn và các loại chiết khấu áp dụng cho từng đơn hàng cụ thể.

### Chuyển đổi tiền tệ và thống kê GMV đa quốc gia

Đối với các nền tảng hoạt động ở nhiều quốc gia, đơn hàng có thể được thanh toán bằng nhiều loại tiền tệ khác nhau. Tuy nhiên, báo cáo tổng giá trị giao dịch toàn hệ thống thường phải quy đổi về một loại tiền tệ duy nhất như Đô la Mỹ hoặc Đồng Việt Nam. Bài toán yêu cầu hệ thống phải lưu trữ tỷ giá tại thời điểm phát sinh giao dịch để tính toán GMV chính xác, tránh việc dùng tỷ giá hiện tại áp cho các đơn hàng trong quá khứ dẫn đến sai lệch số liệu tăng trưởng.

### Phân tích GMV theo vị trí địa lý và mật độ đơn hàng

Để tối ưu hóa kho bãi và logistics, bộ phận vận hành cần xem biểu đồ nhiệt về GMV theo tỉnh thành hoặc quận huyện. Dữ liệu địa chỉ giao hàng cần được chuẩn hóa và phân tách để hệ thống có thể tổng hợp doanh số theo từng vùng miền. Bài toán này giúp bạn luyện tập cách thiết kế các bảng danh mục địa chính và cách thực hiện các câu lệnh truy vấn phân nhóm theo vị trí địa lý để đưa ra bức tranh tổng quan về thị trường.

### Lưu trữ lịch sử GMV theo dạng Snapshot để báo cáo nhanh

Thay vì tính toán lại từ đầu mỗi khi có yêu cầu xem báo cáo năm, hệ thống cần thực hiện chốt số liệu vào cuối mỗi ngày hoặc mỗi tháng và lưu vào một bảng riêng gọi là bảng Snapshot. Việc này giúp việc truy xuất biểu đồ tăng trưởng GMV theo năm trở nên cực kỳ nhanh chóng. Bạn sẽ cần thiết kế các tiến trình chạy ngầm để tự động tổng hợp dữ liệu từ các bảng giao dịch chi tiết và đẩy vào các bảng báo cáo tĩnh này theo lịch trình cố định.
