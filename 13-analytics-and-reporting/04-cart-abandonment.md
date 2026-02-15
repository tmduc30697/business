# Cart abandonment

### Theo dõi thời gian tồn tại của giỏ hàng và định nghĩa trạng thái bỏ rơi

Hệ thống cần ghi nhận thời điểm chính xác khi người dùng thêm sản phẩm đầu tiên vào giỏ hàng và thời điểm cập nhật cuối cùng. Một giỏ hàng được coi là bị bỏ rơi nếu sau một khoảng thời gian nhất định, ví dụ là 24 giờ kể từ lần tương tác cuối cùng, người dùng vẫn không tiến hành thanh toán. Bài toán này yêu cầu bạn thiết kế bảng lưu trữ giỏ hàng với các mốc thời gian chi tiết và một cơ chế quét dữ liệu tự động để phân loại trạng thái giỏ hàng từ đang hoạt động sang đã bị bỏ rơi.

### Lưu trữ lịch sử thay đổi sản phẩm trong giỏ hàng trước khi rời đi

Để phân tích lý do người dùng bỏ cuộc, hệ thống không chỉ lưu trạng thái cuối cùng mà còn phải ghi lại toàn bộ hành vi thay đổi. Ví dụ, người dùng đã thêm sản phẩm A, sau đó tăng số lượng, rồi lại xóa sản phẩm B trước khi thoát ứng dụng. Việc thiết kế database để lưu trữ các sự kiện thay đổi này giúp bộ phận dữ liệu hiểu được liệu người dùng bỏ giỏ hàng do giá cao, do phí vận chuyển thay đổi hay do họ đang so sánh các mặt hàng với nhau.

### Xác định điểm dừng cuối cùng trong quy trình thanh toán

Một người dùng có thể bỏ giỏ hàng ngay tại trang danh sách sản phẩm, nhưng người khác lại bỏ đi khi đã nhập xong địa chỉ giao hàng hoặc ở bước chọn phương thức thanh toán. Hệ thống cần ghi lại chính xác bước cuối cùng mà người dùng thực hiện trong luồng thanh toán (Checkout Pipeline). Dữ liệu này cực kỳ quan trọng để xác định xem rào cản nằm ở khâu kỹ thuật, khâu nhập liệu quá phức tạp hay do phí giao hành hiển thị ở bước cuối quá cao.

### Hệ thống nhắc nhở tự động qua thông báo đẩy và email

Khi một giỏ hàng được xác định là bị bỏ rơi, hệ thống cần kích hoạt một chuỗi các kịch bản chăm sóc khách hàng. Ví dụ, sau 1 giờ sẽ gửi thông báo nhắc nhở, sau 24 giờ sẽ gửi một mã giảm giá ngắn hạn để khuyến khích hoàn tất đơn hàng. Bài toán này yêu cầu thiết kế hệ thống có khả năng kết nối giữa bảng giỏ hàng, bảng chiến dịch marketing và bảng lịch sử gửi thông báo để đảm bảo không gửi trùng lặp hoặc gửi sai đối tượng.

### Quản lý tồn kho ảo và giữ chỗ sản phẩm trong giỏ hàng

Nhiều hệ thống cho phép giữ chỗ sản phẩm trong một khoảng thời gian ngắn khi người dùng thêm vào giỏ để đảm bảo họ chắc chắn mua được hàng. Tuy nhiên, nếu người dùng bỏ giỏ hàng mà sản phẩm vẫn bị khóa thì sẽ gây thiệt hại cho doanh nghiệp. Bạn cần thiết kế cơ chế để hệ thống tự động giải phóng số lượng tồn kho này khi giỏ hàng quá hạn, giúp sản phẩm hiển thị trở lại cho những khách hàng khác có nhu cầu thực sự.

### Phân tích tỷ lệ bỏ rơi giỏ hàng theo từng danh mục sản phẩm

Doanh nghiệp muốn biết nhóm hàng nào thường xuyên bị bỏ rơi nhất để điều chỉnh chính sách giá hoặc khuyến mãi. Ví dụ, đồ điện tử có tỷ lệ bỏ rơi cao hơn quần áo do người dùng cần nhiều thời gian suy nghĩ hơn. Bài toán này đòi hỏi thiết kế báo cáo tổng hợp dữ liệu từ nhiều bảng bao gồm thông tin sản phẩm, danh mục và trạng thái giỏ hàng để tính toán ra tỷ lệ phần trăm cụ thể cho từng nhóm ngành hàng trong các khoảng thời gian khác nhau.

### Khôi phục giỏ hàng trên nhiều thiết bị khác nhau

Người dùng có thể thêm sản phẩm vào giỏ hàng bằng ứng dụng điện thoại khi đang di chuyển nhưng lại muốn thanh toán bằng máy tính khi về nhà. Nếu hệ thống không đồng bộ được giỏ hàng theo tài khoản định danh, người dùng sẽ thấy giỏ hàng trống rỗng trên máy tính và dễ dàng từ bỏ ý định mua hàng. Đây là bài toán về thiết kế API và Database sao cho dữ liệu giỏ hàng được gắn chặt với mã định danh người dùng thay vì chỉ lưu trữ cục bộ trên trình duyệt hoặc thiết bị.

### Đánh giá hiệu quả của các chương trình khuyến mãi khôi phục giỏ hàng

Sau khi gửi mã giảm giá để kéo người dùng quay lại thanh toán giỏ hàng cũ, hệ thống cần đo lường xem có bao nhiêu phần trăm đơn hàng được hoàn tất nhờ vào mã đó. Bạn cần thiết kế sự liên kết giữa mã khuyến mãi được cá nhân hóa, giỏ hàng đã từng bị bỏ rơi và đơn hàng cuối cùng. Điều này giúp hệ thống báo cáo phân biệt được đâu là đơn hàng tự nhiên và đâu là đơn hàng có được nhờ nỗ lực tiếp thị lại.
