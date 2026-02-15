# Loyalty program

### Quản lý ví điểm đa năng và lịch sử giao dịch

Bài toán yêu cầu hệ thống phải quản lý được số dư điểm của khách hàng từ nhiều nguồn khác nhau như mua hàng, quà tặng từ quản trị viên hoặc điểm thưởng sinh nhật. Mỗi khi khách hàng phát sinh giao dịch, hệ thống cần ghi lại biến động số dư bao gồm loại giao dịch, số điểm thay đổi và tham chiếu đến hóa đơn tương ứng. Thử thách ở đây là đảm bảo tính toàn vẹn dữ liệu khi có hàng nghìn giao dịch xảy ra đồng thời và khả năng truy xuất lịch sử điểm nhanh chóng để khách hàng kiểm tra trên ứng dụng di động.

### Cơ chế xếp hạng thành viên và thăng hạng tự động

Hệ thống cần phân loại khách hàng vào các hạng thẻ như Đồng, Bạc, Vàng, Kim cương dựa trên tổng chi tiêu hoặc số điểm tích lũy trong một khoảng thời gian nhất định. Khi một khách hàng đạt đủ điều kiện, hệ thống phải tự động cập nhật hạng mới và ghi lại thời điểm thay đổi. Ngoài ra, bài toán còn bao gồm việc xét tụt hạng nếu trong chu kỳ tiếp theo khách hàng không duy trì được mức chi tiêu tối thiểu, đòi hỏi các tiến trình chạy ngầm để kiểm tra điều kiện định kỳ.

### Quản lý kho ưu đãi và đổi voucher điện tử

Khách hàng có thể sử dụng điểm tích lũy để đổi lấy các mã giảm giá hoặc quà tặng vật lý. Hệ thống phải quản lý danh mục phần thưởng, số lượng tồn kho của từng loại voucher và giới hạn số lần đổi của mỗi khách hàng. Khi khách hàng nhấn đổi quà, hệ thống cần kiểm tra số dư điểm, trừ điểm ngay lập tức và tạo ra một mã voucher duy nhất có trạng thái chưa sử dụng. Việc thiết kế cần tính đến trường hợp nhiều người cùng đổi một phần thưởng có số lượng giới hạn tại cùng một thời điểm.

### Tích điểm theo quy tắc linh hoạt và nhóm sản phẩm

Thay vì chỉ tích điểm cố định trên tổng hóa đơn, doanh nghiệp muốn thiết lập các quy tắc phức tạp hơn như nhân đôi điểm vào ngày cuối tuần hoặc chỉ tích điểm cho một số danh mục hàng hóa nhất định. Hệ thống cần cho phép cấu hình các chiến dịch tích điểm có thời hạn, áp dụng cho các cửa hàng cụ thể hoặc các nhóm khách hàng mục tiêu. Điều này đòi hỏi cấu trúc database linh hoạt để lưu trữ các điều kiện áp dụng mà không cần thay đổi code mỗi khi có chiến dịch mới.

### Quản lý hạn sử dụng của từng đợt điểm tích lũy

Để giảm áp lực tài chính, các doanh nghiệp thường quy định điểm thưởng sẽ hết hạn sau một khoảng thời gian kể từ ngày phát sinh. Hệ thống cần theo dõi được từng dòng điểm nạp vào sẽ hết hạn vào ngày nào. Khi khách hàng tiêu dùng điểm, thuật toán phải ưu tiên trừ những dòng điểm sắp hết hạn trước theo nguyên tắc nhập trước xuất trước. Bài toán này rất quan trọng để rèn luyện tư duy thiết kế bảng dữ liệu chi tiết và các logic tính toán số dư khả dụng tại một thời điểm bất kỳ.

### Hệ thống giới thiệu bạn bè và thưởng đa cấp

Doanh nghiệp muốn mở rộng tệp khách hàng bằng cách thưởng điểm cho người giới thiệu khi người được giới thiệu thực hiện đơn hàng đầu tiên thành công. Hệ thống cần lưu vết mối quan hệ giữa người giới thiệu và người được giới thiệu, đồng thời kiểm soát các điều kiện nhận thưởng để tránh gian lận. Việc thiết kế API cho bài toán này cần đảm bảo ghi nhận đúng đối tượng và thực hiện các giao dịch cộng điểm một cách chính xác trong cùng một transaction.

### Tích hợp đa kênh và đồng bộ dữ liệu thời gian thực

Khách hàng có thể mua hàng tại cửa hàng vật lý, trên website hoặc qua ứng dụng di động. Hệ thống Loyalty đóng vai trò là một dịch vụ trung tâm cung cấp API cho tất cả các nền tảng này. Khi một hóa đơn được thanh toán tại quầy POS, thông tin phải được gửi về hệ thống Loyalty để cộng điểm ngay lập tức và gửi thông báo cho khách hàng. Thử thách của bài toán này nằm ở việc thiết kế hệ thống có khả năng chịu tải tốt và cơ chế xử lý lỗi khi kết nối giữa các nền tảng bị gián đoạn.

### Quản lý nhiệm vụ nhận điểm và tương tác người dùng

Để tăng tỷ lệ giữ chân khách hàng, hệ thống đưa ra các nhiệm vụ như đăng nhập hàng ngày, hoàn thành hồ sơ cá nhân hoặc đánh giá sản phẩm để nhận điểm thưởng. Mỗi nhiệm vụ sẽ có trạng thái hoàn thành và số điểm thưởng tương ứng cho từng khách hàng. Bạn cần thiết kế cấu trúc dữ liệu để lưu trữ danh sách nhiệm vụ, theo dõi tiến độ thực hiện của người dùng và đảm bảo mỗi nhiệm vụ chỉ được nhận thưởng đúng số lần quy định.
