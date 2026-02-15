# Coin apply

### Áp dụng mức trần sử dụng Coin theo danh mục sản phẩm

Trong hệ thống thương mại điện tử đa ngành hàng, mỗi loại sản phẩm có biên lợi nhuận khác nhau nên quy tắc dùng Coin cũng khác nhau. Bài toán yêu cầu thiết kế hệ thống sao cho sản phẩm thuộc ngành hàng điện tử chỉ được giảm tối đa 5% giá trị, trong khi ngành hàng thời trang có thể cho phép dùng Coin thanh toán tới 30% giá trị món hàng. Khi khách hàng thanh toán một giỏ hàng hỗn hợp, hệ thống phải tự động tính toán tổng số Coin tối đa mà khách hàng được phép áp dụng dựa trên từng item cụ thể.

### Xử lý hoàn Coin khi hủy đơn hàng một phần

Một đơn hàng có thể bao gồm nhiều sản phẩm và khách hàng đã dùng 100 Coin để giảm giá tổng thể. Khi khách hàng yêu cầu hủy hoặc trả hàng chỉ một trong số các sản phẩm đó, hệ thống cần có cơ chế tính toán lại số Coin cần hoàn trả vào ví của người dùng. Việc này đòi hỏi logic phân bổ số Coin đã dùng cho từng dòng sản phẩm dựa trên tỷ trọng giá trị, đảm bảo tính công bằng và không làm thất thoát ngân sách của sàn.

### Quản lý thời hạn sử dụng và ưu tiên khấu trừ Coin

Hệ thống phát hành nhiều loại Coin với thời điểm hết hạn khác nhau, ví dụ Coin từ sự kiện Tết có hạn 1 tháng, trong khi Coin từ hoàn tiền mua sắm có hạn 1 năm. Khi khách hàng thực hiện lệnh áp dụng Coin vào đơn hàng, hệ thống phải tự động nhận diện và ưu tiên trừ những đồng Coin có ngày hết hạn gần nhất trước. Điều này đòi hỏi cấu trúc lưu trữ lịch sử biến động số dư phải cực kỳ chi tiết để có thể truy vết và xử lý chính xác khi có giao dịch phát sinh.

### Tích hợp Coin cùng với nhiều mã giảm giá khác

Trong thực tế, khách hàng thường áp dụng đồng thời cả mã giảm giá của shop, mã miễn phí vận chuyển và cuối cùng là dùng Coin để giảm thêm. Bài toán đặt ra là xác định thứ tự ưu tiên tính toán để ra được số tiền cuối cùng khách hàng phải trả. Thông thường, Coin sẽ được áp dụng trên số tiền sau khi đã trừ đi hết các loại voucher khác, và hệ thống cần kiểm soát để tổng giá trị giảm trừ không vượt quá một ngưỡng nhất định hoặc không khiến giá trị đơn hàng trở về bằng không.

### Ngăn chặn Race Condition khi dùng Coin trên nhiều thiết bị

Đây là bài toán kỹ thuật quan trọng khi thiết kế hệ thống chịu tải cao. Một người dùng có thể đăng nhập tài khoản trên hai điện thoại khác nhau và thực hiện thanh toán hai đơn hàng khác nhau gần như cùng một lúc. Nếu không có cơ chế khóa dòng dữ liệu hoặc kiểm tra số dư nghiêm ngặt tại thời điểm xử lý thanh toán, người dùng có thể lợi dụng độ trễ của hệ thống để chi tiêu số Coin vượt quá số dư thực tế mà họ đang có.

### Quy đổi tỷ giá Coin theo phân hạng thành viên

Hệ thống muốn tri ân các khách hàng thân thiết bằng cách thay đổi giá trị của đồng Coin dựa trên hạng thẻ của họ. Ví dụ, với khách hàng hạng Đồng thì 1000 Coin chỉ giảm được 10.000 đồng, nhưng với khách hàng hạng Kim Cương thì 1000 Coin đó lại có giá trị tương đương 15.000 đồng khi thanh toán. Bài toán yêu cầu thiết kế bảng cấu hình tỷ giá linh hoạt và logic tính toán giá trị quy đổi tại thời điểm tạo đơn hàng để đảm bảo tính nhất quán.

### Giới hạn số Coin tối đa trên mỗi giao dịch và theo ngày

Để kiểm soát rủi ro và dòng tiền, doanh nghiệp đặt ra quy định mỗi đơn hàng không được dùng quá 500 Coin và mỗi ngày một tài khoản không được dùng quá 2000 Coin. Hệ thống cần lưu trữ và truy vấn nhanh chóng lịch sử sử dụng Coin trong ngày của người dùng để quyết định có cho phép thực hiện giao dịch tiếp theo hay không. Điều này tác động trực tiếp đến việc thiết kế các bảng lưu trữ tổng hợp hoặc sử dụng bộ nhớ đệm để tối ưu hóa tốc độ kiểm tra.

### Theo dõi biến động và đối soát Coin giữa các bên

Trong mô hình sàn thương mại điện tử, Coin có thể do sàn tặng hoặc do người bán tự bỏ ngân sách ra tặng. Khi khách hàng áp dụng Coin vào đơn hàng của một shop cụ thể, hệ thống phải ghi nhận rõ ràng nguồn gốc số Coin đó để thực hiện đối soát tài chính cuối tháng. Hệ thống cần phân biệt được số tiền nào sàn sẽ bù cho chủ shop và số tiền nào chủ shop phải tự chịu để đảm bảo báo cáo doanh thu và công nợ luôn chính xác.
