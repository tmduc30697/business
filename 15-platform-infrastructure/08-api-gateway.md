# API gateway

### Hệ thống định tuyến yêu cầu linh hoạt dựa trên phiên bản dịch vụ

Trong một hệ thống có nhiều dịch vụ nhỏ như thanh toán, kho hàng và vận chuyển, API Gateway cần đóng vai trò là điểm tiếp nhận duy nhất. Bài toán đặt ra là làm thế nào để Gateway biết được một yêu cầu cụ thể từ khách hàng sẽ phải gửi đến địa chỉ IP và cổng nào của dịch vụ nội bộ. Ngoài ra, khi một dịch vụ nâng cấp lên phiên bản mới, hệ thống phải cho phép cấu hình để điều hướng một phần nhỏ người dùng sang phiên bản mới nhằm thử nghiệm mà không làm gián đoạn toàn bộ hệ thống.

### Xác thực và phân quyền tập trung tại cửa ngõ hệ thống

Thay vì mỗi dịch vụ nhỏ đều phải tự kiểm tra xem người dùng đã đăng nhập chưa hoặc có quyền truy cập hay không, bài toán yêu cầu API Gateway xử lý toàn bộ quá trình này. Gateway phải kiểm tra tính hợp lệ của mã xác thực từ phía khách hàng, sau đó tra cứu thông tin quyền hạn của người dùng để quyết định cho phép yêu cầu đi tiếp hoặc từ chối ngay lập tức. Điều này đòi hỏi một thiết kế lưu trữ thông tin cấu hình quyền hạn sao cho Gateway có thể truy xuất cực nhanh.

### Kiểm soát tần suất truy cập để bảo vệ tài nguyên hệ thống

Để ngăn chặn việc một ứng dụng hoặc người dùng gửi quá nhiều yêu cầu trong một khoảng thời gian ngắn gây tê liệt hệ thống, Gateway cần áp dụng cơ chế giới hạn tốc độ. Bài toán yêu cầu thiết kế cách lưu trữ và đếm số lượng yêu cầu theo từng khóa định danh như địa chỉ IP hoặc mã định danh ứng dụng. Hệ thống phải xử lý được việc cấu hình các mức giới hạn khác nhau cho từng loại tài khoản, ví dụ tài khoản miễn phí được gửi ít yêu cầu hơn tài khoản trả phí.

### Ghi nhật ký và theo dõi luồng yêu cầu xuyên suốt các dịch vụ

Khi một yêu cầu đi qua Gateway và đi sâu vào nhiều dịch vụ bên trong, việc tìm ra nguyên nhân nếu có lỗi xảy ra là rất khó khăn. Gateway cần thực hiện bài toán gắn một mã định danh duy nhất cho mỗi yêu cầu ngay khi nó vừa chạm tới hệ thống. Toàn bộ thông tin về thời gian bắt đầu, thời gian kết thúc, trạng thái thành công hay thất bại và địa chỉ đích của yêu cầu đó phải được ghi lại một cách có cấu trúc để phục vụ việc tra cứu và phân tích hiệu năng sau này.

### Cơ chế ngắt mạch tự động khi dịch vụ phía sau gặp sự cố

Khi một dịch vụ nội bộ phản hồi quá chậm hoặc liên tục xảy ra lỗi, API Gateway không nên tiếp tục gửi thêm yêu cầu đến đó để tránh tình trạng tắc nghẽn dây chuyền. Bài toán yêu cầu thiết kế một cơ chế theo dõi trạng thái sức khỏe của các dịch vụ. Nếu tỷ lệ lỗi vượt quá ngưỡng cho phép, Gateway sẽ tự động ngắt kết nối đến dịch vụ đó và trả về thông báo lỗi tạm thời cho người dùng. Sau một khoảng thời gian, Gateway phải tự thử nghiệm lại để xem dịch vụ đã phục hồi hay chưa.

### Chuyển đổi giao thức và cấu trúc dữ liệu giữa client và server

Khách hàng có thể gửi yêu cầu bằng định dạng dữ liệu hiện đại trên nền web, nhưng một số dịch vụ cũ bên trong hệ thống lại sử dụng giao thức hoặc cấu trúc dữ liệu khác. API Gateway cần thực hiện bài toán tiếp nhận dữ liệu từ khách hàng, sau đó ánh xạ và chuyển đổi chúng sang định dạng mà dịch vụ nội bộ có thể hiểu được. Sau khi nhận kết quả trả về, Gateway lại phải chuyển đổi ngược lại để phản hồi cho khách hàng một cách đồng nhất.

### Quản lý danh sách trắng và danh sách đen các địa chỉ truy cập

Để tăng cường bảo mật, doanh nghiệp cần ngăn chặn các truy cập từ những vùng địa lý không mong muốn hoặc các địa chỉ IP được xác định là có hành vi tấn công. Bài toán yêu cầu Gateway quản lý một danh sách các quy tắc lọc địa chỉ. Hệ thống phải cho phép người quản trị cập nhật danh sách này thường xuyên và Gateway phải thực hiện việc đối soát địa chỉ IP của mỗi yêu cầu đến với danh sách chặn một cách tức thời trước khi thực hiện bất kỳ thao tác nào khác.

### Bộ nhớ đệm phản hồi tại Gateway để tối ưu tốc độ

Với các yêu cầu lấy dữ liệu ít thay đổi nhưng có số lượng truy cập cực lớn, việc gửi yêu cầu vào tận dịch vụ phía sau là không cần thiết. API Gateway cần có khả năng lưu trữ lại kết quả của các yêu cầu trước đó trong một khoảng thời gian ngắn. Khi có yêu cầu tương tự đến, Gateway sẽ trả về kết quả từ bộ nhớ đệm ngay lập tức. Bài toán này yêu cầu thiết kế cách quản lý thời gian sống của dữ liệu đệm và các quy tắc để biết khi nào cần xóa bỏ dữ liệu cũ để cập nhật dữ liệu mới.
