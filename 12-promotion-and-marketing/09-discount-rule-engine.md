# Discount rule engine

### Áp dụng giảm giá dựa trên giá trị tối thiểu của giỏ hàng

Hệ thống cần cho phép người quản lý thiết lập các quy tắc giảm giá dựa trên tổng số tiền mà khách hàng đang có trong giỏ hàng. Ví dụ, khách hàng sẽ được giảm giá mười phần trăm nếu tổng giá trị đơn hàng đạt từ năm trăm nghìn đồng trở lên, hoặc được giảm thẳng một trăm nghìn đồng nếu đơn hàng đạt từ một triệu đồng. Bài toán này yêu cầu database phải lưu trữ được các ngưỡng giá trị và loại hình giảm giá tương ứng để tính toán ngay khi người dùng thay đổi số lượng sản phẩm trong giỏ.

### Giảm giá theo danh mục sản phẩm hoặc thương hiệu cụ thể

Doanh nghiệp muốn chạy chương trình khuyến mãi chỉ dành riêng cho một nhóm hàng hóa nhất định, chẳng hạn như giảm giá hai mươi phần trăm cho tất cả sản phẩm thuộc danh mục đồ điện tử hoặc chỉ áp dụng cho các sản phẩm của một thương hiệu thời trang cụ thể. Hệ thống phải có khả năng bóc tách các sản phẩm trong giỏ hàng, đối chiếu với danh mục được phép khuyến mãi và chỉ tính toán số tiền giảm trên tổng giá trị của những sản phẩm thỏa mãn điều kiện đó thay vì toàn bộ đơn hàng.

### Quy tắc mua nhiều giảm sâu theo số lượng sản phẩm

Để kích thích mua sắm số lượng lớn, hệ thống cần hỗ trợ quy tắc giảm giá theo bậc thang dựa trên số lượng của cùng một loại sản phẩm hoặc tổng số lượng sản phẩm trong một nhóm. Ví dụ, mua từ ba sản phẩm cùng loại thì giảm năm phần trăm, mua từ năm sản phẩm trở lên thì giảm mười phần trăm. Logic xử lý cần phải kiểm tra số lượng thực tế trong giỏ hàng và áp dụng mức chiết khấu cao nhất mà khách hàng đạt được theo cấu hình định sẵn.

### Ưu đãi dành riêng cho vai trò và phân hạng người dùng

Hệ thống cần thực thi các quy tắc giảm giá cá nhân hóa dựa trên dữ liệu thành viên. Ví dụ, những khách hàng có hạng thành viên là Kim Cương sẽ được giảm thêm năm phần trăm trên tổng hóa đơn, hoặc những người dùng mới đăng ký tài khoản trong vòng bảy ngày sẽ nhận được một ưu đãi đặc biệt cho đơn hàng đầu tiên. Bài toán này đòi hỏi sự liên kết chặt chẽ giữa Engine giảm giá và Module quản lý người dùng để kiểm tra điều kiện về vai trò hoặc hành vi người dùng tại thời điểm thanh toán.

### Quy tắc quà tặng đính kèm dựa trên điều kiện đơn hàng

Thay vì giảm tiền trực tiếp, hệ thống cần thực thi quy tắc tặng kèm sản phẩm vật lý hoặc dịch vụ miễn phí. Ví dụ, khi khách hàng mua một chiếc điện thoại, hệ thống tự động thêm một gói bảo hiểm rơi vỡ hoặc một bộ tai nghe với giá không đồng vào đơn hàng. Engine phải xử lý được việc tự động kiểm tra điều kiện, tự động thêm sản phẩm quà tặng vào giỏ và đảm bảo quà tặng này không bị tính tiền nhưng vẫn được quản lý trong kho.

### Loại trừ và ưu tiên giữa các quy tắc giảm giá chồng chéo

Trong thực tế, một đơn hàng có thể thỏa mãn nhiều chương trình khuyến mãi cùng một lúc, ví dụ như vừa thỏa mãn điều kiện giảm giá danh mục, vừa thỏa mãn điều kiện hạng thành viên. Hệ thống cần một cơ chế để định nghĩa quy tắc ưu tiên, chẳng hạn như chỉ chọn mức giảm sâu nhất, hoặc cho phép cộng dồn các loại giảm giá theo một thứ tự nhất định. Việc thiết kế database phải có thêm các trường dữ liệu về độ ưu tiên và cờ cho phép cộng dồn để tránh thất thoát doanh thu.

### Giảm giá theo khung giờ vàng và giới hạn thời gian thực thi

Các chương trình khuyến mãi thường chỉ có hiệu lực trong những khoảng thời gian rất ngắn hoặc vào những khung giờ cố định trong ngày. Hệ thống cần thực thi quy tắc dựa trên thời gian thực khi khách hàng nhấn nút đặt hàng. Nếu khách hàng tạo giỏ hàng lúc chương trình còn hiệu lực nhưng đến khi thanh toán chương trình đã kết thúc, hệ thống phải tự động loại bỏ giảm giá và tính toán lại số tiền thực tế để đảm bảo tính chính xác về mặt tài chính.

### Giới hạn giảm giá tối đa cho các quy tắc phần trăm

Khi áp dụng giảm giá theo tỷ lệ phần trăm, doanh nghiệp thường đặt ra một mức giảm tối đa để kiểm soát chi phí, ví dụ giảm ba mươi phần trăm nhưng tối đa không quá năm mươi nghìn đồng. Engine giảm giá phải có khả năng so sánh giữa số tiền được giảm theo công thức phần trăm và mức trần cho phép, sau đó chọn giá trị nhỏ hơn để áp dụng vào đơn hàng. Đây là một ràng buộc quan trọng cần được lưu trữ trong cấu hình của mỗi quy tắc giảm giá.
