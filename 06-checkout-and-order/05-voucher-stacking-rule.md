# Voucher stacking rule

### Phân loại Voucher theo cấp độ áp dụng

Trong bài toán này, bạn cần thiết kế một hệ thống phân biệt rõ voucher của sàn thương mại điện tử, voucher của từng cửa hàng riêng lẻ và voucher từ đơn vị vận chuyển. Quy tắc đặt ra là người dùng có thể áp dụng đồng thời một voucher mỗi loại cho cùng một đơn hàng, nhưng không được phép áp dụng hai voucher cùng loại. Điều này đòi hỏi database phải thể hiện được tính phân cấp và ràng buộc để khi tính toán tổng tiền, hệ thống biết voucher nào được trừ vào phần nào của đơn hàng.

### Thứ tự ưu tiên và trình tự tính toán

Khi nhiều loại giảm giá được áp dụng như giảm theo số tiền cố định và giảm theo phần trăm, kết quả cuối cùng sẽ thay đổi tùy vào thứ tự thực hiện. Bài toán yêu cầu bạn thiết kế logic để hệ thống luôn ưu tiên trừ các voucher giảm tiền mặt trước, sau đó mới tính phần trăm giảm giá dựa trên số dư còn lại, hoặc ngược lại tùy theo cấu hình của quản trị viên. Việc này ảnh hưởng trực tiếp đến cách bạn thiết kế API trả về thông tin tạm tính của giỏ hàng mỗi khi người dùng tick chọn thêm một voucher mới.

### Loại trừ lẫn nhau giữa các chương trình khuyến mãi

Nhiều doanh nghiệp quy định rằng nếu một sản phẩm đã nằm trong chương trình Flash Sale hoặc đang có giá sốc thì không được phép áp dụng thêm bất kỳ mã giảm giá nào khác. Bạn cần giải quyết bài toán kiểm tra điều kiện của từng sản phẩm trong giỏ hàng để quyết định xem một voucher có hợp lệ hay không. Nếu giỏ hàng có năm sản phẩm nhưng chỉ có hai sản phẩm không thuộc danh mục loại trừ, voucher chỉ được tính toán dựa trên giá trị của hai sản phẩm đó.

### Giới hạn giá trị giảm tối đa cho Voucher phần trăm

Một voucher giảm giá năm mươi phần trăm thường đi kèm với điều kiện số tiền giảm không vượt quá một ngưỡng nhất định, ví dụ tối đa là năm mươi ngàn đồng. Bài toán này yêu cầu database phải lưu trữ được các tham số chặn trên và logic xử lý khi tính toán số tiền thực tế được giảm. Khi người dùng nhập mã, hệ thống phải so sánh giữa giá trị phần trăm tính được và giá trị tối đa cho phép để lấy con số nhỏ hơn, đảm bảo không gây thất thoát cho người bán.

### Quy tắc cộng dồn dựa trên hạng thành viên

Hệ thống cần phân lớp người dùng thành các hạng như đồng, bạc, vàng, kim cương để áp dụng quy tắc stacking khác nhau. Ví dụ, thành viên hạng bạc chỉ được dùng tối đa hai mã giảm giá, trong khi thành viên hạng kim cương có thể áp dụng không giới hạn số lượng mã từ các nguồn khác nhau. Đây là bài toán kết hợp giữa quản lý thông tin khách hàng và cấu hình tham số khuyến mãi linh hoạt, buộc bạn phải thiết kế các bảng trung gian để lưu trữ quyền lợi tương ứng với từng cấp độ.

### Voucher đi kèm điều kiện thanh toán cụ thể

Một số mã giảm giá chỉ có hiệu lực khi người dùng chọn một phương thức thanh toán nhất định như ví điện tử hoặc thẻ tín dụng của một ngân hàng cụ thể. Bài toán đặt ra là khi người dùng thay đổi phương thức thanh toán ở bước thanh toán cuối cùng, hệ thống phải tự động kiểm tra lại toàn bộ danh sách voucher đã áp dụng. Nếu phương thức thanh toán mới không thỏa mãn, hệ thống phải gỡ bỏ voucher đó và cập nhật lại tổng số tiền đơn hàng ngay lập tức.

### Quản lý ngân sách và giới hạn lượt sử dụng đồng thời

Mỗi voucher thường có một ngân sách tổng hoặc số lượng lượt sử dụng tối đa cho toàn chiến dịch. Thách thức lớn nhất ở đây là xử lý concurrency khi hàng ngàn người dùng cùng áp dụng mã tại cùng một thời điểm. Bạn cần thiết kế hệ thống sao cho việc giữ chỗ voucher xảy ra khi người dùng đang thanh toán nhưng chưa hoàn tất, và phải hoàn trả lại số lượt sử dụng nếu đơn hàng bị hủy hoặc thanh toán không thành công.

### Voucher dành riêng cho sản phẩm mua kèm

Đây là bài toán về combo khuyến mãi, trong đó voucher chỉ được kích hoạt khi người dùng mua sản phẩm chính đi kèm với một sản phẩm phụ cụ thể. Quy tắc stacking ở đây trở nên phức tạp vì phải xác định xem sản phẩm nào là sản phẩm mồi và sản phẩm nào được hưởng lợi từ voucher. Nếu người dùng xóa sản phẩm chính ra khỏi giỏ hàng, hệ thống phải tự động vô hiệu hóa toàn bộ chuỗi voucher liên quan đến sản phẩm phụ đó.
