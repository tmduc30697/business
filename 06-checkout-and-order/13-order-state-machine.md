# Order state machine

### Quản lý đơn hàng thương mại điện tử đa hình thức thanh toán

Bài toán này tập trung vào việc xử lý sự khác biệt giữa thanh toán khi nhận hàng và thanh toán trực tuyến. Với thanh toán trực tuyến, đơn hàng cần trạng thái chờ thanh toán và tự động hủy nếu quá hạn. Với thanh toán khi nhận hàng, luồng đi thẳng từ xác nhận sang chờ lấy hàng. Bạn cần thiết kế bảng đơn hàng sao cho lưu trữ được lịch sử chuyển trạng thái và các điều kiện kích hoạt việc chuyển đổi tương ứng với từng phương thức thanh toán khác nhau.

### Hệ thống đặt đồ ăn trực tuyến với sự tham gia của ba bên

Đây là kịch bản phức tạp nơi trạng thái đơn hàng phụ thuộc vào sự tương tác giữa khách hàng, nhà hàng và tài xế. Trạng thái đơn hàng không chỉ đơn thuần là đang giao mà phải chi tiết hơn như nhà hàng đã nhận đơn, nhà hàng đang chuẩn bị, tài xế đã lấy hàng. Bài toán yêu cầu bạn thiết kế hệ thống sao cho khi một bên cập nhật trạng thái thì thông báo được gửi đến các bên còn lại theo thời gian thực và đảm bảo tính nhất quán của dữ liệu.

### Quy trình đổi trả và hoàn tiền tích hợp

Thay vì chỉ dừng lại ở trạng thái hoàn thành, bài toán này mở rộng sang giai đoạn hậu mãi. Khách hàng có thể yêu cầu trả hàng sau khi đã nhận hàng thành công. Trạng thái đơn hàng lúc này sẽ rẽ nhánh sang chờ kiểm tra hàng trả, đã nhận hàng trả và cuối cùng là đã hoàn tiền. Bạn cần xử lý việc cập nhật lại kho hàng và số dư ví của khách hàng sao cho khớp với các bước chuyển đổi trạng thái này để tránh thất thoát tài chính.

### Đơn hàng đặt trước và quản lý tồn kho giữ chỗ

Trong các sự kiện mở bán sản phẩm hot hoặc hàng đặt trước, đơn hàng sẽ có trạng thái giữ chỗ trong một khoảng thời gian ngắn. Nếu khách hàng không thanh toán, hệ thống phải tự động chuyển sang trạng thái hủy và giải phóng tồn kho. Thách thức ở đây là thiết kế cơ chế khóa bản ghi hoặc hàng đợi để xử lý hàng nghìn yêu cầu chuyển trạng thái cùng lúc mà không gây ra tình trạng bán quá số lượng thực tế.

### Hệ thống đơn hàng dịch vụ đăng ký theo gói định kỳ

Bài toán này áp dụng cho các dịch vụ như Netflix hoặc phần mềm dạng dịch vụ nơi đơn hàng tự động phát sinh mỗi tháng. Trạng thái đơn hàng sẽ lặp đi lặp lại từ chờ thanh toán sang thành công. Nếu thanh toán thất bại, đơn hàng sẽ rơi vào trạng thái tạm tạm dừng hoặc chờ thử lại. Bạn cần thiết kế logic để quản lý các phiên bản đơn hàng và cách thức hệ thống tự động kích hoạt tiến trình thanh toán dựa trên lịch trình đã định sẵn.

### Quy trình kiểm duyệt đơn hàng rủi ro cao

Đối với các sản phẩm giá trị lớn, đơn hàng không được chuyển sang trạng thái giao hàng ngay sau khi thanh toán mà phải đi qua trạng thái chờ kiểm duyệt thủ công. Nhân viên vận hành sẽ kiểm tra tính hợp lệ của thông tin và chuyển sang trạng thái đã phê duyệt hoặc từ chối. Bài toán này giúp bạn thực hành thiết kế phân quyền trong API và lưu vết người thực hiện mỗi bước chuyển trạng thái để phục vụ mục đích đối soát.

### Đơn hàng giao nhiều lần và tách kiện hàng

Trong thực tế, một đơn hàng lớn có thể được chia thành nhiều kiện hàng nhỏ và mỗi kiện có một vòng đời giao hàng riêng biệt. Một kiện có thể đã giao thành công trong khi kiện khác vẫn đang ở trạng thái lấy hàng. Bạn phải thiết kế cấu trúc database sao cho quan hệ giữa đơn hàng tổng và các kiện hàng con được đồng bộ về trạng thái chung, ví dụ đơn hàng tổng chỉ hoàn thành khi tất cả các kiện con đã hoàn thành.

### Hệ thống đặt chỗ và hủy phòng khách sạn

Vòng đời đơn hàng ở đây gắn liền với thời gian thực tế của dịch vụ. Trạng thái sẽ chuyển từ đã đặt sang đã nhận phòng và cuối cùng là đã trả phòng. Điểm đặc biệt là logic xử lý trạng thái hủy đơn hàng kèm theo phí phạt tùy thuộc vào thời điểm khách hàng thực hiện thao tác hủy so với ngày nhận phòng. Điều này đòi hỏi thiết kế logic tính toán động ngay tại thời điểm chuyển đổi trạng thái đơn hàng.

### Đơn hàng xuất khẩu và thông quan quốc tế

Đây là bài toán về chuỗi cung ứng với rất nhiều trạng thái trung gian như chờ đóng container, đang làm thủ tục hải quan, đã rời cảng và đã nhập kho quốc gia đích. Mỗi bước chuyển trạng thái thường đi kèm với việc đính kèm các chứng từ số. Bạn cần thiết kế hệ thống sao cho mỗi lần chuyển đổi trạng thái đều yêu cầu các điều kiện đầu vào là các tệp tin hoặc mã vận đơn quốc tế tương ứng.

### Hệ thống mua hàng trả góp qua đơn vị tài chính

Trong mô hình này, trạng thái đơn hàng phụ thuộc vào kết quả xét duyệt của một bên thứ ba. Sau khi khách hàng đặt hàng, đơn hàng sẽ ở trạng thái chờ xét duyệt tín dụng. Chỉ khi công ty tài chính chuyển trạng thái sang đã giải ngân thì phía cửa hàng mới chuyển đơn sang trạng thái chuẩn bị hàng. Bài toán này giúp bạn luyện tập cách thiết kế Webhook và tích hợp API với bên thứ ba để cập nhật trạng thái tự động.
