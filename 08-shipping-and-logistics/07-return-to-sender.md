# Return to sender

### Quản lý trạng thái vòng đời đơn hàng hoàn

Khi một đơn hàng giao không thành công sau tối đa ba lần, hệ thống cần tự động chuyển trạng thái từ giao hàng sang chờ hoàn. Bài toán đặt ra là phải ghi lại toàn bộ lịch sử thay đổi trạng thái kèm theo lý do cụ thể từ phía shipper như khách không nghe máy, khách hẹn ngày khác nhưng quá hạn, hoặc khách từ chối nhận do hàng móp méo. Việc này giúp hệ thống xác định được thời điểm chính xác hàng bắt đầu quay về và căn cứ để tính toán thời gian hoàn hàng dự kiến.

### Phân loại và xử lý lý do hoàn hàng

Hệ thống cần phân biệt rõ giữa việc hoàn hàng do lỗi vận chuyển với hoàn hàng do người mua chủ động từ chối. Trong trường hợp người mua từ chối nhận vì hàng hỏng hóc, hệ thống phải cho phép đính kèm bằng chứng hình ảnh hoặc video từ shipper. Dữ liệu này rất quan trọng để sau này bộ phận chăm sóc khách hàng hoặc bộ phận khiếu nại quyết định xem chi phí vận chuyển chiều về sẽ do người bán, người mua hay đơn vị vận chuyển chịu trách nhiệm.

### Quy trình kiểm soát lưu kho hàng hoàn

Khi hàng quay về kho của người bán hoặc kho trung tâm, nhân viên kho cần thực hiện bước xác nhận đã nhận hàng. Bài toán ở đây là xử lý các tình huống hàng về không đủ số lượng so với lúc đi, hoặc hàng bị tráo đổi bên trong. Hệ thống cần ghi nhận mã kiện hàng, mã vận đơn gốc và đối chiếu với tình trạng vật lý lúc nhận lại để cập nhật chính xác số lượng tồn kho khả dụng cho việc bán lại hoặc chuyển vào khu vực hàng lỗi.

### Tính toán và phân bổ chi phí vận chuyển ngược

Một đơn hàng hoàn phát sinh chi phí vận chuyển chiều đi và thường là thêm một phần chi phí chiều về. Bài toán thực tế là làm sao để tự động tính toán số tiền này dựa trên hợp đồng với đơn vị vận chuyển. Hệ thống phải tách bạch được khoản tiền thu hộ (COD) sẽ bị hủy bỏ, phí giao hàng bị mất đi, và các loại phí lưu kho phát sinh trong quá trình hàng nằm chờ tại bưu cục trước khi quay đầu về cho người bán.

### Quản lý phiếu thu hồi và biên bản bàn giao

Trong môi trường B2B hoặc các sàn thương mại điện tử lớn, việc trả hàng cần có chứng từ pháp lý. Bài toán yêu cầu thiết kế quy trình tạo ra các phiếu thu hồi hàng hóa tự động có mã vạch riêng. Khi shipper trả hàng cho người bán, hai bên phải ký nhận thông qua ứng dụng hoặc giấy tờ, và hệ thống cần cập nhật thông tin người ký, giờ ký để tránh tranh chấp về việc người bán bảo chưa nhận được hàng nhưng đơn vị vận chuyển báo đã trả xong.

### Điều hướng và tối ưu lộ trình hàng hoàn

Không phải lúc nào hàng cũng quay về kho xuất phát ban đầu. Trong các hệ thống đa kho, bài toán là điều hướng hàng hoàn về kho gần nhất hoặc kho chuyên xử lý hàng lỗi để giảm chi phí vận chuyển. Hệ thống cần có logic kiểm tra vị trí hiện tại của gói hàng và các quy tắc cấu hình của người bán để quyết định đích đến cuối cùng của kiện hàng đó, thay vì mặc định quay lại điểm lấy hàng ban đầu.

### Đối soát tài chính giữa người bán và đơn vị vận chuyển

Cuối mỗi kỳ thanh toán, người bán và bên vận chuyển cần đối soát danh sách các đơn hàng hoàn. Bài toán này yêu cầu hệ thống xuất ra được báo cáo chi tiết các đơn hàng đã chuyển trạng thái hoàn thành việc trả hàng, tổng phí vận chuyển phải trả cho các đơn lỗi, và bù trừ với các khoản tiền thu hộ từ các đơn giao thành công khác. Dữ liệu phải đảm bảo tính toàn vẹn để không bị trùng lặp hoặc bỏ sót bất kỳ vận đơn nào.

### Hệ thống cảnh báo và phân tích tỷ lệ hoàn hàng

Để tối ưu kinh doanh, người bán cần biết những khách hàng hoặc khu vực nào có tỷ lệ hoàn hàng cao bất thường. Bài toán đặt ra là thiết kế các chỉ số đo lường tỷ lệ hoàn trên tổng đơn theo thời gian thực. Hệ thống cần gửi cảnh báo nếu một tài khoản người mua có dấu hiệu đặt hàng ảo hoặc thường xuyên từ chối nhận hàng để người bán có thể chủ động chặn hoặc yêu cầu thanh toán trước thay vì cho phép thanh toán khi nhận hàng.
