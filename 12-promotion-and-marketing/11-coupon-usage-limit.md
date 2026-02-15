# Coupon usage limit

### Chiến dịch khai trương giới hạn số lượng toàn hệ thống

Một cửa hàng mới khai trương và tung ra mã giảm giá đặc biệt cho 100 khách hàng đầu tiên thanh toán thành công. Hệ thống cần một cơ chế để đếm tổng số lần mã đã được sử dụng trên toàn bộ nền tảng. Khi số lượt sử dụng chạm ngưỡng 100, mã phải ngay lập tức trở nên vô hiệu với tất cả các khách hàng khác, kể cả những người đã lưu mã vào ví nhưng chưa kịp thanh toán.

### Chương trình tri ân khách hàng thân thiết giới hạn theo người dùng

Để tránh việc một khách hàng lạm dụng ưu đãi quá nhiều lần, doanh nghiệp thiết lập quy định mỗi tài khoản định danh chỉ được phép sử dụng mã giảm giá này tối đa 2 lần trong suốt thời gian diễn ra chương trình. Hệ thống cần lưu trữ lịch sử sử dụng chi tiết của từng người dùng để kiểm tra điều kiện này mỗi khi họ tiến hành áp dụng mã vào đơn hàng mới.

### Mã giảm giá theo ngày cho dịch vụ giao đồ ăn

Một ứng dụng giao đồ ăn muốn kích cầu vào khung giờ thấp điểm bằng cách tung ra mã giảm giá có giới hạn theo ngày. Ví dụ, mỗi ngày chỉ có 50 lượt sử dụng mã này. Sang ngày hôm sau, con số này sẽ được làm mới lại từ đầu. Bài toán này yêu cầu thiết kế database sao cho có thể quản lý giới hạn theo từng chu kỳ thời gian cụ thể thay vì chỉ là một con số tổng cố định.

### Chiến dịch săn deal khung giờ vàng theo đợt

Trong các ngày lễ lớn, sàn thương mại điện tử tung ra mã giảm giá theo từng khung giờ cố định như 9h sáng, 12h trưa và 21h tối. Mỗi khung giờ sẽ có một số lượng mã nhất định. Người dùng có thể tham gia săn mã ở nhiều khung giờ khác nhau. Hệ thống cần quản lý giới hạn sử dụng theo từng đợt phát hành riêng biệt của cùng một mã giảm giá để đảm bảo tính công bằng và tạo sự khan hiếm.

### Ưu đãi kết hợp giữa tổng lượt dùng và lượt dùng cá nhân

Một nhãn hàng tung ra mã giảm giá với điều kiện phức tạp hơn nhằm tối ưu hóa tệp khách hàng: tổng số lượt sử dụng toàn hệ thống là 500 lượt, nhưng đồng thời mỗi người dùng chỉ được sử dụng tối đa 1 lần. Điều này đòi hỏi logic kiểm tra phải thực hiện đồng thời hai điều kiện: hệ thống còn lượt hay không và người dùng này đã dùng chưa, tránh tình trạng hệ thống còn lượt nhưng người dùng đã hết lượt cá nhân.

### Giới hạn mã giảm giá cho nhóm khách hàng cụ thể

Doanh nghiệp phát hành mã giảm giá dành riêng cho nhóm khách hàng VIP. Giới hạn sử dụng được thiết lập theo nhóm: tổng cả nhóm VIP chỉ có 200 lượt dùng. Bài toán này đặt ra yêu cầu về việc phân quyền và quản lý hạn ngạch theo phân khúc khách hàng trong database, đồng thời phải xử lý việc kiểm tra điều kiện nhóm trước khi kiểm tra số lượng mã còn lại.

### Quản lý mã giảm giá theo trạng thái đơn hàng

Khi người dùng áp dụng mã và đặt hàng, số lượt sử dụng của mã sẽ bị tạm giữ hoặc trừ đi. Tuy nhiên, nếu đơn hàng đó bị hủy hoặc thanh toán thất bại, hệ thống phải có cơ chế hoàn lại lượt sử dụng cho mã đó để người khác có thể dùng hoặc chính người đó dùng lại. Đây là bài toán quan trọng về tính nhất quán dữ liệu giữa bảng quản lý coupon và bảng đơn hàng.

### Giới hạn mã giảm giá theo thiết bị hoặc địa chỉ giao hàng

Để ngăn chặn tình trạng một người dùng tạo nhiều tài khoản ảo nhằm gian lận mã giảm giá, hệ thống cần thiết lập giới hạn dựa trên các thông tin phần cứng như ID thiết bị hoặc địa chỉ giao hàng. Ví dụ, một địa chỉ nhà chỉ được nhận ưu đãi tối đa 1 lần dù có nhiều tài khoản khác nhau đặt về đó. Bài toán này yêu cầu thiết kế ERD có sự kết nối chặt chẽ giữa thông tin vận chuyển và lịch sử dùng mã.

### Chương trình khuyến mãi theo đối tác ngân hàng

Một sàn thương mại điện tử hợp tác với ngân hàng để giảm giá cho khách hàng thanh toán bằng thẻ quốc tế. Mã giảm giá có giới hạn tổng là 1000 lượt nhưng chỉ áp dụng cho đầu số thẻ của ngân hàng đó. Hệ thống cần kiểm tra phương thức thanh toán và số lượt còn lại của ngân hàng đó trước khi cho phép áp dụng mã, đòi hỏi sự phối hợp giữa module thanh toán và module khuyến mãi.

### Giới hạn số lượng mã phát hành dưới dạng Voucher Code cá nhân

Thay vì dùng chung một mã văn bản, hệ thống sinh ra 10.000 mã ngẫu nhiên duy nhất cho 10.000 người đăng ký sớm nhất. Mỗi mã này chỉ có giá trị sử dụng đúng 1 lần duy nhất. Bài toán này tập trung vào việc quản lý trạng thái của từng mã code riêng lẻ trong một tập hợp lớn, thay vì chỉ quản lý một con số đếm tổng cho một mã chung.
