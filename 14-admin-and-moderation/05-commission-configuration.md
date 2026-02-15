# Commission configuration

### Thiết lập hoa hồng mặc định theo danh mục hàng hóa

Sàn thương mại điện tử áp dụng các mức phí hoa hồng khác nhau tùy vào loại sản phẩm mà người bán đăng tải. Ví dụ, danh mục đồ điện tử có mức phí là ba phần trăm do giá trị sản phẩm cao và biên lợi nhuận thấp, trong khi danh mục thời trang có mức phí là mười phần trăm. Hệ thống cần tự động xác định mức phí này khi người bán tạo sản phẩm mới dựa trên cây danh mục và áp dụng nó vào giá trị đơn hàng khi giao dịch hoàn tất.

### Cấu hình mức hoa hồng ưu đãi cho từng người bán cụ thể

Để thu hút các thương hiệu lớn hoặc người bán có doanh số cao, nền tảng cho phép thỏa thuận các mức hoa hồng riêng biệt thay vì dùng mức chung của hệ thống. Một người bán cụ thể có thể được hưởng mức phí chỉ một phần trăm cho tất cả các mặt hàng họ bán ra bất kể thuộc danh mục nào. Bài toán này yêu cầu database phải có cơ chế ưu tiên: nếu có cấu hình riêng cho người bán thì bỏ qua cấu hình mặc định của danh mục.

### Hoa hồng biến thiên theo chương trình khuyến mãi và sự kiện

Vào các ngày lễ hoặc sự kiện mua sắm lớn, nền tảng thực hiện chương trình giảm phí hoa hồng để khuyến khích người bán giảm giá sâu cho khách hàng. Mức hoa hồng mới này chỉ có hiệu lực trong một khoảng thời gian nhất định, ví dụ từ ngày mười đến ngày mười hai hằng tháng. Sau khi kết thúc thời gian sự kiện, hệ thống phải tự động quay lại áp dụng mức hoa hồng cũ mà không cần người quản trị phải can thiệp thủ công vào từng bản ghi.

### Phân bậc hoa hồng dựa trên tổng doanh thu tháng của người bán

Nền tảng áp dụng chính sách khuyến khích người bán tăng trưởng doanh số bằng cách giảm dần tỷ lệ hoa hồng khi họ đạt được các mốc doanh thu nhất định. Nếu tổng doanh thu trong tháng dưới một trăm triệu, mức phí là năm phần trăm. Nếu đạt từ một trăm triệu đến năm trăm triệu, mức phí giảm xuống còn bốn phần trăm. Bài toán này đòi hỏi hệ thống phải tính toán doanh thu tích lũy thời gian thực hoặc định kỳ để cập nhật mức phí áp dụng cho các đơn hàng tiếp theo.

### Hoa hồng cố định theo đơn vị sản phẩm thay vì tỷ lệ phần trăm

Đối với một số loại dịch vụ hoặc hàng hóa đặc thù như nạp thẻ điện thoại hoặc vé máy bay, nền tảng không thu theo tỷ lệ phần trăm mà thu một số tiền cố định trên mỗi sản phẩm bán được. Ví dụ, mỗi vé xem phim bán ra nền tảng thu phí cố định là năm nghìn đồng. Hệ thống cần hỗ trợ cấu hình linh hoạt giữa hai loại hình: thu theo phần trăm hoặc thu một con số tiền mặt cụ thể cho từng loại cấu hình.

### Xử lý hoa hồng khi đơn hàng có nhiều sản phẩm từ nhiều danh mục

Một khách hàng thực hiện một đơn hàng duy nhất nhưng bên trong bao gồm một chiếc điện thoại và một chiếc áo thun. Mỗi sản phẩm này thuộc các danh mục có mức hoa hồng khác nhau. Hệ thống cần tách nhỏ đơn hàng hoặc có logic tính toán chi tiết phí hoa hồng cho từng dòng sản phẩm (order item) thay vì tính trên tổng giá trị đơn hàng để đảm bảo số tiền thu về của nền tảng là chính xác theo từng danh mục.

### Điều chỉnh hoa hồng dựa trên phương thức thanh toán hoặc vận chuyển

Nền tảng có thỏa thuận với các đơn vị ví điện tử hoặc đơn vị vận chuyển để thúc đẩy người dùng sử dụng dịch vụ của họ. Nếu người mua chọn thanh toán qua ví điện tử liên kết, người bán sẽ được giảm một phần phí hoa hồng nền tảng như một hình thức hỗ trợ. Điều này yêu cầu hệ thống tính toán hoa hồng phải kết nối với dữ liệu về phương thức thanh toán và trạng thái vận chuyển để đưa ra con số cuối cùng sau khi đơn hàng thành công.

### Quản lý lịch sử thay đổi cấu hình hoa hồng và đối soát

Mức hoa hồng có thể thay đổi theo thời gian do chính sách kinh doanh. Khi một đơn hàng được tạo vào tháng trước nhưng đến tháng này mới hoàn tất thanh toán, hệ thống phải đảm bảo áp dụng mức hoa hồng tại thời điểm khách hàng đặt hàng chứ không phải mức mới nhất hiện tại. Bài toán này yêu cầu thiết kế database phải lưu trữ lịch sử các phiên bản cấu hình (versioning) để phục vụ việc đối soát và minh bạch tài chính với người bán.
