# Cohort analysis

### Phân tích tỷ lệ giữ chân người dùng theo tháng đăng ký

Đây là bài toán cơ bản nhất trong Cohort Analysis. Hệ thống cần nhóm tất cả người dùng đăng ký tài khoản mới trong cùng một tháng vào một nhóm duy nhất. Sau đó, qua từng tháng tiếp theo, hệ thống phải thống kê xem có bao nhiêu người trong nhóm đó còn quay lại thực hiện ít nhất một hành động bất kỳ trên ứng dụng. Kết quả trả về thường là một bảng ma trận giúp nhà quản lý biết được chất lượng người dùng mới của tháng nào là tốt nhất và sau bao lâu thì người dùng có xu hướng rời bỏ ứng dụng.

### Đánh giá hiệu quả của các chiến dịch quảng cáo theo nguồn đổ về

Thay vì chỉ nhóm theo thời gian, bài toán này yêu cầu nhóm người dùng dựa trên nguồn mà họ đến với ứng dụng như Facebook Ads, Google Ads hoặc Organic Search. Hệ thống cần lưu trữ thông tin nguồn gốc của người dùng tại thời điểm đăng ký và theo dõi hành vi mua hàng của họ trong các tuần kế tiếp. Mục tiêu là so sánh xem người dùng đến từ nguồn nào có tỷ lệ trung thành cao hơn và mang lại doanh thu bền vững hơn, từ đó tối ưu hóa chi phí marketing.

### Phân tích xu hướng mua lại sau lần đầu tiên trải nghiệm dịch vụ

Bài toán này tập trung vào hành vi thương mại điện tử. Nhóm người dùng được xác định dựa trên thời điểm họ phát sinh đơn hàng đầu tiên thành công. Hệ thống sẽ theo dõi các mốc thời gian sau đó như tuần thứ nhất, tuần thứ hai hoặc tháng thứ nhất để xem có bao nhiêu phần trăm người dùng quay lại đặt đơn hàng thứ hai. Việc thiết kế database cần đảm bảo truy vấn nhanh chóng giữa bảng thông tin khách hàng và bảng lịch sử giao đơn hàng để tính toán khoảng cách giữa các lần mua.

### Theo dõi mức chi tiêu trung bình của các nhóm khách hàng theo thời gian

Đây là dạng Cohort về doanh thu (Revenue Cohort). Hệ thống không chỉ đếm số lượng người quay lại mà còn phải tính tổng số tiền hoặc số tiền trung bình mà mỗi nhóm khách hàng chi trả qua từng giai đoạn. Bài toán này giúp doanh nghiệp xác định được giá trị trọn đời của khách hàng. Ví dụ, nhóm người dùng đăng ký vào dịp Tết có thể có số lượng đông nhưng mức chi tiêu trung bình ở các tháng sau đó lại thấp hơn nhóm đăng ký vào các tháng bình thường.

### Phân tích tác động của việc cập nhật tính năng mới đến giữ chân người dùng

Khi ứng dụng ra mắt một tính năng lớn hoặc thay đổi giao diện, hệ thống cần tạo ra các nhóm người dùng bắt đầu sử dụng tính năng đó trong cùng một khoảng thời gian. Sau đó, bạn cần so sánh tỷ lệ quay lại của nhóm có sử dụng tính năng mới với nhóm không sử dụng hoặc nhóm người dùng cũ trước khi có tính năng. Bài toán này đòi hỏi thiết kế hệ thống logging sự kiện chi tiết để ghi lại chính xác thời điểm người dùng tương tác với các thành phần cụ thể trong app.

### Đánh giá tỷ lệ rời bỏ của người dùng đăng ký gói dịch vụ trả phí

Đối với các mô hình kinh doanh đăng ký định kỳ như Netflix hay Spotify, việc phân tích nhóm theo thời điểm bắt đầu trả phí là cực kỳ quan trọng. Hệ thống cần theo dõi xem sau bao nhiêu chu kỳ thanh toán thì người dùng có xu hướng hủy gói. Bài toán này giúp bộ phận vận hành thiết kế các chương trình khuyến mãi đúng thời điểm để ngăn chặn việc người dùng rời đi ngay trước khi họ định hủy dịch vụ.

### Phân tích hành vi theo ngưỡng hành động then chốt

Bài toán này nhóm người dùng dựa trên việc họ hoàn thành một cột mốc cụ thể, ví dụ như hoàn thành hồ sơ cá nhân hoặc kết bạn với 5 người đầu tiên. Hệ thống sẽ theo dõi xem những người hoàn thành cột mốc này trong cùng một tuần có tỷ lệ giữ chân khác biệt thế nào so với những người không thực hiện. Điều này giúp kiểm chứng giả thuyết về những hành động dẫn tới sự gắn bó lâu dài với sản phẩm.

### Theo dõi hiệu quả của chương trình khách hàng thân thiết theo hạng thành viên

Hệ thống nhóm người dùng dựa trên thời điểm họ được thăng hạng lên thành viên Bạc, Vàng hoặc Kim cương. Sau đó, hệ thống phân tích xem sau khi lên hạng, tần suất mua hàng và giá trị đơn hàng của họ thay đổi như thế nào trong các tháng tiếp theo. Bài toán này yêu cầu database phải lưu trữ lịch sử thay đổi hạng thành viên và kết nối chặt chẽ với dữ liệu giao dịch để thấy được sự biến chuyển trong hành vi mua sắm.
