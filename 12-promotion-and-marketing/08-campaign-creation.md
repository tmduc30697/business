# Campaign creation

### Thiết lập chiến dịch khuyến mãi theo khung thời gian đa dạng

Đội ngũ Marketing cần tạo các chiến dịch có thời hạn bắt đầu và kết thúc cụ thể. Tuy nhiên, bài toán trở nên phức tạp khi có những chiến dịch chỉ chạy vào các khung giờ cố định trong ngày như giờ vàng buổi trưa hoặc chỉ chạy vào các ngày cuối tuần trong suốt một tháng. Hệ thống cần cho phép thiết lập cấu hình thời gian linh hoạt để tự động kích hoạt hoặc tạm dừng các ưu đãi mà không cần sự can thiệp thủ công từ quản trị viên tại mỗi thời điểm.

### Phân đoạn đối tượng khách hàng mục tiêu cho chiến dịch

Một chiến dịch không dành cho tất cả mọi người mà chỉ nhắm đến các nhóm cụ thể. Ví dụ như chiến dịch tặng quà cho khách hàng chưa mua hàng trong 3 tháng qua, hoặc chiến dịch giảm giá đặc biệt cho những người có sinh nhật trong tháng hiện tại. Hệ thống cần có khả năng lưu trữ các tiêu chí lọc khách hàng hoặc liên kết với danh sách ID người dùng đã được phân loại sẵn để đảm bảo chỉ những đối tượng thỏa mãn điều kiện mới thấy và sử dụng được ưu đãi.

### Quản lý chiến dịch đa kênh với mã giảm giá dùng chung và mã riêng lẻ

Marketing muốn triển khai một chiến dịch lớn trên cả Facebook và Email. Trên Facebook, họ dùng một mã chung dễ nhớ để mọi người cùng nhập. Trong khi đó, qua Email, họ muốn gửi cho mỗi khách hàng một mã định danh duy nhất để cá nhân hóa trải nghiệm. Bài toán đặt ra là làm thế nào để thiết kế database quản lý một chiến dịch mẹ nhưng chứa nhiều loại hình phát hành mã khác nhau bên dưới mà vẫn thống nhất được báo cáo doanh thu.

### Thiết lập thứ tự ưu tiên và quy tắc loại trừ giữa các chiến dịch

Khi có nhiều chiến dịch diễn ra cùng một lúc, ví dụ như vừa có chương trình giảm giá toàn sàn 10%, vừa có mã giảm giá 50.000 đồng cho đơn hàng đầu tiên. Hệ thống cần một cơ chế để xác định chiến dịch nào được ưu tiên áp dụng trước, hoặc quy định rõ ràng rằng các chiến dịch này có được phép cộng dồn với nhau hay không. Nếu không được cộng dồn, hệ thống phải tự động chọn ra phương án có lợi nhất cho khách hàng hoặc tuân theo thứ tự ưu tiên đã cài đặt.

### Quản lý ngân sách và giới hạn chi phí tối đa cho chiến dịch

Mỗi chiến dịch đều có một hạn mức ngân sách nhất định, ví dụ như tổng số tiền giảm giá cho khách hàng không được vượt quá 100 triệu đồng. Hệ thống phải theo dõi tổng số tiền đã thực tế giảm trừ cho khách hàng theo thời gian thực. Ngay khi số tiền giảm giá tích lũy chạm ngưỡng ngân sách cho phép, chiến dịch phải tự động kết thúc hoặc chuyển sang trạng thái chờ để đảm bảo bộ phận Marketing không chi vượt quá số tiền đã phê duyệt.

### Tạo chiến dịch tặng kèm sản phẩm theo giá trị giỏ hàng

Thay vì giảm tiền trực tiếp, Marketing muốn thiết kế chiến dịch tặng một món quà cụ thể khi đơn hàng đạt giá trị nhất định. Ví dụ, với đơn hàng trên 500.000 đồng, khách hàng được chọn 1 trong 3 món quà tặng kèm. Bài toán này yêu cầu hệ thống quản lý chiến dịch phải kết nối chặt chẽ với danh mục sản phẩm và kho hàng để kiểm tra tính khả dụng của quà tặng trước khi xác nhận chiến dịch có thể áp dụng cho người dùng.

### Quy trình phê duyệt và quản lý trạng thái chiến dịch

Để đảm bảo tính chính xác, một chiến dịch sau khi được nhân viên Marketing tạo ra phải trải qua trạng thái chờ phê duyệt bởi quản lý cấp cao trước khi chính thức chạy. Trong quá trình chạy, nhân viên có thể cần tạm dừng chiến dịch khẩn cấp để điều chỉnh nội dung hoặc kết thúc sớm hơn dự kiến. Hệ thống cần ghi lại lịch sử thay đổi trạng thái và người thực hiện để phục vụ việc kiểm soát nội bộ và vận hành an toàn.

### Theo dõi hiệu quả chiến dịch thông qua các chỉ số chuyển đổi

Để đánh giá thành công của một chiến dịch, hệ thống cần ghi lại các thông số như số lượt mã được phát ra, số lượt mã đã áp dụng thành công vào đơn hàng, và tổng giá trị đơn hàng mà chiến dịch đó mang lại. Việc thiết kế database cần cho phép truy vấn nhanh chóng các chỉ số này theo thời gian thực hoặc xuất báo cáo định kỳ, giúp Marketing đưa ra quyết định có nên tiếp tục gia hạn chiến dịch hay thực hiện các thay đổi phù hợp.
