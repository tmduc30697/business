# Shipping fee subsidy

### Quản lý mã giảm giá vận chuyển theo điều kiện đơn hàng tối thiểu

Trong mô hình này, hệ thống cần cho phép người quản lý tạo ra các chiến dịch khuyến mãi mà ở đó phí vận chuyển chỉ được giảm khi giá trị giỏ hàng đạt một ngưỡng nhất định. Bài toán đặt ra là làm sao để lưu trữ linh hoạt các điều kiện như giá trị đơn hàng tối thiểu, mức giảm tối đa, và phạm vi áp dụng cho từng đơn vị vận chuyển cụ thể. Khi người dùng thanh toán, hệ thống phải kiểm tra tính hợp lệ của đơn hàng so với các quy tắc này để quyết định có áp dụng trợ giá hay không.

### Phân bổ ngân sách trợ giá giữa sàn thương mại điện tử và người bán

Đây là bài toán về việc chia sẻ chi phí vận chuyển giữa nhiều thực thể khác nhau. Một chương trình trợ giá có thể được tài trợ 50 phần trăm bởi sàn và 50 phần trăm bởi người bán, hoặc sàn hỗ trợ một số tiền cố định và người bán chịu phần còn lại. Việc thiết kế cơ sở dữ liệu phải đảm bảo ghi vết được nguồn tiền chi trả cho mỗi đơn hàng để phục vụ quá trình đối soát tài chính và thanh toán cho đơn vị vận chuyển vào cuối kỳ.

### Giới hạn lượt sử dụng trợ giá theo người dùng và thời gian

Để tránh việc lạm dụng khuyến mãi, hệ thống cần áp dụng các chính sách giới hạn số lần một khách hàng được hưởng trợ giá vận chuyển trong một ngày, một tuần hoặc một tháng. Bài toán này đòi hỏi khả năng truy vấn nhanh lịch sử sử dụng của người dùng và cập nhật trạng thái hạn ngạch ngay lập tức khi đơn hàng được tạo. Điều này ảnh hưởng trực tiếp đến cách bạn thiết kế bảng lưu trữ lịch sử giao dịch và cơ chế khóa bản ghi để tránh tình trạng sử dụng vượt mức cho phép.

### Trợ giá vận chuyển dựa trên vị trí địa lý và vùng đặc biệt

Nhiều nền tảng áp dụng chính sách trợ giá khác nhau dựa trên khoảng cách giữa kho hàng của người bán và địa chỉ nhận hàng của người mua. Ví dụ, các đơn hàng nội tỉnh có mức trợ giá thấp hơn so với đơn hàng liên tỉnh, hoặc các khu vực hải đảo, vùng sâu vùng xa sẽ có chính sách hỗ trợ riêng biệt để kích cầu. Hệ thống cần quản lý được danh mục vùng miền và các bảng giá vận chuyển tương ứng để tính toán mức hỗ trợ chính xác ngay tại bước xem giỏ hàng.

### Xử lý hoàn trả phí trợ giá khi đơn hàng bị hủy hoặc trả hàng

Khi một đơn hàng đã được áp dụng trợ giá nhưng sau đó bị hủy một phần hoặc toàn bộ, hệ thống cần có cơ chế xử lý logic hoàn trả. Nếu khách hàng trả lại một phần hàng khiến giá trị còn lại không còn đủ điều kiện hưởng trợ giá, hệ thống phải tính toán lại số tiền thực tế khách hàng cần trả hoặc hoàn lại cho người bán. Bài toán này tập trung vào việc duy trì tính toàn vẹn dữ liệu giữa các bảng đơn hàng, bảng khuyến mãi và bảng dòng tiền.

### Hệ thống tích điểm đổi mã trợ giá vận chuyển

Thay vì tặng trực tiếp, hệ thống cho phép người dùng sử dụng điểm tích lũy từ các hoạt động mua sắm để đổi lấy các thẻ trợ giá vận chuyển. Bài toán yêu cầu thiết kế quy trình từ lúc phát hành thẻ, quản lý kho thẻ trong ví của người dùng, cho đến khi thẻ được áp dụng vào đơn hàng và hết hạn sử dụng. Bạn cần chú ý đến trạng thái của thẻ như chưa sử dụng, đã sử dụng, đang chờ xử lý hoặc đã hết hạn.

### Ưu tiên áp dụng nhiều lớp trợ giá vận chuyển đồng thời

Trong thực tế, một đơn hàng có thể thỏa mãn nhiều chương trình trợ giá cùng lúc, ví dụ như mã giảm giá của sàn cộng với chương trình miễn phí vận chuyển của người bán và ưu đãi từ ví điện tử. Bài toán yêu cầu thiết kế logic ưu tiên để xác định xem mã nào sẽ được áp dụng trước, hoặc cách kết hợp các mã này sao cho tổng mức trợ giá không vượt quá phí vận chuyển thực tế mà đơn vị giao vận yêu cầu.

### Theo dõi và cảnh báo ngân sách chiến dịch trợ giá theo thời gian thực

Mỗi chiến dịch trợ giá thường có một hạn mức ngân sách tổng, ví dụ là một tỷ đồng. Khi khách hàng đặt hàng liên tục, ngân sách này sẽ vơi dần đi. Bài toán đặt ra là làm sao để hệ thống có thể theo dõi biến động ngân sách này một cách chính xác trong môi trường có hàng nghìn giao dịch cùng lúc, và tự động ngắt áp dụng trợ giá ngay khi ngân sách chạm ngưỡng giới hạn để tránh gây thất thoát cho doanh nghiệp.
