# Order split by seller

### Quản lý kho hàng đa điểm của một người bán

Trong mô hình này, một người bán có thể sở hữu nhiều kho hàng tại các vị trí địa lý khác nhau. Khi khách hàng đặt một đơn hàng gồm nhiều sản phẩm, hệ thống cần tính toán xem những sản phẩm đó có sẵn ở cùng một kho hay không. Nếu các sản phẩm nằm ở các kho khác nhau, đơn hàng của người bán đó lại phải tiếp tục được tách nhỏ thành các kiện hàng riêng biệt để tối ưu lộ trình vận chuyển và thời gian đóng gói.

### Áp dụng mã giảm giá và chương trình khuyến mãi hỗn hợp

Bài toán phát sinh khi khách hàng áp dụng cùng lúc nhiều loại mã giảm giá như mã toàn sàn, mã riêng của từng người bán và mã hỗ trợ phí vận chuyển. Hệ thống phải xác định được giá trị giảm giá nào thuộc về trách nhiệm chi trả của sàn và giá trị nào khấu trừ trực tiếp vào doanh thu của người bán. Khi tách đơn, việc phân bổ số tiền giảm giá trên tổng giỏ hàng xuống từng đơn con phải đảm bảo tính chính xác đến từng đơn vị tiền tệ để phục vụ đối soát tài chính sau này.

### Tính toán phí vận chuyển và lựa chọn đơn vị vận chuyển theo vùng miền

Mỗi người bán trong giỏ hàng có thể đặt trụ sở tại các tỉnh thành khác nhau và hợp tác với các đơn vị vận chuyển khác nhau. Khi tách đơn, hệ thống cần gọi API của các đơn vị vận chuyển để lấy báo giá dựa trên cân nặng, kích thước của các sản phẩm thuộc người bán đó và khoảng cách đến địa chỉ người mua. Bài toán này đòi hỏi việc xử lý song song và gom nhóm các thông tin vận chuyển một cách logic trước khi hiển thị tổng chi phí cuối cùng cho khách hàng.

### Trạng thái thanh toán và quy trình hoàn tiền cho đơn hàng tách nhỏ

Đối với các đơn hàng thanh toán trước qua thẻ hoặc ví điện tử, khách hàng chỉ thực hiện một giao dịch thanh toán duy nhất cho tổng giá trị giỏ hàng. Tuy nhiên, khi một trong các đơn con bị hủy do người bán hết hàng hoặc người mua từ chối nhận hàng, hệ thống phải có cơ chế xử lý hoàn tiền một phần. Điều này yêu cầu thiết kế hệ thống thanh toán có khả năng liên kết nhiều đơn hàng con với một mã giao dịch gốc và quản lý dòng tiền minh bạch.

### Quản lý vòng đời đơn hàng và thông báo trạng thái độc lập

Sau khi đơn hàng tổng được tách, mỗi đơn con sẽ có một hành trình riêng biệt: người bán A có thể đóng gói rất nhanh trong khi người bán B đang chờ nhập hàng. Hệ thống cần cung cấp giao diện quản lý sao cho người mua có thể theo dõi tiến độ của từng kiện hàng một cách độc lập. Việc gửi thông báo qua email hoặc ứng dụng cũng cần được thiết kế để tránh gây phiền nhiễu nhưng vẫn đảm bảo khách hàng nắm bắt được đơn hàng nào đang đến gần.

### Ràng buộc về giá trị đơn hàng tối thiểu cho từng người bán

Nhiều người bán trên sàn đặt ra quy định chỉ xử lý đơn hàng nếu tổng giá trị sản phẩm đạt một ngưỡng tối thiểu để bù đắp chi phí vận hành. Khi khách hàng bỏ nhiều món đồ vào giỏ, hệ thống phải kiểm tra điều kiện này cho từng nhóm sản phẩm sau khi tách theo người bán. Nếu một nhóm không thỏa mãn, hệ thống phải cảnh báo người dùng ngay tại bước thanh toán hoặc yêu cầu người dùng mua thêm sản phẩm từ người bán đó.

### Phân bổ thuế VAT và hóa đơn điện tử cho từng thực thể kinh doanh

Trong một giỏ hàng đa người bán, mỗi người bán có thể là một cá nhân hoặc doanh nghiệp với mã số thuế khác nhau. Khi tách đơn hàng, thông tin xuất hóa đơn phải được tách bạch hoàn toàn. Bài toán yêu cầu hệ thống lưu trữ thông tin thuế chi tiết cho từng đơn con để khi khách hàng yêu cầu xuất hóa đơn, hệ thống có thể xuất nhiều hóa đơn điện tử khác nhau tương ứng với từng người bán thay vì một hóa đơn tổng không hợp lệ.

### Xử lý đồng bộ tồn kho thực tế tại thời điểm tách đơn

Đây là vấn đề nhạy cảm về hiệu năng khi có nhiều người dùng cùng thanh toán một lúc. Tại thời điểm hệ thống bắt đầu tách đơn hàng tổng thành các đơn con, số lượng tồn kho của từng sản phẩm tại từng người bán phải được khóa hoặc trừ tạm thời. Nếu việc tách đơn thất bại ở một người bán do hết hàng đột ngột, hệ thống phải có kịch bản xử lý cho các đơn con còn lại trong cùng giỏ hàng đó để đảm bảo tính nhất quán của dữ liệu.
