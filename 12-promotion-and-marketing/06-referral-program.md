# Referral program

### Quản lý liên kết giới hạn và mã mời duy nhất cho mỗi người dùng

Mỗi khách hàng khi đăng ký tài khoản sẽ được hệ thống cấp một mã mời duy nhất hoặc một đường dẫn định danh riêng biệt. Bài toán đặt ra là làm thế nào để lưu trữ và sinh mã này một cách hiệu quả để người dùng có thể chia sẻ cho bạn bè. Khi người bạn nhấp vào liên kết hoặc nhập mã lúc đăng ký, hệ thống phải ghi nhận chính xác mối quan hệ giữa người giới thiệu và người được giới thiệu vào cơ sở dữ liệu để phục vụ việc trả thưởng sau này.

### Xử lý trả thưởng tự động khi người được mời hoàn tất đơn hàng đầu tiên

Trong mô hình thương mại điện tử, người giới thiệu chỉ nhận được xu hoặc voucher khi người bạn mà họ mời thực hiện thanh toán thành công đơn hàng đầu tiên và đơn hàng đó không bị hoàn trả trong vòng bảy ngày. Hệ thống cần một cơ chế theo dõi trạng thái đơn hàng của người được mời và tự động kích hoạt lệnh cộng thưởng cho người giới thiệu ngay khi điều kiện thời gian và trạng thái được thỏa mãn.

### Chương trình giới thiệu đa cấp với hoa hồng phân tầng

Một ứng dụng học trực tuyến áp dụng chính sách thưởng theo tầng để khuyến khích người dùng mở rộng mạng lưới. Nếu người A mời người B, và người B tiếp tục mời người C, thì khi người C mua khóa học, cả người A và người B đều nhận được một tỷ lệ hoa hồng nhất định. Đây là bài toán điển hình về cấu trúc dữ liệu dạng cây hoặc phân cấp trong database, đòi hỏi khả năng truy vấn ngược danh sách người cấp trên để phân bổ tiền thưởng chính xác.

### Giới hạn số lượng lời mời thành công và tổng ngân sách thưởng

Để kiểm soát chi phí marketing, doanh nghiệp thiết lập quy định mỗi người dùng chỉ được nhận thưởng cho tối đa mười người bạn giới thiệu thành công đầu tiên trong một tháng. Đồng thời, toàn bộ chương trình sẽ dừng lại nếu tổng số tiền thưởng phát ra đạt đến một ngưỡng ngân sách cố định của công ty. Hệ thống cần kiểm tra các hạn mức này theo thời gian thực trước khi ghi nhận một giao dịch thưởng mới.

### Ngăn chặn gian lận tự giới thiệu bằng địa chỉ thiết bị và mạng

Nhiều người dùng cố gắng trục lợi bằng cách tự tạo nhiều tài khoản ảo trên cùng một điện thoại để nhập mã mời của chính mình. Hệ thống cần lưu trữ các thông tin định danh phần cứng, địa chỉ mạng hoặc dấu hiệu trình duyệt của cả người giới thiệu và người được giới thiệu. Nếu phát hiện sự trùng khớp hoặc bất thường trong các thông tin này, hệ thống phải gắn cờ nghi ngờ và tạm dừng việc trả thưởng để bộ phận kiểm soát phê duyệt thủ công.

### Trả thưởng bằng nhiều hình thức khác nhau tùy theo chiến dịch

Tùy vào từng thời điểm, phần thưởng cho người giới thiệu có thể là tiền mặt cộng vào ví, voucher giảm giá hoặc nâng cấp gói thành viên miễn phí trong một tháng. Thiết kế hệ thống cần tính linh hoạt để có thể thay đổi loại phần thưởng mà không phải thay đổi cấu trúc bảng dữ liệu chính. Mỗi loại phần thưởng sẽ có quy trình xử lý riêng nhưng phải được quản lý tập trung trong lịch sử nhận thưởng của người dùng.

### Theo dõi hiệu quả chuyển đổi từ lời mời đến hành động thực tế

Bộ phận vận hành cần một hệ thống báo cáo chi tiết để biết được một người dùng đã gửi đi bao nhiêu lời mời, bao nhiêu người đã nhấn vào link, bao nhiêu người đã đăng ký tài khoản nhưng chưa mua hàng. Việc thiết kế database phải cho phép lưu trữ các sự kiện trung gian này để vẽ được phễu chuyển đổi, giúp doanh nghiệp đánh giá được mức độ hấp dẫn của chương trình giới thiệu.

### Xử lý hoàn trả và thu hồi phần thưởng khi phát hiện gian lận hậu kiểm

Có những trường hợp người được mời đã mua hàng để người giới thiệu nhận thưởng, nhưng sau đó cố tình hủy đơn hoặc yêu cầu hoàn tiền. Hệ thống cần một cơ chế xử lý đảo ngược giao dịch, tức là nếu đơn hàng gốc bị hủy thì phần thưởng đã trao cho người giới thiệu cũng phải bị thu hồi hoặc trừ vào số dư hiện tại. Điều này đòi hỏi sự liên kết chặt chẽ giữa module bán hàng, module ví điện tử và module referral.
