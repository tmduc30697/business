# Localization

### Quản lý kho nội dung đa ngôn ngữ cho sản phẩm thương mại điện tử

Một sàn thương mại điện tử hoạt động tại nhiều quốc gia cần hiển thị tên sản phẩm, mô tả và thông số kỹ thuật theo ngôn ngữ bản địa của người dùng. Bài toán đặt ra là làm thế nào để thiết kế cơ sở dữ liệu có thể lưu trữ linh hoạt hàng chục ngôn ngữ khác nhau cho cùng một sản phẩm mà không làm phình to bảng dữ liệu chính. Hệ thống cần cơ chế dự phòng để nếu một sản phẩm chưa có bản dịch tiếng Việt thì sẽ tự động hiển thị tiếng Anh mặc định thay vì để trống thông tin.

### Hiển thị giá cả và xử lý làm tròn theo đơn vị tiền tệ địa phương

Mỗi quốc gia có đơn vị tiền tệ và quy tắc hiển thị số thập phân khác nhau. Ví dụ, tiền Đô la Mỹ thường có hai chữ số thập phân sau dấu phẩy, trong khi tiền Việt Nam Đồng thường là số nguyên và không dùng phần thập phân. Hệ thống cần một bảng danh mục tiền tệ để lưu trữ tỷ giá hối đoái, ký hiệu tiền tệ và vị trí đặt ký hiệu đó. Ngoài ra, việc lưu trữ giá gốc trong database và tính toán giá hiển thị theo thời gian thực dựa trên vị trí người dùng là một bài toán quan trọng về hiệu năng và độ chính xác.

### Đồng bộ hóa múi giờ trong hệ thống đặt lịch hẹn toàn cầu

Một ứng dụng đặt lịch họp trực tuyến cho phép người dùng ở London đặt lịch với chuyên gia ở Tokyo. Bài toán yêu cầu hệ thống phải lưu trữ thời gian dưới dạng chuẩn quốc tế trong database nhưng phải hiển thị chính xác theo múi giờ địa phương của từng người dùng khi họ xem lịch. Thử thách lớn hơn là xử lý các khu vực có áp dụng giờ mùa hè (Daylight Saving Time), nơi mà chênh lệch múi giờ có thể thay đổi tùy theo thời điểm trong năm, ảnh hưởng trực tiếp đến việc kiểm tra xem chuyên gia có đang rảnh hay không.

### Bản địa hóa định dạng địa chỉ và thông tin vận chuyển

Cấu trúc địa chỉ giao hàng không hề giống nhau giữa các quốc gia. Ở Việt Nam thường theo cấp Hành chính gồm Tỉnh, Quận, Phường; trong khi ở Mỹ lại yêu cầu Bang và Mã bưu chính (Zip Code) bắt buộc. Thiết kế database và API cần phải linh hoạt để thay đổi các trường nhập liệu và quy tắc kiểm tra dữ liệu tùy thuộc vào quốc gia mà người dùng chọn. Nếu thiết kế cứng nhắc theo một mẫu duy nhất, người dùng ở quốc gia khác sẽ không thể hoàn tất quá trình thanh toán vì thiếu hoặc thừa thông tin địa chỉ.

### Thay đổi nội dung banner và hình ảnh theo chiến dịch văn hóa

Bản địa hóa không chỉ là dịch chữ mà còn là thay đổi hình ảnh để phù hợp với văn hóa. Một ứng dụng xem phim có thể hiển thị banner cổ động Tết Nguyên Đán cho người dùng ở Việt Nam và Trung Quốc, nhưng cùng lúc đó lại hiển thị banner chủ đề mùa đông cho người dùng ở Châu Âu. Bài toán này yêu cầu hệ thống quản lý nội dung (CMS) phải có khả năng phân phối tài sản số dựa trên metadata về vị trí địa lý và sở thích văn hóa của người dùng thay vì chỉ dựa vào ID của nội dung đó.

### Quản lý quy tắc hiển thị số và đơn vị đo lường theo vùng lãnh thổ

Các quốc gia sử dụng các hệ thống đo lường khác nhau như Metric (mét, kg) hoặc Imperial (inch, pound). Một ứng dụng theo dõi sức khỏe cần hiển thị cân nặng và chiều cao của người dùng theo đơn vị họ quen thuộc nhất. Bên cạnh đó, dấu ngăn cách hàng nghìn và hàng thập phân cũng khác nhau, nơi dùng dấu phẩy, nơi dùng dấu chấm. Hệ thống cần một lớp chuyển đổi dữ liệu trước khi trả về API để đảm bảo trải nghiệm người dùng tự nhiên nhất có thể theo đúng tiêu chuẩn vùng miền.

### Điều hướng ngôn ngữ dựa trên ưu tiên của trình duyệt và cài đặt cá nhân

Khi một người dùng lần đầu truy cập trang web, hệ thống cần có cơ chế thông minh để tự động nhận diện ngôn ngữ phù hợp nhất. Bài toán là thiết kế logic ưu tiên: bắt đầu từ cài đặt thủ công của người dùng trong hồ sơ, nếu không có thì dựa trên cookie, nếu không có cookie thì dựa trên thông tin ngôn ngữ từ trình duyệt, và cuối cùng là dựa trên địa chỉ IP để xác định quốc gia. Việc quản lý các mức độ ưu tiên này trong hệ thống phân quyền và hồ sơ người dùng là rất quan trọng để tránh gây bối rối cho khách hàng.

### Bản địa hóa các tài liệu pháp lý và chính sách bảo mật

Mỗi quốc gia có những quy định pháp luật riêng về thương mại điện tử và bảo mật dữ liệu như GDPR tại Châu Âu. Hệ thống cần lưu trữ và hiển thị các phiên bản điều khoản sử dụng khác nhau cho từng vùng lãnh thổ. Khi các chính sách này cập nhật, hệ thống phải biết chính xác người dùng ở khu vực nào cần phải xác nhận lại điều khoản mới. Điều này đòi hỏi một thiết kế database có tính lịch sử (versioning) và liên kết chặt chẽ với ranh giới địa lý của người dùng.
