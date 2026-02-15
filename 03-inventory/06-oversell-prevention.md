# Oversell prevention

### Hệ thống Flash Sale cho sản phẩm công nghệ theo khung giờ

Trong các sự kiện khuyến mãi lớn, một số sản phẩm hot như điện thoại đời mới sẽ được bán với giá cực sốc trong một khung giờ nhất định. Số lượng sản phẩm có hạn nhưng số lượng người dùng truy cập vào trang chi tiết và nhấn nút mua tại cùng một thời điểm có thể lên tới hàng chục nghìn người. Thách thức ở đây là hệ thống phải trừ tồn kho ngay khi người dùng đặt hàng thành công và lập tức thông báo hết hàng cho những người đến sau, tránh tình trạng hàng đã hết nhưng nút mua vẫn còn hiển thị hoặc cho phép thanh toán.

### Đặt vé xem phim và chọn ghế ngồi trực tuyến

Khi người dùng chọn một ghế cụ thể trong rạp chiếu phim, hệ thống cần tạm giữ ghế đó trong một khoảng thời gian ngắn để người dùng thực hiện thanh toán. Trong thời gian này, những người dùng khác xem cùng một suất chiếu không được phép chọn đúng vị trí ghế đó. Nếu quá trình thanh toán thất bại hoặc quá thời gian quy định, ghế phải được giải phóng ngay lập tức để người khác có thể đặt. Bài toán này yêu cầu sự chính xác tuyệt đối về vị trí và trạng thái của từng đơn vị sản phẩm nhỏ nhất.

### Hệ thống đặt chỗ khách sạn trên nhiều nền tảng đại lý

Một khách sạn thường phân phối phòng của mình qua nhiều kênh khác nhau như website chính thức và các trang đại lý du lịch trực tuyến. Khi một phòng cuối cùng được đặt trên một đại lý, thông tin tồn kho phải được cập nhật đồng bộ lên tất cả các kênh khác trong thời gian thực. Nếu không có cơ chế kiểm soát chặt chẽ, hai khách hàng khác nhau có thể đặt cùng một căn phòng thông qua hai nền tảng khác nhau tại cùng một thời điểm, dẫn đến việc khách sạn không có đủ phòng phục vụ khi khách đến nhận.

### Bán vé xe khách liên tỉnh với lộ trình nhiều chặng

Khác với vé xem phim, một chiếc ghế trên xe khách có thể được bán nhiều lần cho các chặng đường khác nhau nếu chúng không chồng lấn lên nhau. Ví dụ, một khách có thể đặt ghế số 5 cho chặng từ điểm đầu đến điểm giữa, và một khách khác có thể đặt chính ghế số 5 đó cho chặng từ điểm giữa đến điểm cuối. Hệ thống cần kiểm tra sự tồn tại của ghế dựa trên toàn bộ lộ trình di chuyển của xe để đảm bảo tại mỗi phân đoạn của chuyến đi, số lượng khách không bao giờ vượt quá số ghế thực tế trên xe.

### Quản lý tồn kho cho mô hình thực phẩm tươi sống giao nhanh

Trong mô hình đi chợ hộ, số lượng tồn kho của các mặt hàng thực phẩm tươi sống như rau củ hoặc thịt thường thay đổi rất nhanh và đôi khi có sự sai lệch giữa kho vật lý và kho trên hệ thống. Khi khách hàng thêm hàng vào giỏ và tiến hành thanh toán, hệ thống phải thực hiện kiểm tra tồn kho cuối cùng tại kho hàng gần nhất với vị trí của khách. Nếu số lượng trong kho không đủ đáp ứng ngay tại thời điểm đó, hệ thống cần phải điều chỉnh đơn hàng hoặc gợi ý sản phẩm thay thế ngay trước khi khách hoàn tất giao dịch.

### Phân phối mã giảm giá giới hạn số lượng cho chiến dịch marketing

Các chiến dịch marketing thường tung ra các mã giảm giá có giá trị cao nhưng giới hạn số lượng sử dụng cho toàn sàn. Khác với sản phẩm vật lý, mã giảm giá có tốc độ áp dụng cực nhanh ở bước kiểm tra cuối cùng của giỏ hàng. Bài toán đặt ra là làm sao để khi hàng triệu người dùng cùng nhấn áp dụng mã, hệ thống chỉ cho phép đúng số lượng người dùng quy định được hưởng ưu đãi, trong khi vẫn đảm bảo hiệu năng của toàn bộ luồng thanh toán không bị chậm lại.

### Đặt trước các phiên bản giới hạn của trò chơi điện tử

Khi một trò chơi sắp ra mắt, nhà phát hành thường mở bán các bản đặc biệt với số lượng sản phẩm được đánh số thứ tự. Người dùng thường có xu hướng giữ hàng trong giỏ nhưng chưa thanh toán ngay. Hệ thống cần một cơ chế để phân biệt giữa tồn kho thực tế, tồn kho đang bị tạm giữ trong giỏ hàng, và tồn kho đã bán. Việc thiết kế cần đảm bảo rằng những người thực sự có ý định mua và thanh toán nhanh sẽ có quyền ưu tiên hơn những người chỉ giữ hàng trong giỏ rồi bỏ quên.

### Hệ thống đăng ký tín chỉ cho sinh viên đại học

Mỗi lớp học phần trong trường đại học đều có giới hạn sĩ số tối đa để đảm bảo chất lượng giảng dạy. Tại thời điểm cổng đăng ký mở ra, hàng nghìn sinh viên sẽ cùng truy cập để chọn các lớp có giảng viên tốt hoặc khung giờ đẹp. Nếu hệ thống không kiểm soát tốt việc ghi nhận số lượng đăng ký theo thời gian thực, một lớp học có thể bị vượt quá sĩ số cho phép, gây khó khăn cho việc sắp xếp phòng học và quản lý của nhà trường sau này.
