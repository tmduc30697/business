# Shipping fee calculation

### Quản lý bảng giá vận chuyển theo vùng miền và khối lượng quy đổi

Trong thực tế, đơn vị vận chuyển không chỉ tính phí dựa trên cân nặng thực tế mà còn dựa trên kích thước thùng hàng để tính ra khối lượng quy đổi. Bài toán yêu cầu hệ thống phải lưu trữ được các mốc khối lượng và bảng giá tương ứng cho từng vùng địa lý như nội tỉnh, nội vùng, và liên tỉnh. Hệ thống cần xác định được địa chỉ người gửi và người nhận thuộc phân loại vùng nào để áp dụng đơn giá chính xác nhất từ cơ sở dữ liệu.

### Tối ưu hóa lựa chọn kho hàng gần nhất để giảm chi phí

Một doanh nghiệp có nhiều kho hàng trải dài trên khắp cả nước và khi khách hàng đặt hàng, hệ thống phải tự động tính toán khoảng cách từ các kho đang còn hàng đến vị trí người mua. Bài toán đặt ra là làm sao để thiết kế database lưu trữ tọa độ hoặc mã vùng của kho hàng sao cho API có thể nhanh chóng so sánh và lựa chọn kho hàng tối ưu nhất. Việc này không chỉ ảnh hưởng đến phí vận chuyển mà còn quyết định thời gian giao hàng dự kiến cho khách.

### Tính phí dịch vụ giá trị gia tăng và phụ phí hàng hóa đặc biệt

Các đơn vị vận chuyển thường áp dụng thêm các loại phí phụ thu dựa trên tính chất của kiện hàng như hàng dễ vỡ, hàng quá khổ, hoặc hàng cần bảo quản lạnh. Ngoài ra, khách hàng có thể chọn thêm các dịch vụ như bảo hiểm hàng hóa, giao hàng thu tiền hộ hoặc giao hàng hỏa tốc. Bạn cần thiết kế hệ thống sao cho các phụ phí này có thể cộng dồn vào phí cơ bản một cách minh bạch và dễ dàng cập nhật đơn giá phụ phí theo từng thời điểm.

### Tích hợp đa đơn vị vận chuyển với cấu trúc phí khác nhau

Mỗi đối tác giao vận như Giao Hàng Nhanh, Viettel Post hay Grab đều có một cấu trúc tính phí và các ngưỡng chiết khấu riêng biệt cho doanh nghiệp. Bài toán yêu cầu thiết kế một hệ thống trung gian có khả năng lưu trữ cấu hình API và bảng giá riêng của từng đối tác. Khi người dùng đặt hàng, hệ thống sẽ gọi dữ liệu từ các bên này để so sánh và hiển thị danh sách các tùy chọn vận chuyển từ rẻ nhất đến nhanh nhất cho người dùng lựa chọn.

### Xử lý logic miễn phí vận chuyển và giảm giá theo điều kiện

Để kích cầu mua sắm, các sàn thương mại điện tử thường có các chương trình như miễn phí vận chuyển cho đơn hàng trên một giá trị nhất định hoặc hỗ trợ tối đa một số tiền phí vận chuyển cụ thể. Bài toán này đòi hỏi database phải quản lý được các chiến dịch khuyến mãi, giới hạn ngân sách cho từng đợt giảm giá vận chuyển. Logic tính toán phải xử lý được việc trừ số tiền giảm giá vào tổng phí vận chuyển cuối cùng trước khi hiển thị cho khách hàng.

### Quản lý phí vận chuyển cho đơn hàng tách kiện hoặc giao nhiều lần

Trong trường hợp đơn hàng có quá nhiều sản phẩm mà một kiện hàng không thể chứa hết, hoặc các sản phẩm nằm ở các kho khác nhau, hệ thống buộc phải tách thành nhiều kiện hàng nhỏ. Mỗi kiện hàng sẽ có trọng lượng và kích thước riêng, dẫn đến việc tính phí vận chuyển cho từng kiện và tổng hợp lại cho toàn bộ đơn hàng. Việc thiết kế Database phải đảm bảo mối quan hệ giữa một đơn hàng và nhiều vận đơn khác nhau để theo dõi chi phí chính xác.

### Điều chỉnh phí dựa trên thời điểm và nhu cầu thị trường

Vào các dịp lễ Tết hoặc thời tiết xấu, các đơn vị vận chuyển có thể áp dụng thêm hệ số nhân phí dịch vụ hoặc phí cao điểm. Bài toán thực tế là làm sao để cấu hình hệ thống có khả năng tự động điều chỉnh đơn giá dựa trên các tham số thời gian hoặc tình trạng vận hành của hệ thống tại một khu vực cụ thể. Điều này yêu cầu một thiết kế hệ thống linh hoạt, cho phép các quản trị viên cập nhật các quy tắc tính phí mà không cần thay đổi mã nguồn của ứng dụng.
