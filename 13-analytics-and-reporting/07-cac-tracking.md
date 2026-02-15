# CAC tracking

### Phân bổ chi phí quảng cáo từ nhiều nguồn về một khách hàng duy nhất

Hệ thống cần ghi nhận một khách hàng mới đến từ đâu khi họ có thể đã nhấp vào quảng cáo Facebook vào ngày đầu tiên, sau đó nhấp vào quảng cáo Google vào ngày thứ ba và cuối cùng mới đăng ký tài khoản. Bài toán đặt ra là làm thế nào để lưu trữ các điểm chạm này trong cơ sở dữ liệu và quyết định xem chi phí tìm kiếm khách hàng đó sẽ được tính cho kênh nào hoặc chia tỷ lệ cho cả hai kênh theo các mô hình tương tác khác nhau.

### Đồng bộ dữ liệu chi tiêu định kỳ từ các nền tảng quảng cáo bên thứ ba

Các nền tảng như Facebook Ads hay Google Ads cung cấp dữ liệu chi phí thông qua API theo từng chiến dịch và từng ngày. Hệ thống của bạn cần một cơ chế để tự động lấy dữ liệu này về và lưu trữ vào bảng chi phí marketing. Thách thức ở đây là cấu trúc dữ liệu của mỗi nền tảng mỗi khác, đòi hỏi một thiết kế database linh hoạt để có thể chuẩn hóa mọi nguồn chi phí về cùng một đơn vị đo lường chung nhằm phục vụ việc tính toán tổng chi phí đã bỏ ra.

### Theo dõi hiệu quả của các chiến dịch sử dụng mã giới thiệu cá nhân

Doanh nghiệp thực hiện chiến dịch tăng trưởng bằng cách cho phép người dùng hiện tại gửi mã giới thiệu cho bạn bè. Mỗi khi có một người dùng mới đăng ký thành công qua mã này, hệ thống phải ghi nhận chi phí quà tặng hoặc tiền thưởng cho người giới thiệu là một phần của chi phí để có được khách hàng mới đó. Việc thiết kế bảng dữ liệu phải thể hiện được mối quan hệ giữa người giới thiệu, người được giới thiệu và giá trị quy đổi của phần thưởng tại thời điểm phát sinh giao dịch.

### Tính toán chi phí khách hàng mới theo khu vực địa lý và thời gian

Để tối ưu hóa ngân sách, nhà quản lý cần biết chi phí để có một khách hàng ở thành phố lớn có cao hơn ở các tỉnh lẻ hay không, hoặc chi phí này biến động thế nào giữa các tháng trong năm. Bài toán yêu cầu hệ thống phải lưu trữ thông tin vị trí của khách hàng khi họ đăng ký và liên kết nó với các chiến dịch quảng cáo được nhắm mục tiêu theo vùng tương ứng để đưa ra các báo cáo phân tích chi tiết theo nhiều chiều dữ liệu khác nhau.

### Xử lý sự sai lệch giữa số lượt nhấp quảng cáo và số lượng đăng ký thực tế

Trong thực tế, số lượng người nhấp vào quảng cáo luôn cao hơn số người thực sự trở thành khách hàng. Hệ thống cần theo dõi tỷ lệ chuyển đổi này bằng cách gắn các tham số theo dõi đặc biệt vào đường dẫn trang web. Dữ liệu cần được thiết kế sao cho có thể truy ngược từ một khách hàng cụ thể về đúng mã định danh của lần nhấp chuột đó, từ đó giúp bộ phận kỹ thuật và marketing xác định được những điểm rơi rò rò rỉ ngân sách trong phễu bán hàng.

### Phân loại chi phí cố định và chi phí biến đổi trong vận hành marketing

Ngoài chi phí trực tiếp trả cho các nền tảng quảng cáo, doanh nghiệp còn tốn chi phí cho nhân sự vận hành hoặc các công cụ hỗ trợ marketing hàng tháng. Bài toán yêu cầu thiết kế một hệ thống quản lý các loại chi phí gián tiếp này và có cơ chế phân bổ chúng vào tổng chi phí để tính toán chỉ số giá vốn khách hàng một cách chính xác nhất, tránh việc chỉ nhìn thấy phần chi phí quảng cáo mà bỏ qua các chi phí vận hành ẩn.

### Loại bỏ các khách hàng cũ quay lại khỏi danh sách tính toán chi phí mới

Chỉ số CAC chỉ áp dụng cho khách hàng mới hoàn toàn. Tuy nhiên, nhiều khách hàng cũ vẫn nhấp vào quảng cáo của các chiến dịch tìm kiếm khách hàng mới. Hệ thống cần có logic kiểm tra thông tin định danh như số điện thoại hoặc email trong cơ sở dữ liệu để loại trừ những đối tượng này khi tính toán hiệu quả của chiến dịch, đảm bảo rằng ngân sách marketing được tính đúng cho việc tăng trưởng tập khách hàng mới thay vì duy trì khách hàng cũ.

### Theo dõi chi phí từ các kênh marketing không chính thống và offline

Nhiều doanh nghiệp sử dụng các kênh như bảng quảng cáo ngoài trời hoặc tờ rơi để thu hút khách hàng. Vì không có API để đo lường trực tiếp, hệ thống cần thiết kế các giao diện cho phép nhập liệu thủ công chi phí và các công cụ đo lường gián tiếp như mã QR đặc biệt cho từng địa điểm. Dữ liệu từ các nguồn ngoại tuyến này phải được tích hợp đồng nhất với dữ liệu trực tuyến để cung cấp cái nhìn tổng thể về hiệu quả sử dụng vốn của toàn bộ doanh nghiệp.
