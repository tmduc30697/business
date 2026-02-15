# Return approval

### Hệ thống trả hàng tự động dựa trên điều kiện sản phẩm

Trong bài toán này, hệ thống cần phân loại yêu cầu trả hàng ngay lập tức dựa trên lý do và tình trạng hàng hóa. Nếu khách hàng chọn lý do là hàng lỗi và đính kèm video bằng chứng, hệ thống sẽ tự động phê duyệt và cấp mã vận đơn trả hàng. Ngược lại, nếu là lý do chủ quan từ phía người mua như đổi ý, hệ thống yêu cầu chuyển qua bước xét duyệt thủ công của nhân viên chăm sóc khách hàng. Bạn cần quản lý các trạng thái từ lúc chờ duyệt, đã duyệt, đến khi hàng về kho và được kiểm tra lại.

### Quản lý quy trình kiểm định hàng trả về tại kho

Sau khi một yêu cầu trả hàng được hệ thống chấp nhận, quy trình tiếp theo là tiếp nhận hàng tại kho. Bài toán tập trung vào việc đối soát giữa nội dung ghi trong phiếu yêu cầu và thực tế hàng hóa nhận được. Nhân viên kho sẽ cập nhật tình trạng hàng khi mở kiện, ví dụ như còn nguyên tem mác hay đã qua sử dụng. Nếu hàng hóa không đúng như mô tả ban đầu, hệ thống phải cho phép người bán từ chối hoàn tiền dù trước đó đã phê duyệt cho gửi trả lại.

### Xử lý trả hàng và đổi trả sản phẩm thay thế

Đây là kịch bản phức tạp khi khách hàng không muốn nhận lại tiền mà muốn đổi sang một sản phẩm khác. Hệ thống cần quản lý việc phê duyệt trả hàng cũ đồng thời tạo ra một đơn hàng mới với giá trị tương đương hoặc chênh lệch. Quy trình này đòi hỏi sự liên kết chặt chẽ giữa tồn kho của sản phẩm cũ bị lỗi và tồn kho của sản phẩm mới sắp gửi đi, đảm bảo giữ chỗ hàng trong kho ngay khi yêu cầu đổi trả được phê duyệt.

### Tính toán phí vận chuyển ngược và phí lưu kho

Khi một yêu cầu trả hàng được phê duyệt, hệ thống phải xác định ai là người chịu phí vận chuyển. Nếu lỗi do nhà sản xuất, người bán chịu phí; nếu do khách hàng đổi ý, phí sẽ trừ vào tiền hoàn lại. Bài toán yêu cầu thiết kế logic để tích hợp với các đơn vị vận chuyển bên thứ ba nhằm lấy mã vận đơn (tracking) và tính toán trước số tiền thực tế khách hàng sẽ nhận được sau khi trừ đi các loại phí dịch vụ phát sinh.

### Phân quyền phê duyệt đa cấp cho đơn hàng giá trị cao

Đối với các sàn thương mại điện tử xa xỉ, việc phê duyệt trả hàng không thể thực hiện bởi một nhân viên duy nhất. Các đơn hàng có giá trị trên một ngưỡng nhất định cần quy trình phê duyệt hai lớp: đầu tiên là nhân viên kiểm tra hồ sơ, sau đó là quản lý cấp cao xác nhận cuối cùng. Hệ thống cần lưu vết (audit log) chi tiết ai đã phê duyệt vào thời điểm nào và những ghi chú trao đổi giữa các cấp quản lý trong quá trình xử lý yêu cầu.

### Quản lý hạn trả hàng và gia hạn thời gian gửi trả

Mỗi yêu cầu trả hàng sau khi được chấp nhận sẽ có một thời hạn nhất định để khách hàng gửi hàng ra bưu cục. Nếu quá thời gian này mà mã vận đơn chưa có tín hiệu hoạt động, hệ thống sẽ tự động hủy yêu cầu trả hàng và đóng phiếu hỗ trợ. Bài toán này đặt ra yêu cầu về việc xử lý các tác vụ nền (background jobs) để theo dõi thời gian thực và cho phép nhân viên hỗ trợ gia hạn thêm thời gian trong các trường hợp đặc biệt.

### Hoàn tiền đa phương thức sau khi phê duyệt thành công

Sau khi bước chấp nhận trả hàng hoàn tất và hàng đã về kho, hệ thống cần xử lý lệnh hoàn tiền. Khách hàng có thể đã thanh toán bằng nhiều hình thức khác nhau như thẻ tín dụng, ví điện tử hoặc điểm thưởng thành viên. Bài toán yêu cầu thiết kế cách thức phân bổ số tiền hoàn lại đúng vào nguồn tiền ban đầu của khách hàng, đồng thời cập nhật lại các chương trình khuyến mãi hoặc mã giảm giá đã áp dụng cho đơn hàng đó.

### Phân tích tỷ lệ trả hàng để cảnh báo chất lượng sản phẩm

Hệ thống không chỉ dừng lại ở việc phê duyệt mà còn phải thu thập dữ liệu để phục vụ báo cáo. Khi một sản phẩm có tỷ lệ yêu cầu trả hàng vượt quá mức cho phép trong một khoảng thời gian ngắn, hệ thống sẽ gửi cảnh báo đến bộ phận thu mua hoặc người bán. Bạn cần thiết kế các bảng lưu trữ lý do trả hàng chi tiết để có thể phân loại được lỗi là do khâu vận chuyển đóng gói hay do chất lượng cốt lõi của sản phẩm từ nhà máy.
