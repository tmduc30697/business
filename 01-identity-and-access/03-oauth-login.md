# OAuth login

### Quản lý liên kết đa tài khoản xã hội

Người dùng thường có nhu cầu kết nối cùng một tài khoản nội bộ với nhiều nhà cung cấp khác nhau như Google, Facebook và GitHub. Bài toán yêu cầu hệ thống phải lưu trữ thông tin định danh riêng biệt từ các provider nhưng vẫn trỏ về một thực thể người dùng duy nhất. Bạn cần xử lý trường hợp khi người dùng đăng nhập bằng Google lần đầu, sau đó lại muốn dùng Facebook để vào chính tài khoản đó mà không tạo ra tài khoản mới trùng lặp.

### Xử lý đồng bộ hóa thông tin profile và ảnh đại diện

Khi người dùng thay đổi tên hiển thị hoặc ảnh đại diện trên Google, hệ thống của bạn có thể cần cập nhật những thông tin này để đảm bảo tính đồng nhất. Bài toán đặt ra là làm sao để lưu trữ URL ảnh từ bên thứ ba, quyết định khi nào nên tải ảnh về server nội bộ và khi nào chỉ dẫn link, đồng thời quản lý các metadata mà provider trả về trong object profile để hiển thị lên giao diện người dùng.

### Cơ chế hợp nhất tài khoản khi trùng email

Một tình huống phổ biến là người dùng đã đăng ký bằng email và mật khẩu truyền thống, sau đó họ nhấn chọn đăng nhập bằng Google cũng với email đó. Hệ thống cần một quy trình xác thực để đảm bảo người đang giữ tài khoản Google thực sự là chủ sở hữu của tài khoản email nội bộ. Điều này đòi hỏi thiết kế các trạng thái xác thực tài khoản và logic để gộp (merge) thông tin mà không làm mất dữ liệu lịch sử của người dùng.

### Quản lý phạm vi truy cập và thu hồi quyền hạn

Hệ thống không chỉ dùng OAuth để đăng nhập mà còn muốn xin quyền truy cập vào các tài nguyên khác như danh sách bạn bè hoặc lịch làm việc. Bạn cần thiết kế cách lưu trữ các chuỗi scope khác nhau cho từng provider. Quan trọng hơn, bài toán yêu cầu xử lý logic khi người dùng ngắt kết nối với Facebook từ phía trang quản trị của Facebook, làm sao để hệ thống nội bộ nhận biết và vô hiệu hóa các token tương ứng.

### Hệ thống Refresh Token và duy trì phiên đăng nhập

Mỗi Access Token từ provider thường có thời hạn rất ngắn. Để người dùng không phải đăng nhập lại liên tục, hệ thống cần quản lý Refresh Token một cách an toàn. Bài toán này tập trung vào việc thiết kế bảng lưu trữ token với thời gian hết hạn, cơ chế tự động gọi API của provider để lấy Access Token mới ở dưới nền và đảm bảo rằng phiên đăng nhập nội bộ (session/JWT) vẫn được duy trì mượt mà.

### Lưu trữ log lịch sử đăng nhập và thiết bị

Để tăng cường bảo mật, hệ thống cần ghi lại mọi hoạt động đăng nhập thông qua bên thứ ba. Dữ liệu cần thể hiện rõ người dùng đã vào hệ thống từ provider nào, vào thời gian nào, sử dụng trình duyệt hay thiết bị gì. Bài toán này giúp bạn thiết kế các bảng audit log và cung cấp dữ liệu cho tính năng hiển thị danh sách các thiết bị đang đăng nhập để người dùng có thể thực hiện đăng xuất từ xa.

### Tích hợp đăng nhập cho hệ thống đa ứng dụng

Giả sử công ty bạn có nhiều ứng dụng khác nhau như web bán hàng, ứng dụng di động và trang quản trị nhưng chỉ muốn dùng một hệ thống OAuth tập trung. Bạn cần thiết kế mô hình Centralized Authentication nơi các ứng dụng con nhận ủy quyền từ một server trung tâm sau khi server đó xác thực xong với Google. Bài toán này đòi hỏi việc quản lý các Client ID và Redirect URL cho từng ứng dụng con một cách linh hoạt.

### Xử lý logic đăng ký bổ sung thông tin sau OAuth

Nhiều trường hợp Google không cung cấp đủ thông tin bạn cần, ví dụ như số điện thoại hoặc địa chỉ giao hàng. Sau khi nhận được token thành công từ bên thứ ba, hệ thống cần đưa người dùng vào một trạng thái đăng ký dở dang (onboarding). Bạn phải thiết kế luồng dữ liệu sao cho người dùng buộc phải hoàn thiện các thông tin bắt buộc này trước khi chính thức được cấp quyền truy cập đầy đủ vào các tính năng của hệ thống.
