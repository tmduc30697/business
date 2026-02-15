# Data encryption

### Lưu trữ mật khẩu người dùng và cơ chế xác thực an toàn

Khi người dùng đăng ký tài khoản, hệ thống không được phép lưu mật khẩu dưới dạng văn bản thuần túy vào cơ sở dữ liệu để tránh lộ lọt khi bị tấn công chiếm quyền điều khiển server. Bài toán yêu cầu bạn thiết kế quy trình băm mật khẩu kết hợp với một chuỗi ký tự ngẫu nhiên cho từng người dùng riêng biệt. Ngoài ra, bạn cần thiết kế API đăng nhập sao cho việc kiểm tra mật khẩu diễn ra an toàn mà không cần giải mã dữ liệu cũ, đồng thời đảm bảo rằng ngay cả quản trị viên hệ thống cũng không thể biết mật khẩu thật của khách hàng.

### Bảo mật thông tin thẻ thanh toán theo tiêu chuẩn tài chính

Một ứng dụng thương mại điện tử cần lưu trữ thông tin thẻ tín dụng của khách hàng để phục vụ tính năng thanh toán một chạm cho lần mua hàng sau. Theo quy định, các thông tin như số thẻ và mã bảo mật phải được mã hóa ngay khi vừa rời khỏi trình duyệt của người dùng và lưu trữ dưới dạng mã hóa trong cơ sở dữ liệu. Bạn cần thiết kế hệ thống quản lý khóa mã hóa tách biệt hoàn toàn với máy chủ ứng dụng, sao cho nếu cơ sở dữ liệu bị lấy cắp, kẻ tấn công cũng không thể giải mã được số thẻ nếu không có khóa từ dịch vụ quản lý khóa riêng.

### Mã hóa hồ sơ y tế điện tử và quyền truy cập của bác sĩ

Trong hệ thống quản lý bệnh viện, thông tin bệnh lý và kết quả xét nghiệm của bệnh nhân là dữ liệu cực kỳ nhạy cảm. Bài toán đặt ra là dữ liệu phải được mã hóa ở mức độ từng bản ghi trong cơ sở dữ liệu. Chỉ những bác sĩ được phân quyền điều trị cho bệnh nhân đó mới có thể giải mã và xem nội dung chi tiết. Bạn cần thiết kế một mô hình dữ liệu sao cho các trường thông tin cá nhân bị ẩn đi đối với nhân viên hành chính nhưng lại hiển thị đầy đủ đối với nhân viên y tế có thẩm quyền thông qua một cơ chế cấp phát khóa giải mã tạm thời.

### Truyền tải dữ liệu nhạy cảm giữa các Microservices nội bộ

Trong một hệ thống lớn chia thành nhiều dịch vụ nhỏ, dữ liệu người dùng thường xuyên được luân chuyển giữa dịch vụ đặt hàng, dịch vụ vận chuyển và dịch vụ thông báo. Ngay cả khi các dịch vụ này nằm trong mạng nội bộ, nguy cơ bị nghe lén vẫn tồn tại. Bài toán yêu cầu thiết kế cơ chế truyền tải dữ liệu sử dụng giao thức bảo mật để đảm bảo dữ liệu được mã hóa trên đường đi. Bạn cần thiết kế cách thức các dịch vụ tự xác thực lẫn nhau thông qua chứng chỉ số để đảm bảo dữ liệu không bị gửi nhầm đến một dịch vụ giả mạo trong cùng mạng lưới.

### Quản lý khóa mã hóa và cơ chế xoay vòng khóa tự động

Khi hệ thống sử dụng một khóa duy nhất để mã hóa toàn bộ dữ liệu người dùng trong nhiều năm, rủi ro sẽ rất lớn nếu khóa đó bị lộ. Bài toán thực tế là thiết kế một hệ thống quản lý khóa có khả năng tự động tạo ra khóa mới định kỳ và thực hiện việc mã hóa lại các dữ liệu cũ bằng khóa mới mà không gây gián đoạn dịch vụ. Bạn cần thiết kế cấu trúc database sao cho mỗi bản ghi dữ liệu mã hóa đều đi kèm với một định danh của khóa được sử dụng, giúp hệ thống biết chính xác cần dùng khóa nào để giải mã trong tương lai.

### Tìm kiếm trên dữ liệu đã được mã hóa trong cơ sở dữ liệu

Đây là một bài toán khó trong thiết kế hệ thống vì khi dữ liệu đã được mã hóa, các câu lệnh tìm kiếm thông thường của cơ sở dữ liệu sẽ không còn tác dụng. Ví dụ, bạn cần tìm kiếm khách hàng theo số điện thoại nhưng số điện thoại đó đã được mã hóa thành một chuỗi ký tự không có ý nghĩa. Bạn phải thiết kế một giải pháp lưu trữ sao cho hệ thống vừa đảm bảo dữ liệu được bảo vệ an toàn, vừa cho phép thực hiện các truy vấn tìm kiếm chính xác hoặc tìm kiếm theo vùng một cách hiệu quả mà không cần giải mã toàn bộ bảng dữ liệu.

### Lưu trữ và chia sẻ tài liệu minh chứng định danh khách hàng

Các ứng dụng ngân hàng số yêu cầu người dùng tải lên ảnh chụp chứng minh nhân dân hoặc hộ chiếu để định danh. Những tệp tin hình ảnh này cần được mã hóa trước khi lưu trữ vào các dịch vụ lưu trữ đám mây. Bài toán yêu cầu bạn thiết kế quy trình: ứng dụng client mã hóa file, đẩy file lên server, server lưu trữ và khi cần hiển thị lại cho nhân viên kiểm duyệt, hệ thống phải thực hiện giải mã và tạo ra một đường dẫn truy cập tạm thời có thời hạn ngắn để đảm bảo ảnh không bị rò rỉ ra bên ngoài.

### Bảo mật tin nhắn trò chuyện giữa hai người dùng đầu cuối

Trong một ứng dụng nhắn tin, người dùng kỳ vọng rằng ngay cả nhà cung cấp dịch vụ cũng không thể đọc được nội dung tin nhắn của họ. Bạn cần thiết kế hệ thống mã hóa đầu cuối, nơi mà quá trình mã hóa diễn ra ngay tại điện thoại của người gửi và chỉ được giải mã tại điện thoại của người nhận. Bài toán này đòi hỏi bạn thiết kế API và Database để lưu trữ các khóa công khai của người dùng, xử lý việc đồng bộ tin nhắn khi người dùng thay đổi thiết bị và đảm bảo tính toàn vẹn của nội dung tin nhắn không bị thay đổi trong quá trình truyền tải.
