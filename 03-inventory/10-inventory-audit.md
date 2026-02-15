# Inventory audit

### Quản lý phiên kiểm kho theo khu vực và nhân viên phụ trách

Trong các kho hàng lớn, việc kiểm tra toàn bộ kho cùng một lúc là bất khả thi. Hệ thống cần cho phép tạo ra các đợt kiểm kê nhỏ theo từng khu vực hoặc kệ hàng cụ thể. Mỗi đợt kiểm kê sẽ được gán cho một hoặc nhiều nhân viên thực hiện. Bài toán đặt ra là làm sao để quản lý trạng thái của từng phiên kiểm kê, ghi nhận thời gian bắt đầu, thời gian kết thúc và đảm bảo rằng một vị trí hàng hóa không bị kiểm kê chồng lấn bởi hai phiên khác nhau trong cùng một thời điểm.

### Đối chiếu dữ liệu tồn kho tức thời tại thời điểm chốt sổ

Thách thức lớn nhất trong kiểm kê là hàng hóa vẫn tiếp tục biến động (nhập thêm hoặc xuất đi) trong khi nhân viên đang đếm hàng. Hệ thống cần có cơ chế đóng băng số liệu tồn kho trên sổ sách tại một thời điểm chính xác để làm mốc so sánh. Khi nhân viên nhập số lượng thực tế vào, hệ thống phải tính toán được sự chênh lệch dựa trên con số đã chốt đó, thay vì so sánh với số tồn kho liên tục thay đổi trong cơ sở dữ liệu thời gian thực.

### Xử lý sai lệch đơn vị tính và quy cách đóng gói

Nhiều mặt hàng được lưu trữ dưới nhiều đơn vị khác nhau như thùng, kiện hoặc cái lẻ. Nhân viên kiểm kho có thể đếm theo thùng nhưng hệ thống lại quản lý theo cái. Bài toán yêu cầu thiết kế cơ sở dữ liệu và logic API sao cho có thể tự động quy đổi số lượng thực tế về đơn vị chuẩn để đối chiếu. Ngoài ra, cần ghi lại chi tiết việc nhân viên đã đếm bao nhiêu thùng và bao nhiêu cái lẻ để phục vụ việc truy soát nguồn gốc sai lệch sau này.

### Quy trình phê duyệt điều chỉnh tồn kho sau kiểm kê

Không phải mọi sai lệch sau khi phát hiện đều được cập nhật ngay vào kho. Những sai sót vượt quá một ngưỡng giá trị nhất định hoặc thuộc danh mục hàng cao cấp cần phải qua bước phê duyệt của quản lý kho hoặc kế toán trưởng. Hệ thống cần lưu trữ các phiếu kiểm kê ở trạng thái chờ xử lý, ghi nhận lý do sai lệch (như hàng hỏng, mất cắp, hoặc lỗi nhập liệu) và chỉ khi có chữ ký số hoặc lệnh xác nhận thì số tồn kho thực tế mới được cập nhật vào bảng cân đối chính.

### Truy vết lịch sử biến động giữa các kỳ kiểm kê

Để tìm ra nguyên nhân tại sao hàng hóa bị thất thoát, người dùng cần xem lại toàn bộ các giao dịch nhập xuất phát sinh giữa hai lần kiểm kê gần nhất. Bài toán này đòi hỏi thiết kế hệ thống có khả năng truy xuất lịch sử giao dịch cực nhanh và liên kết chặt chẽ với các mã phiếu kiểm kê. Việc này giúp hệ thống tự động gợi ý các giao dịch nghi ngờ có sai sót dẫn đến việc lệch kho hiện tại.

### Kiểm kê theo mã định danh duy nhất Serial Number hoặc IMEI

Đối với các mặt hàng điện tử hoặc giá trị cao, việc kiểm kê không chỉ là đếm số lượng mà còn là xác nhận sự hiện diện của từng mã định danh cụ thể. Bài toán yêu cầu hệ thống đối chiếu danh sách các mã Serial Number hiện có trong kho với danh sách nhân viên quét được thực tế. Nếu phát hiện một mã có trong hệ thống nhưng không thấy ở kho, hoặc một mã lạ xuất hiện ở kho nhưng không có trong dữ liệu, hệ thống phải đưa ra cảnh báo chính xác về mã đó.

### Quản lý hạn sử dụng và chất lượng hàng hóa khi kiểm kê

Trong quá trình kiểm kê thực tế, nhân viên không chỉ đếm số lượng mà còn phải phân loại tình trạng hàng hóa như hàng tốt, hàng móp méo, hoặc hàng sắp hết hạn sử dụng. Hệ thống cần hỗ trợ việc cập nhật trạng thái chất lượng này vào cơ sở dữ liệu. Nếu một mặt hàng vẫn đủ số lượng nhưng đã bị hỏng, hệ thống phải thực hiện quy trình điều chuyển loại kho từ kho hàng bán sang kho hàng lỗi hoặc chờ tiêu hủy.

### Tối ưu hóa lộ trình kiểm kê dựa trên sơ đồ kho

Để việc kiểm kê diễn ra nhanh chóng, hệ thống cần cung cấp danh sách các mặt hàng cần kiểm tra theo một thứ tự logic dựa trên vị trí địa lý trong kho (tầng, dãy, kệ). Bài toán này yêu cầu thiết kế cơ sở dữ liệu về sơ đồ kho (Warehouse Map) và tích hợp vào API lấy danh sách kiểm kê sao cho nhân viên có thể di chuyển theo một đường thẳng thay vì phải đi lại giữa các khu vực nhiều lần.
