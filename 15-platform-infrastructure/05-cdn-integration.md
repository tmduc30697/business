# CDN integration

### Quản lý phiên bản và thu hồi bộ nhớ đệm tức thì

Khi quản trị viên cập nhật một hình ảnh sản phẩm hoặc một file CSS mới lên server gốc, người dùng ở khắp nơi trên thế giới vẫn có thể nhìn thấy phiên bản cũ do CDN đã lưu bản sao đó trong một khoảng thời gian dài. Bài toán đặt ra là thiết kế một cơ chế để khi có sự thay đổi tại server gốc, hệ thống phải tự động gửi tín hiệu yêu cầu CDN xóa bỏ bản cũ hoặc đánh dấu bản cũ đã hết hạn trên tất cả các cụm máy chủ toàn cầu. Điều này giúp đảm bảo tính nhất quán của dữ liệu hiển thị mà không cần chờ đợi thời gian hết hạn mặc định của cache.

### Bảo mật tài nguyên bằng đường dẫn có thời hạn

Đối với các nội dung trả phí như khóa học video hoặc tài liệu nội bộ, hệ thống không thể cung cấp một đường dẫn tĩnh công khai vì bất kỳ ai có link cũng có thể truy cập. Hệ thống cần một cơ chế tạo ra các đường dẫn tạm thời chứa các tham số mã hóa về thời gian hết hạn và địa chỉ IP được phép truy cập. Khi người dùng yêu cầu file từ CDN, máy chủ CDN sẽ kiểm tra chữ ký số trong đường dẫn đó để quyết định cho phép tải file hay từ chối, giúp ngăn chặn việc chia sẻ link trái phép.

### Tối ưu hóa dung lượng ảnh tự động theo thiết bị người dùng

Hệ thống lưu trữ ảnh gốc có độ phân giải rất cao, nhưng khi phân phối qua CDN, tùy vào việc người dùng truy cập bằng điện thoại hay máy tính mà hệ thống cần trả về kích thước khác nhau. Bài toán yêu cầu thiết kế một hệ thống xử lý ảnh trung gian hoặc tận dụng tính năng của CDN để tự động nén ảnh, chuyển đổi định dạng từ JPG sang WebP và thay đổi kích thước ảnh ngay trên đường truyền dựa vào các tham số truyền lên từ API, giúp giảm tối đa băng thông và tăng tốc độ hiển thị.

### Xử lý tải lên tệp tin dung lượng lớn qua CDN

Khi người dùng tải lên các video nặng vài GB, việc gửi trực tiếp về server gốc thường gây nghẽn mạch và dễ thất bại nếu đường truyền không ổn định. Hệ thống cần tích hợp cơ chế cho phép người dùng tải lên các phân đoạn nhỏ của tệp tin tới điểm kết nối gần nhất của CDN. Sau khi tất cả các phân đoạn được tải lên thành công, CDN hoặc một dịch vụ xử lý sẽ thực hiện việc ghép nối và chuyển dữ liệu cuối cùng về kho lưu trữ trung tâm, giúp cải thiện trải nghiệm người dùng và giảm tải cho server ứng dụng.

### Phân tích số liệu và báo cáo lưu lượng truy cập toàn cầu

Để quản lý chi phí và hiểu hành vi người dùng, doanh nghiệp cần biết rõ dung lượng băng thông đã tiêu thụ tại từng khu vực địa lý, tỉ lệ các yêu cầu được lấy từ cache so với tỉ lệ phải quay về server gốc để lấy dữ liệu. Bài toán này yêu cầu thiết kế hệ thống thu thập và xử lý các bản ghi nhật ký khổng lồ từ CDN gửi về, sau đó tổng hợp vào cơ sở dữ liệu để vẽ biểu đồ báo cáo theo thời gian thực, phục vụ cho việc tối ưu hóa cấu hình cache và dự báo ngân sách.

### Chiến lược dự phòng khi CDN gặp sự cố

Mặc dù CDN rất ổn định nhưng vẫn có lúc các cụm máy chủ này gặp sự cố diện rộng, khiến toàn bộ ảnh và video trên website không thể hiển thị. Hệ thống cần được thiết kế với cơ chế phát hiện sự cố tự động. Nếu CDN không phản hồi hoặc trả về lỗi trong một khoảng thời gian nhất định, mã nguồn phía máy khách hoặc phía server phải có khả năng tự động chuyển hướng các yêu cầu lấy tài nguyên trực tiếp từ server gốc hoặc từ một nhà cung cấp CDN dự phòng khác để đảm bảo dịch vụ không bị gián đoạn.

### Quản lý quyền truy cập tệp tin theo khu vực địa lý

Vì lý do bản quyền hoặc pháp lý, một số video hoặc nội dung chỉ được phép hiển thị tại một số quốc gia nhất định và phải bị chặn ở các vùng lãnh thổ khác. Bài toán đặt ra là thiết kế cấu hình và API quản lý danh sách trắng hoặc danh sách đen các quốc gia cho từng tệp tin cụ thể. Khi CDN nhận được yêu cầu, nó phải kiểm tra vị trí địa lý của người dùng dựa trên địa chỉ IP và đối chiếu với quy tắc đã thiết lập để quyết định trả về nội dung hay thông báo lỗi truy cập bị từ chối.

### Đồng bộ hóa danh mục tệp tin giữa server gốc và CDN

Trong các hệ thống lớn, danh sách các tệp tin tĩnh (ảnh sản phẩm, video quảng cáo) có thể lên tới hàng triệu bản ghi trong cơ sở dữ liệu. Bài toán yêu cầu thiết kế một hệ thống quản lý trạng thái tệp tin, ghi nhận tệp tin nào đã được đẩy lên CDN thành công, tệp tin nào đang chờ xử lý và tệp tin nào đã bị xóa. Việc thiết kế database và API ở đây phải đảm bảo rằng thông tin về đường dẫn CDN luôn được cập nhật chính xác và đồng bộ với vòng đời của dữ liệu thực tế trong hệ thống quản trị nội dung.
