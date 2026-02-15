# Register account

### Hệ thống thương mại điện tử đa quốc gia

Bài toán yêu cầu xử lý việc đăng ký tài khoản cho người dùng ở nhiều quốc gia khác nhau. Bạn cần lưu trữ thông tin không chỉ là email và mật khẩu mà còn là mã vùng điện thoại, đơn vị tiền tệ mặc định và ngôn ngữ ưu tiên. Hệ thống phải đảm bảo rằng một email chỉ có thể đăng ký một lần trên toàn hệ thống nhưng người dùng có thể có nhiều địa chỉ giao hàng ở các quốc gia khác nhau ngay từ bước thiết lập hồ sơ ban đầu.

### Nền tảng học trực tuyến với phân quyền phức tạp

Người dùng khi đăng ký sẽ phải chọn vai trò là học viên hoặc giảng viên. Tùy vào vai trò được chọn, hệ thống sẽ yêu cầu các trường thông tin khác nhau, ví dụ giảng viên cần tải lên bằng cấp hoặc chứng chỉ hành nghề trong khi học viên chỉ cần thông tin cá nhân cơ bản. Sau khi tạo tài khoản, hệ thống cần gán các quyền hạn truy cập vào kho nội dung khác nhau và tạo các bản ghi tương ứng trong bảng hồ sơ chuyên biệt cho từng vai trò.

### Ứng dụng ví điện tử yêu cầu xác thực định danh

Đây là bài toán tập trung vào tính bảo mật và quy trình xác thực. Khi người dùng cung cấp số điện thoại để đăng ký, hệ thống phải lưu trạng thái tài khoản là chưa xác thực. Sau đó, quy trình yêu cầu tích hợp thêm các bước lưu trữ thông tin định danh cá nhân như số căn cước, ảnh chân dung và liên kết với mã OTP được gửi qua tin nhắn. Bạn cần thiết kế cách lưu trữ các mốc thời gian xác thực và lịch sử thay đổi trạng thái của tài khoản.

### Hệ thống quản lý phần mềm dịch vụ cho doanh nghiệp

Trong mô hình này, một người dùng đăng ký không chỉ tạo ra tài khoản cá nhân mà còn tạo ra một thực thể doanh nghiệp mới. Hệ thống cần thiết kế để người đăng ký đầu tiên trở thành quản trị viên cấp cao nhất của tổ chức đó. Cấu trúc dữ liệu phải thể hiện được mối quan hệ giữa người dùng, vai trò của họ trong tổ chức và các gói dịch vụ mà tổ chức đó đã đăng ký sử dụng ngay tại thời điểm khởi tạo.

### Mạng xã hội hình ảnh với tính năng mời tham gia

Người dùng chỉ có thể đăng ký tài khoản nếu họ có mã mời từ một người dùng hiện tại. Bài toán yêu cầu bạn thiết kế cách lưu trữ mối quan hệ giới thiệu này để phục vụ việc truy vết nguồn gốc người dùng. Ngoài các thông tin cơ bản, hệ thống cần lưu trữ thông tin về thiết bị đăng ký để ngăn chặn việc tạo tài khoản ảo hàng loạt và tự động gán các kết nối bạn bè ban đầu dựa trên người đã gửi lời mời.

### Hệ thống đặt chỗ y tế và hồ sơ bệnh án điện tử

Khi bệnh nhân đăng ký tài khoản, hệ thống không chỉ tạo user record mà còn phải tự động khởi tạo một mã số hồ sơ y tế duy nhất. Thông tin đăng ký bao gồm cả nhóm máu, tiền sử dị ứng và thông tin người thân liên hệ khẩn cấp. Thiết kế database ở đây cần chú trọng vào việc tách biệt thông tin đăng nhập và thông tin y tế nhạy cảm để đảm bảo tính riêng tư và tuân thủ các quy định về bảo mật dữ liệu y tế.

### Sàn giao dịch tiền điện tử với bảo mật nhiều lớp

Bài toán này đòi hỏi thiết kế hệ thống đăng ký tích hợp sẵn các tùy chọn bảo mật như xác thực hai yếu tố ngay từ đầu. Ngoài email và mật khẩu, hệ thống cần lưu trữ cấu hình bảo mật của người dùng, danh sách các địa chỉ IP tin cậy và lịch sử đăng ký thiết bị. Bạn cần tính toán cách thiết kế bảng để lưu trữ các khóa bí mật được mã hóa và trạng thái kích hoạt của các phương thức bảo mật khác nhau.

### Hệ thống quản lý thư viện số cho trường học

Quá trình đăng ký tài khoản sẽ liên kết trực tiếp với mã số sinh viên hoặc mã số nhân viên đã tồn tại trong cơ sở dữ liệu nội bộ của nhà trường. Nếu thông tin cung cấp không khớp với dữ liệu nhân sự có sẵn, hệ thống sẽ từ chối tạo tài khoản. Sau khi đăng ký thành công, hệ thống tự động gán hạn mức mượn sách và thời hạn sử dụng tài khoản dựa trên niên khóa của sinh viên hoặc hợp đồng của giảng viên.

### Ứng dụng giao đồ ăn với tài khoản đa năng

Hệ thống cho phép một người dùng có thể đăng ký với tư cách là khách hàng, tài xế hoặc chủ cửa hàng. Mỗi loại tài khoản lại có những bảng dữ liệu mở rộng khác nhau nhưng dùng chung một bảng định danh chính để đăng nhập. Bài toán này giúp bạn thực hành thiết kế cấu trúc kế thừa trong cơ sở dữ liệu và cách quản lý các luồng logic đăng ký khác nhau trên cùng một nền tảng API.

### Nền tảng phát trực tuyến video theo gói thuê bao

Người dùng đăng ký tài khoản đồng thời với việc chọn một gói dịch vụ trả phí hoặc dùng thử. Hệ thống cần lưu trữ thông tin thẻ thanh toán hoặc liên kết ví điện tử ngay lúc đăng ký. Bạn cần thiết kế database sao cho có thể quản lý được ngày bắt đầu, ngày hết hạn dùng thử và trạng thái thanh toán của tài khoản để hệ thống có thể tự động khóa hoặc mở quyền truy cập nội dung tương ứng.
