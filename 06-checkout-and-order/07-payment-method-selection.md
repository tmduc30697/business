# Payment method selection

### Quản lý danh mục phương thức thanh toán theo khu vực địa lý

Hệ thống cần hiển thị các tùy chọn thanh toán khác nhau dựa trên vị trí của người mua. Ví dụ, khách hàng tại Việt Nam có thể chọn MoMo hoặc ZaloPay, trong khi khách hàng quốc tế chỉ thấy tùy chọn Thẻ tín dụng hoặc PayPal. Bài toán yêu cầu thiết kế cách lưu trữ cấu hình phương thức thanh toán đi kèm với các điều kiện về quốc gia, loại tiền tệ hỗ trợ và trạng thái bật tắt của từng cổng thanh toán để frontend có thể truy vấn và hiển thị đúng cho người dùng.

### Tính toán phí giao dịch và chiết khấu theo phương thức thanh toán

Mỗi phương thức thanh toán thường đi kèm với một mức phí xử lý khác nhau từ phía nhà cung cấp dịch vụ. Hệ thống cần lưu trữ cấu hình phí giao dịch cho từng phương thức, ví dụ như thanh toán qua thẻ tín dụng chịu phí 2.5% trong khi chuyển khoản ngân hàng là miễn phí. Khi người dùng chọn một phương thức, hệ thống phải tự động tính toán lại tổng số tiền cuối cùng bao gồm phí dịch vụ hoặc áp dụng các mã giảm giá chỉ dành riêng cho một loại ví điện tử nhất định.

### Xử lý quy trình thanh toán nhiều bước và trạng thái giao dịch

Khi người dùng chọn thanh toán qua thẻ tín dụng hoặc ví điện tử, quy trình không kết thúc ngay mà phải trải qua nhiều trạng thái như chờ thanh toán, đang xử lý, thành công hoặc thất bại. Bài toán này tập trung vào việc thiết kế bảng ghi nhận lịch sử giao dịch, lưu trữ các mã tham chiếu từ phía đối tác thứ ba và cách cập nhật trạng thái đơn hàng tương ứng khi nhận được phản hồi từ webhook của cổng thanh toán.

### Hệ thống lưu trữ thông tin thanh toán ưu tiên cho lần sau

Để tăng trải nghiệm người dùng, hệ thống cần cho phép khách hàng lưu lại thông tin thẻ hoặc liên kết ví điện tử sau lần thanh toán đầu tiên. Thách thức ở đây là thiết kế cấu hình lưu trữ các token đại diện cho thông tin thanh toán mà không vi phạm các tiêu chuẩn bảo mật, giúp người dùng có thể thực hiện thanh toán nhanh trong những lần mua hàng tiếp theo mà không cần nhập lại dữ liệu.

### Tích hợp hệ thống đối soát chuyển khoản ngân hàng thủ công

Đối với phương thức chuyển khoản ngân hàng, việc xác nhận thanh toán thường không diễn ra tức thì như ví điện tử. Bài toán yêu cầu thiết kế quy trình lưu trữ thông tin lệnh chuyển khoản từ phía khách hàng như ảnh chụp biên lai hoặc mã nội dung chuyển khoản. Đồng thời, hệ thống cần có giao diện và cấu trúc dữ liệu để nhân viên kế toán có thể kiểm tra, đối soát và phê duyệt trạng thái thanh toán của đơn hàng một cách thủ công.

### Quản lý hạn mức và điều kiện áp dụng phương thức thanh toán

Một số phương thức thanh toán có giới hạn về giá trị đơn hàng tối thiểu hoặc tối đa. Chẳng hạn, phương thức trả góp chỉ xuất hiện nếu đơn hàng trên 3 triệu đồng, hoặc phương thức COD bị vô hiệu hóa nếu tổng giá trị đơn hàng vượt quá 10 triệu đồng để giảm thiểu rủi ro vận chuyển. Bạn cần thiết kế các quy tắc nghiệp vụ lưu trữ trong database để hệ thống tự động lọc bỏ các phương thức không khả dụng trước khi hiển thị cho khách hàng.

### Xử lý hoàn tiền theo đúng phương thức thanh toán gốc

Khi một đơn hàng bị hủy hoặc trả hàng, hệ thống cần thực hiện quy trình hoàn tiền. Nguyên tắc thực tế là tiền phải được hoàn về đúng phương thức mà khách hàng đã sử dụng để thanh toán trước đó. Bài toán này yêu cầu thiết kế cấu trúc dữ liệu để liên kết chặt chẽ giữa giao dịch thanh toán đầu vào và giao dịch hoàn tiền đầu ra, đảm bảo tính minh bạch và dễ dàng theo dõi dòng tiền cho cả khách hàng và người quản trị.

### Hệ thống ghi nhật ký phản hồi và xử lý lỗi từ cổng thanh toán

Trong quá trình giao tiếp với các bên thứ ba như Stripe, VNPay hay MoMo, các lỗi kỹ thuật hoặc lỗi từ phía người dùng như sai mã OTP, hết hạn thẻ thường xuyên xảy ra. Hệ thống cần một cấu trúc log chi tiết để lưu trữ toàn bộ dữ liệu thô nhận được từ API của đối tác. Việc này giúp đội ngũ kỹ thuật có thể tra cứu nguyên nhân thất bại của một giao dịch cụ thể và cung cấp thông báo lỗi chính xác, thân thiện cho người dùng cuối.

### Quản lý ví nội bộ và thanh toán kết hợp

Nhiều hệ thống cho phép người dùng nạp tiền vào ví nội bộ hoặc sử dụng điểm thưởng để thanh toán. Bài toán thực tế là khách hàng muốn dùng kết hợp điểm thưởng để giảm giá một phần và thanh toán số tiền còn lại bằng thẻ tín dụng. Bạn cần thiết kế cách tách nhỏ một đơn hàng thành nhiều giao dịch con với các phương thức thanh toán khác nhau nhưng vẫn đảm bảo tính nhất quán về tổng tiền và trạng thái của toàn bộ đơn hàng.

### Tự động phân bổ doanh thu cho các bên liên quan

Trong mô hình sàn thương mại điện tử, số tiền khách hàng thanh toán cần được phân tách thành tiền hàng cho nhà bán lẻ, phí sàn và phí vận chuyển. Tùy vào phương thức thanh toán, thời gian tiền về tài khoản của sàn sẽ khác nhau. Bài toán yêu cầu thiết kế hệ thống theo dõi dòng tiền từ lúc khách thanh toán cho đến khi tiền được phân bổ vào số dư của các bên liên quan, bao gồm cả việc trừ đi các loại phí giao dịch tương ứng.
