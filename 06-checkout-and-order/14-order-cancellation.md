# Order cancellation

### Quản lý trạng thái đơn hàng và điều kiện hủy theo luồng vận hành

Bài toán này tập trung vào việc xác định thời điểm nào người dùng được phép tự hủy trên ứng dụng và khi nào nút hủy phải bị khóa lại. Bạn cần thiết kế một hệ thống máy trạng thái để kiểm soát việc hủy đơn dựa trên tiến độ thực tế như chờ xác nhận, đang lấy hàng, hoặc đã giao cho đơn vị vận chuyển. Thách thức ở đây là đảm bảo tính đồng nhất dữ liệu khi trạng thái đơn hàng thay đổi liên tục bởi cả người mua, người bán và shipper.

### Xử lý hoàn tiền tự động cho các phương thức thanh toán trả trước

Khi một đơn hàng đã được thanh toán qua thẻ tín dụng hoặc ví điện tử bị hủy, hệ thống cần thực hiện quy trình hoàn tiền tương ứng. Bài toán yêu cầu thiết kế logic tích hợp với các cổng thanh toán bên thứ ba để lệnh hoàn tiền được kích hoạt ngay khi đơn hàng chuyển sang trạng thái đã hủy. Bạn phải tính đến các trường hợp giao dịch bị lỗi giữa chừng, việc đối soát số tiền hoàn và lưu vết lịch sử giao dịch để tránh hoàn tiền nhầm hoặc hoàn nhiều lần.

### Khôi phục số lượng tồn kho và giữ chỗ sản phẩm

Khi khách hàng đặt hàng, số lượng tồn kho thường bị trừ đi hoặc chuyển vào trạng thái giữ chỗ để đảm bảo không bị bán chồng chéo. Khi đơn hàng bị hủy, hệ thống phải thực hiện cộng lại số lượng này vào kho hàng khả dụng một cách chính xác. Bài toán trở nên phức tạp hơn trong các sự kiện khuyến mãi lớn, nơi hàng nghìn đơn hàng bị hủy cùng lúc và yêu cầu cập nhật tồn kho phải diễn ra gần như ngay lập tức để người dùng khác có thể mua.

### Hệ thống quản lý lý do hủy và phân tích hành vi người dùng

Thay vì chỉ cho phép hủy, doanh nghiệp cần thu thập dữ liệu về lý do hủy hàng để cải thiện dịch vụ. Bài toán yêu cầu thiết kế cấu trúc dữ liệu cho phép lưu trữ các nhóm lý do khác nhau như đổi ý, tìm thấy giá rẻ hơn, hoặc thời gian giao hàng quá lâu. Dữ liệu này sau đó được sử dụng để phân loại và báo cáo, giúp bộ phận kinh doanh hiểu được điểm yếu trong quy trình bán hàng hoặc phát hiện các mẫu hành vi bất thường từ phía khách hàng.

### Ràng buộc hủy đơn đối với các gói combo và sản phẩm khuyến mãi

Trong thực tế, một đơn hàng có thể chứa các sản phẩm đi kèm quà tặng hoặc nằm trong một chương trình giảm giá theo gói. Bài toán đặt ra yêu cầu thiết kế logic hủy toàn bộ đơn hàng sao cho các ràng buộc về khuyến mãi được giải trừ hoàn toàn. Nếu đơn hàng bị hủy, các mã giảm giá đã sử dụng phải được khôi phục lại cho người dùng, đồng thời các điều kiện áp dụng cho quà tặng đi kèm cũng phải bị hủy bỏ để tránh thất thoát tài sản của cửa hàng.

### Phí hủy đơn và chính sách bồi thường cho người bán

Đối với các sàn thương mại điện tử, việc khách hàng hủy đơn quá muộn có thể gây thiệt hại về chi phí đóng gói hoặc vận chuyển cho người bán. Bài toán yêu cầu thiết kế một cơ chế tính phí hủy đơn dựa trên thời gian thực hiện lệnh hủy. Bạn cần xử lý việc trích xuất một phần tiền từ đơn hàng đã thanh toán để đền bù cho người bán hoặc đơn vị vận chuyển, đồng thời lưu trữ các quy tắc về phí này trong cơ sở dữ liệu để có thể thay đổi linh hoạt theo từng ngành hàng.

### Xử lý tranh chấp và phê duyệt hủy đơn từ phía quản trị viên

Không phải mọi yêu cầu hủy đơn đều được thực hiện tự động. Trong một số trường hợp đơn hàng có giá trị cao hoặc đã đi vào giai đoạn sản xuất riêng biệt, yêu cầu hủy cần phải qua bước phê duyệt của nhân viên chăm sóc khách hàng. Bài toán này tập trung vào việc thiết kế quy trình làm việc giữa người dùng và quản trị viên, bao gồm việc gửi yêu cầu, đính kèm minh chứng nếu cần, và luồng thông báo phản hồi kết quả phê duyệt cho người mua.

### Đồng bộ dữ liệu hủy đơn giữa hệ thống nội bộ và đơn vị vận chuyển thứ ba

Khi một đơn hàng đã được đẩy sang hệ thống của bên vận chuyển nhưng khách hàng nhấn nút hủy, hệ thống của bạn phải gửi một tín hiệu thu hồi đơn hàng đến đối tác ngay lập tức. Bài toán yêu cầu thiết kế kiến trúc kết nối API để đồng bộ trạng thái giữa hai hệ thống khác nhau. Thách thức là xử lý các tình huống độ trễ mạng hoặc phía vận chuyển từ chối hủy vì shipper đã lấy hàng thành công, dẫn đến việc phải cập nhật lại trạng thái hủy không thành công trên hệ thống nội bộ.
