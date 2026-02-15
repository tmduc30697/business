# Auto deduct stock

### Quản lý tồn kho biến thể cho sàn thương mại điện tử

Trong mô hình này, một sản phẩm cơ bản có thể có nhiều lựa chọn như màu sắc và kích cỡ khác nhau. Khi khách hàng đặt mua một chiếc áo thun màu xanh size L, hệ thống không được trừ vào tổng số lượng áo thun chung mà phải xác định chính xác mã SKU cụ thể của biến thể đó để trừ tồn kho. Bài toán yêu cầu xử lý mối quan hệ giữa bảng sản phẩm chính và bảng biến thể, đảm bảo rằng khi một biến thể hết hàng thì người dùng không thể đặt lệnh mua nhưng các biến thể khác vẫn hoạt động bình thường.

### Giữ chỗ hàng hóa trong thời gian chờ thanh toán

Khi khách hàng thêm sản phẩm vào giỏ hàng và tiến hành đặt hàng nhưng chưa thanh toán ngay qua cổng điện tử, hệ thống cần có cơ chế tạm giữ hàng. Bài toán đặt ra là số lượng tồn kho thực tế sẽ bị trừ tạm thời để tránh việc người khác mua mất, nhưng nếu sau mười lăm phút khách hàng không hoàn tất thanh toán, hệ thống phải tự động hoàn lại số lượng đó vào kho. Điều này đòi hỏi thiết kế logic về trạng thái đơn hàng và các tiến trình chạy ngầm để kiểm tra thời hạn của các giao dịch đang treo.

### Trừ kho cho các gói sản phẩm combo hoặc set quà tặng

Hệ thống bán các gói combo bao gồm nhiều sản phẩm đơn lẻ khác nhau để khuyến khích mua sắm. Khi một combo được xác nhận bán ra, hệ thống không có một mã tồn kho riêng cho combo đó mà phải thực hiện việc trừ tồn kho của từng món hàng thành phần cấu thành nên combo theo tỷ lệ định sẵn. Thách thức ở đây là nếu chỉ cần một món thành phần trong combo hết hàng, hệ thống phải cập nhật trạng thái hết hàng cho tất cả các combo có chứa thành phần đó để tránh tình trạng đơn hàng không thể hoàn tất.

### Điều phối tồn kho đa kho hàng theo vị trí địa lý

Doanh nghiệp có nhiều kho hàng đặt tại các tỉnh thành khác nhau để tối ưu tốc độ giao hàng. Khi đơn hàng được xác nhận, hệ thống cần dựa trên quy tắc định nghĩa sẵn như khoảng cách gần nhất hoặc kho còn nhiều hàng nhất để quyết định sẽ trừ tồn kho ở kho hàng nào. Bài toán này yêu cầu cấu trúc dữ liệu phải quản lý được số lượng hàng hóa chi tiết theo từng ID kho và lịch sử xuất kho phải ghi nhận chính xác địa điểm hàng đã rời đi để phục vụ việc kiểm toán sau này.

### Xử lý tranh chấp tồn kho trong sự kiện Flash Sale

Trong các đợt giảm giá lớn, có hàng nghìn người cùng nhấn nút mua một sản phẩm có số lượng giới hạn tại cùng một thời điểm. Bài toán yêu cầu thiết kế hệ thống có khả năng xử lý các yêu cầu ghi đọc dữ liệu cực lớn mà không xảy ra tình trạng bán quá số lượng thực tế hiện có. Việc trừ tồn kho phải đảm bảo tính nhất quán dữ liệu tuyệt đối, tránh hiện tượng nhiều giao dịch cùng đọc một số dư tồn kho cũ và ghi đè kết quả dẫn đến sai lệch con số cuối cùng.

### Quản lý tồn kho thực tế và tồn kho ảo cho bán hàng đa kênh

Doanh nghiệp bán hàng đồng thời trên website, cửa hàng trực tiếp và các sàn thương mại điện tử trung gian. Hệ thống cần một cơ chế đồng bộ tồn kho tập trung, nơi mà khi một đơn hàng từ sàn thương mại điện tử được xác nhận, số lượng hàng khả dụng trên website và tại cửa hàng cũng phải giảm xuống ngay lập tức. Bài toán này tập trung vào việc thiết kế các API cập nhật thời gian thực và xử lý độ trễ dữ liệu giữa các nền tảng khác nhau để tránh việc khách hàng đặt mua hàng khi thực tế kho đã cạn.

### Khấu trừ tồn kho theo lô sản xuất và hạn sử dụng

Đối với các mặt hàng như thực phẩm hoặc mỹ phẩm, việc trừ tồn kho không đơn thuần là giảm một con số mà phải tuân theo nguyên tắc nhập trước xuất trước hoặc ưu tiên hàng sắp hết hạn. Khi đơn hàng được thanh toán thành công, hệ thống tự động quét qua danh sách các lô hàng hiện có để trừ vào lô có hạn sử dụng gần nhất. Thiết kế database cho bài toán này cần quản lý chi tiết thông tin lô hàng, ngày sản xuất và hạn dùng đính kèm với mỗi lần nhập kho.

### Hoàn trả tồn kho khi đơn hàng bị hủy hoặc trả hàng

Một quy trình auto deduct stock hoàn chỉnh không thể thiếu cơ chế đảo ngược. Khi khách hàng hủy đơn sau khi đã thanh toán hoặc thực hiện quy trình trả hàng hoàn tiền do lỗi, hệ thống phải thực hiện cộng lại số lượng vào kho đúng bằng số lượng đã trừ trước đó. Bài toán này đòi hỏi việc lưu trữ log giao dịch tồn kho cực kỳ chi tiết để biết chính xác đơn hàng đó đã từng trừ bao nhiêu sản phẩm, tại kho nào, nhằm đảm bảo quy trình hoàn kho diễn ra minh bạch và không bị thất thoát.
