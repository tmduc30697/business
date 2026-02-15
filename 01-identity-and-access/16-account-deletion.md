# Account deletion

### Xử lý xóa mềm và khôi phục tài khoản trong thời gian chờ

Trong thực tế, các ứng dụng thường không xóa vĩnh viễn dữ liệu ngay lập tức mà áp dụng cơ chế xóa mềm. Khi người dùng xác nhận xóa, trạng thái tài khoản chuyển sang chờ xóa và bị khóa đăng nhập. Hệ thống cần một cơ chế để lưu trữ mốc thời gian yêu cầu và tự động tính toán thời hạn 30 ngày để người dùng có thể đổi ý. Bài toán này yêu cầu thiết kế bảng sao cho các truy vấn tìm kiếm thông thường không hiện ra người dùng đã xóa, đồng thời vẫn cho phép quy trình khôi phục diễn ra vẹn toàn dữ liệu nếu người dùng đăng nhập lại trong thời gian quy định.

### Ràng buộc dữ liệu và làm sạch quan hệ trong cơ sở dữ liệu

Một tài khoản thường liên kết với rất nhiều bảng khác như đơn hàng, bình luận, địa chỉ và lịch sử giao dịch. Khi xóa tài khoản, bạn phải quyết định số phận của các dữ liệu liên quan này để tránh lỗi vi phạm ràng buộc khóa ngoại. Bài toán đặt ra là thiết kế một quy trình dọn dẹp dữ liệu theo tầng, xác định những thông tin nào sẽ bị xóa hoàn toàn, thông tin nào cần được ẩn danh và thông tin nào phải giữ nguyên để đảm bảo tính toàn vẹn của các báo cáo tài chính hoặc thống kê hệ thống.

### Xóa dữ liệu phân tán thông qua Message Broker

Trong kiến trúc Microservices, thông tin người dùng có thể được lưu trữ phân tán ở nhiều dịch vụ khác nhau như dịch vụ khuyến mãi, dịch vụ thanh toán và dịch vụ vận chuyển. Khi dịch vụ định danh nhận yêu cầu xóa tài khoản, nó cần thông báo cho toàn bộ các dịch vụ còn lại để cùng thực hiện xóa dữ liệu tương ứng. Bài toán này tập trung vào việc thiết kế luồng sự kiện không đồng bộ, đảm bảo rằng ngay cả khi một dịch vụ đang ngoại tuyến thì lệnh xóa vẫn sẽ được thực thi đầy đủ khi dịch vụ đó hoạt động trở lại.

### Lưu trữ dữ liệu lịch sử phục vụ mục đích pháp lý và kiểm toán

Ngay cả khi người dùng yêu cầu xóa tài khoản, các quy định về pháp lý và kế toán thường bắt buộc doanh nghiệp phải lưu giữ các chứng từ giao dịch hoặc thông tin định danh trong một khoảng thời gian nhất định (ví dụ 5 năm). Bài toán yêu cầu thiết kế một hệ thống lưu trữ tách biệt dành cho dữ liệu lưu trữ sau khi xóa. Hệ thống này phải đảm bảo dữ liệu không được sử dụng cho mục đích kinh doanh hay tiếp thị, nhưng vẫn có thể truy xuất nhanh chóng khi có yêu cầu từ cơ quan chức năng hoặc phục vụ việc đối soát tài chính.

### Xử lý tài nguyên tệp tin và phương tiện truyền thông trên Cloud Storage

Người dùng thường tải lên rất nhiều hình ảnh, video hoặc tài liệu cá nhân lên các dịch vụ lưu trữ đám mây. Khi tài khoản bị xóa vĩnh viễn, việc chỉ xóa bản ghi trong cơ sở dữ liệu là chưa đủ mà cần phải dọn dẹp các tệp tin vật lý để tiết kiệm chi phí lưu trữ và bảo mật thông tin. Bài toán này yêu cầu thiết kế một tiến trình chạy ngầm để quét và xóa các tệp tin liên quan trên các dịch vụ như Amazon S3 hoặc Google Cloud Storage, đồng thời xử lý các trường hợp xóa lỗi hoặc tệp tin đang được dùng chung bởi nhiều người dùng khác.

### Quản lý phiên đăng nhập và thu hồi quyền truy cập tức thì

Khi một người dùng nhấn nút xóa tài khoản, hệ thống cần phải vô hiệu hóa ngay lập tức tất cả các phiên đăng nhập hiện có trên các thiết bị khác nhau và thu hồi các mã truy cập (Access Tokens/Refresh Tokens). Bài toán này đòi hỏi thiết kế một cơ chế kiểm tra trạng thái tài khoản với hiệu năng cao, đảm bảo rằng người dùng không thể thực hiện thêm bất kỳ hành động nào khác trên hệ thống ngay sau khi lệnh xóa được ghi nhận, tránh việc lợi dụng kẽ hở để tẩu tán dữ liệu hoặc phá hoại trong lúc chờ xóa.
