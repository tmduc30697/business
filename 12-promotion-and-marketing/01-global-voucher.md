# Global voucher

### Quản lý hạn mức sử dụng và ngân sách chiến dịch

Hệ thống cần kiểm soát số lượng mã giảm giá phát ra và số lượng thực tế đã được sử dụng để tránh tình trạng chi tiêu vượt quá ngân sách của sàn thương mại điện tử. Mỗi voucher có một tổng số lượng nhất định, nhưng đồng thời cũng cần giới hạn số lần một khách hàng cụ thể được phép áp dụng mã đó. Thách thức ở đây là việc cập nhật số lượng còn lại trong môi trường có hàng nghìn người cùng bấm thanh toán một lúc, đảm bảo không xảy ra tình trạng bán vượt mức so với số lượng voucher đã cấu hình ban đầu.

### Phân loại áp dụng voucher theo danh mục sản phẩm

Một mã giảm giá toàn sàn thường có những điều kiện loại trừ hoặc ưu tiên cho các nhóm ngành hàng nhất định để tối ưu lợi nhuận. Ví dụ, mã có thể áp dụng cho mọi sản phẩm thuộc ngành hàng điện tử và thời trang nhưng lại không có giá trị đối với ngành hàng nhu yếu phẩm hoặc thẻ điện thoại. Hệ thống cần lưu trữ mối quan hệ giữa voucher và các danh mục hoặc nhãn hàng bị giới hạn, từ đó thực hiện kiểm tra tính hợp lệ của giỏ hàng trước khi cho phép người dùng kích hoạt mã giảm giá.

### Chiến dịch voucher theo khung giờ và trạng thái kích hoạt

Để tạo hiệu ứng săn sale, các mã giảm giá thường được lên lịch xuất hiện theo từng khung giờ cố định trong ngày như khung giờ vàng hoặc các ngày đôi. Bài toán yêu cầu quản lý trạng thái của voucher từ lúc mới tạo, đang chờ kích hoạt, đang hiệu lực cho đến khi hết hạn hoặc bị quản trị viên tạm dừng thủ công. Điều này đòi hỏi thiết kế hệ thống có khả năng tự động cập nhật hoặc lọc các mã đang hoạt động một cách nhanh chóng để hiển thị cho người dùng trên ứng dụng.

### Kiểm tra điều kiện giá trị đơn hàng tối thiểu

Mỗi voucher thường đi kèm với một ngưỡng chi tiêu tối thiểu để người dùng được hưởng ưu đãi. Tuy nhiên, giá trị này phải được tính toán dựa trên giá sau khi đã trừ đi các khuyến mãi khác của người bán hoặc các loại phí vận chuyển nếu có. Hệ thống cần phân định rõ ràng cách tính tổng tiền giỏ hàng để so khớp với điều kiện của voucher, đảm bảo rằng nếu người dùng hủy một phần đơn hàng dẫn đến tổng giá trị thấp hơn mức quy định thì voucher sẽ không còn hiệu lực.

### Tích hợp và ưu tiên thứ tự áp dụng mã giảm giá

Trong thực tế, một đơn hàng có thể áp dụng đồng thời nhiều loại mã như mã giảm giá của sàn, mã của shop và mã miễn phí vận chuyển. Bài toán đặt ra là làm sao để thiết kế database và logic xử lý để phân biệt rõ các loại mã này, đồng thời xác định thứ tự trừ tiền sao cho chính xác. Việc chồng chéo các loại khuyến mãi cần được quy định chặt chẽ để tránh lỗi tính toán khiến tổng số tiền thanh toán của khách hàng trở về con số không hoặc bị âm.

### Lưu vết lịch sử và trạng thái sử dụng voucher

Khi người dùng áp dụng mã vào đơn hàng nhưng chưa thanh toán ngay, voucher đó cần được giữ chỗ trong một khoảng thời gian nhất định. Nếu đơn hàng bị hủy hoặc quá trình thanh toán thất bại, hệ thống phải có cơ chế hoàn trả lại lượt sử dụng cho người dùng một cách chính xác. Việc truy vết lịch sử sử dụng voucher gắn liền với mã đơn hàng là cực kỳ quan trọng để phục vụ công tác đối soát, chăm sóc khách hàng và phân tích hành vi người tiêu dùng sau các chiến dịch lớn.

### Cá nhân hóa voucher theo đối tượng khách hàng

Không phải mọi voucher đều dành cho tất cả mọi người; có những mã chỉ dành riêng cho khách hàng mới, khách hàng hạng kim cương hoặc những người đã lâu không quay lại ứng dụng. Hệ thống cần một cơ chế để định nghĩa các tập khách hàng mục tiêu và liên kết chúng với các mã giảm giá tương ứng. Khi một người dùng truy cập vào kho voucher, hệ thống phải lọc và chỉ hiển thị những mã mà người đó thực sự có quyền sử dụng dựa trên các thuộc tính tài khoản cá nhân.

### Hệ thống ví voucher và tính năng lưu mã trước khi dùng

Thay vì chỉ nhập mã tại bước thanh toán, người dùng thường có nhu cầu thu thập mã vào ví voucher của mình trước để dành cho các đợt mua sắm sau. Bài toán này yêu cầu quản lý mối quan hệ giữa người dùng và các mã giảm giá đã thu thập, bao gồm thông tin về thời điểm thu thập và trạng thái đã sử dụng hay chưa. Điều này giúp hệ thống gửi thông báo nhắc nhở khi mã trong ví của người dùng sắp hết hạn, từ đó thúc đẩy tỷ lệ chuyển đổi đơn hàng cho nền tảng.
