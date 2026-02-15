# Voucher apply

### Quản lý giới hạn lượt sử dụng và ngân sách chiến dịch

Hệ thống cần quản lý các mã giảm giá có giới hạn tổng số lần áp dụng trên toàn hệ thống hoặc giới hạn ngân sách tối đa cho một chương trình. Bài toán đặt ra là khi một voucher được tung ra với số lượng có hạn, hệ thống phải đảm bảo không xảy ra tình trạng áp dụng vượt mức khi có hàng nghìn người dùng cùng thanh toán một lúc. Bạn cần thiết kế cách lưu trữ số lượng đã dùng, số lượng còn lại và trạng thái của voucher để phản hồi ngay lập tức cho người dùng liệu mã đó còn hiệu lực hay không trước khi họ tiến hành đặt hàng.

### Kiểm tra điều kiện áp dụng theo danh mục hàng hóa và giá trị đơn hàng tối thiểu

Một mã giảm giá thường không áp dụng cho toàn bộ cửa hàng mà chỉ có hiệu lực với một số ngành hàng nhất định hoặc các sản phẩm cụ thể. Bài toán yêu cầu hệ thống phải bóc tách giỏ hàng của người dùng, lọc ra những sản phẩm thỏa mãn điều kiện danh mục, sau đó tính tổng tiền của riêng những sản phẩm đó để xem có đạt mức chi tiêu tối thiểu mà voucher yêu cầu hay không. Nếu chỉ có một phần giỏ hàng thỏa mãn, số tiền giảm giá chỉ được tính dựa trên giá trị của phần hàng hóa đó thay vì tổng giá trị đơn hàng ban đầu.

### Phân loại voucher theo đối tượng khách hàng mục tiêu

Để tối ưu hóa marketing, doanh nghiệp thường phát hành các mã giảm giá dành riêng cho khách hàng mới, khách hàng thành viên hạng vàng hoặc những người đã lâu không mua hàng. Bài toán này đòi hỏi hệ thống kiểm tra điều kiện phải truy vấn ngược lại lịch sử mua hàng và thông tin định danh của người dùng trong cơ sở dữ liệu. Bạn cần thiết kế cấu trúc để liên kết giữa bảng mã giảm giá với các tiêu chí phân loại khách hàng, đảm bảo một người dùng không thể sử dụng mã của nhóm đối tượng khác dù họ có biết mã đó.

### Hệ thống Voucher tích lũy và khả năng cộng dồn mã giảm giá

Trong thực tế, một đơn hàng có thể áp dụng đồng thời nhiều loại voucher khác nhau như mã giảm giá của sàn, mã giảm giá của shop và mã miễn phí vận chuyển. Bài toán yêu cầu thiết kế logic để xác định loại voucher nào được phép dùng chung với nhau và thứ tự áp dụng chúng. Việc tính toán lại tổng tiền phải thực hiện theo từng bước, ví dụ giảm trừ theo số tiền cố định trước rồi mới tính phần trăm giảm giá trên số dư còn lại, nhằm tránh trường hợp tổng số tiền giảm vượt quá giá trị đơn hàng.

### Quản lý vòng đời voucher từ lúc phát hành đến khi thu hồi

Bài toán này tập trung vào quy trình trạng thái của một mã giảm giá bao gồm các giai đoạn như bản nháp, đã kích hoạt, tạm dừng, hết hạn hoặc đã bị hủy. Hệ thống cần xử lý các trường hợp đặc biệt như khi khách hàng đã áp dụng mã vào đơn hàng nhưng sau đó hủy đơn hoặc trả hàng. Lúc này, hệ thống phải có cơ chế tự động hoàn lại lượt sử dụng cho voucher đó vào tài khoản của người dùng nếu mã vẫn còn trong thời hạn hiệu lực, đồng thời cập nhật lại các báo cáo sử dụng ngân sách.

### Cá nhân hóa Voucher qua ví khuyến mãi riêng biệt

Thay vì nhập mã thủ công, hệ thống hiện đại thường cho phép người dùng thu thập voucher vào một ví điện tử cá nhân. Bài toán yêu cầu thiết kế sự liên kết giữa bảng voucher tổng và bảng lưu trữ các mã mà người dùng đã thu thập. Bạn cần quản lý được thời điểm người dùng thu thập mã, thời điểm mã bắt đầu có hiệu lực trong ví và đánh dấu các mã đã sử dụng để chúng không xuất hiện trong danh sách gợi ý khi người dùng thanh toán các đơn hàng tiếp theo.

### Giới hạn số lần sử dụng trên mỗi thiết bị hoặc số điện thoại

Để chống lại việc gian lận bằng cách tạo nhiều tài khoản ảo để săn khuyến mãi, hệ thống cần có các điều kiện kiểm tra nâng cao. Bài toán đặt ra là ngoài việc kiểm tra ID người dùng, hệ thống phải lưu trữ và đối soát các thông tin như số điện thoại nhận hàng, địa chỉ hoặc ID thiết bị di động. Nếu một thiết bị hoặc một số điện thoại đã sử dụng mã giảm giá đó quá số lần quy định, hệ thống sẽ từ chối áp dụng ngay cả khi người dùng đang sử dụng một tài khoản hoàn toàn mới.

### Tự động gợi ý voucher tối ưu nhất cho giỏ hàng

Đây là bài toán về trải nghiệm người dùng và tối ưu hóa logic phía backend. Khi người dùng vào trang thanh toán, thay vì bắt họ tự chọn, hệ thống sẽ quét toàn bộ danh sách voucher mà người dùng đang có và tự động tính toán thử các kịch bản áp dụng khác nhau. Mục tiêu là tìm ra tổ hợp các mã giảm giá giúp người dùng tiết kiệm được nhiều tiền nhất và tự động điền vào ô mã giảm giá. Điều này đòi hỏi thuật toán xử lý nhanh và cấu trúc dữ liệu cho phép truy vấn hiệu quả các mã khả dụng.
