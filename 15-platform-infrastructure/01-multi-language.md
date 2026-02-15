# Multi-language

### Quản lý nội dung sản phẩm đa ngôn ngữ trong thương mại điện tử

Một sàn thương mại điện tử hoạt động tại nhiều quốc gia yêu cầu mỗi sản phẩm phải có tên, mô tả và thuộc tính hiển thị theo ngôn ngữ của người dùng. Bài toán đặt ra là làm thế nào để thiết kế bảng dữ liệu sao cho khi thêm một ngôn ngữ mới, chúng ta không phải thay đổi cấu trúc bảng hay thêm cột mới. Hệ thống cần truy vấn nhanh chóng thông tin sản phẩm theo mã ngôn ngữ cụ thể và phải có cơ chế hiển thị ngôn ngữ mặc định nếu nội dung của ngôn ngữ yêu cầu chưa được biên dịch.

### Hệ thống quản lý bản dịch tập trung bằng Translation Keys

Thay vì lưu trực tiếp văn bản vào code, các ứng dụng hiện đại sử dụng các mã định danh duy nhất để đại diện cho một câu hoặc một từ trên giao diện. Bài toán yêu cầu thiết kế một hệ thống quản lý các mã này sao cho lập trình viên chỉ cần gọi mã, còn biên dịch viên có thể cập nhật nội dung dịch thông qua một giao diện quản lý mà không cần can thiệp vào mã nguồn. Hệ thống phải xử lý được việc phân nhóm các mã theo từng trang hoặc từng module để tối ưu hóa việc tải dữ liệu lên trình duyệt của người dùng.

### Cá nhân hóa thông báo và email tự động theo ngôn ngữ người dùng

Khi hệ thống gửi các email xác nhận đơn hàng hoặc thông báo đẩy cho người dùng, nội dung phải khớp với ngôn ngữ mà người dùng đó đã lựa chọn trong phần cài đặt tài khoản. Thách thức ở đây là thiết kế các mẫu email có chứa các biến động như tên khách hàng, số tiền, ngày tháng nhưng phần khung văn bản vẫn phải được dịch chính xác. Bạn cần thiết kế logic để hệ thống tự động xác định ngôn ngữ ưu tiên của người dùng tại thời điểm gửi tin nhắn dựa trên dữ liệu profile.

### Xử lý định dạng tiền tệ và số học theo vùng lãnh thổ

Đa ngôn ngữ thường đi kèm với đa khu vực, dẫn đến việc hiển thị số tiền và ngày tháng khác nhau. Ví dụ, cùng một số tiền nhưng ở Mỹ dùng dấu phẩy để phân cách hàng nghìn, còn ở một số nước châu Âu lại dùng dấu chấm. Bài toán yêu cầu thiết kế hệ thống sao cho các API không chỉ trả về giá trị số thuần túy mà còn phải cung cấp thông tin về định dạng hoặc đơn vị tiền tệ tương ứng với quốc gia đó. Database cần lưu trữ thông tin về tỷ giá và quy tắc định dạng của từng khu vực để hiển thị nhất quán trên giao diện.

### Quản lý phiên bản và quy trình phê duyệt bản dịch

Trong một hệ thống lớn, nội dung dịch thuật thường xuyên được cập nhật bởi nhiều biên dịch viên khác nhau. Bài toán đặt ra là thiết kế một cơ chế lưu trữ lịch sử thay đổi của các bản dịch để có thể khôi phục lại phiên bản cũ nếu có sai sót. Ngoài ra, hệ thống cần một quy trình phê duyệt trạng thái: một nội dung mới dịch chỉ được hiển thị cho người dùng sau khi đã được người quản lý kiểm duyệt. Điều này ảnh hưởng trực tiếp đến việc thiết kế các trường trạng thái và quan hệ giữa các bảng trong cơ sở dữ liệu.

### Tối ưu hóa hiệu năng truy vấn dữ liệu đa ngôn ngữ ở quy mô lớn

Khi ứng dụng có hàng triệu sản phẩm và hỗ trợ hàng chục ngôn ngữ, việc thực hiện các phép nối bảng (join) giữa bảng chính và bảng dịch thuật cho mỗi yêu cầu từ người dùng sẽ gây áp lực cực lớn cho cơ sở dữ liệu. Bài toán này yêu cầu bạn suy nghĩ về các giải pháp như sử dụng bộ nhớ đệm (caching) cho các bản dịch, hoặc kỹ thuật lưu trữ dữ liệu dịch dưới dạng tài liệu phi cấu trúc ngay trong bảng chính để tăng tốc độ đọc dữ liệu mà vẫn đảm bảo tính linh hoạt khi mở rộng ngôn ngữ.

### Hệ thống quản lý danh mục và phân loại đa cấp đa ngôn ngữ

Các danh mục sản phẩm hoặc bài viết thường có cấu trúc cây cha con phức tạp. Khi người dùng chuyển đổi ngôn ngữ, toàn bộ cây danh mục này phải hiển thị tên tương ứng nhưng vẫn phải giữ nguyên quan hệ logic và thứ tự sắp xếp. Bạn cần thiết kế database sao cho cấu trúc phân cấp chỉ được định nghĩa một lần, trong khi nhãn hiển thị của từng nút trong cây có thể tồn tại ở nhiều ngôn ngữ khác nhau mà không làm phá vỡ tính toàn vẹn của dữ liệu quan hệ.

### Tự động phát hiện và gợi ý ngôn ngữ dựa trên vị trí và trình duyệt

Để tối ưu trải nghiệm khách hàng mới, hệ thống cần có khả năng tự động xác định ngôn ngữ phù hợp nhất để hiển thị ngay lần đầu truy cập. Bài toán yêu cầu thiết kế một dịch vụ trung gian có khả năng đọc các thông tin từ tiêu đề yêu cầu của trình duyệt hoặc tra cứu địa chỉ mạng của người dùng để ánh xạ sang ngôn ngữ tương ứng trong hệ thống. Thiết kế hệ thống này cần tính đến việc ưu tiên ngôn ngữ nào nếu có sự xung đột giữa vị trí địa lý và cài đặt ngôn ngữ của trình duyệt.
