# Autocomplete

### Gợi ý sản phẩm trong thương mại điện tử đa kênh

Bài toán yêu cầu xây dựng hệ thống gợi ý sản phẩm ngay khi người dùng nhập vào ô tìm kiếm trên trang web hoặc ứng dụng di động. Hệ thống không chỉ gợi ý tên sản phẩm mà còn phải hiển thị kèm hình ảnh thu nhỏ, giá bán hiện tại và thương hiệu tương ứng. Thách thức ở đây là việc xử lý dữ liệu từ nhiều ngành hàng khác nhau, đảm bảo các sản phẩm còn hàng được ưu tiên hiển thị lên đầu. Bạn cần thiết kế cơ sở dữ liệu để lưu trữ thông tin sản phẩm sao cho việc truy vấn theo tiền tố diễn ra nhanh chóng và API trả về đầy đủ thông tin để giao diện người dùng hiển thị ngay lập tức.

### Tìm kiếm địa điểm trên ứng dụng bản đồ và giao hàng

Trong bài toán này, người dùng sẽ nhập địa chỉ nhà hoặc tên cửa hàng để đặt hàng. Hệ thống cần gợi ý các địa chỉ chính xác dựa trên tọa độ địa lý và phân cấp hành chính từ quốc gia, tỉnh thành đến quận huyện. Đặc thù của bài toán là dữ liệu địa chỉ rất lớn và có tính cấu trúc phân cấp. Bạn phải thiết kế hệ thống sao cho khi người dùng nhập tên đường, API có thể lọc nhanh các địa điểm lân cận hoặc các địa chỉ phổ biến nhất để giảm thiểu việc nhập liệu thủ công, đồng thời xử lý được các trường hợp viết tắt tên đường thường gặp.

### Hệ thống gợi ý bạn bè và nhóm trong mạng xã hội

Khi người dùng gõ ký tự @ hoặc nhập tên vào thanh tìm kiếm của một mạng xã hội, hệ thống cần hiển thị danh sách bạn bè hoặc các nhóm công khai liên quan. Điểm đặc biệt của bài toán này là tính cá nhân hóa: kết quả gợi ý cho người dùng A phải khác với người dùng B dựa trên danh sách bạn bè chung hoặc mức độ tương tác thường xuyên giữa họ. Việc thiết kế database và API cần chú trọng vào các mối quan hệ thực thể phức tạp để đảm bảo tốc độ phản hồi dưới 100ms trong khi vẫn phải lọc qua hàng triệu người dùng.

### Tra cứu mã chứng khoán và tin tức tài chính

Trên các bảng điện tử hoặc ứng dụng tài chính, khi người dùng nhập mã cổ phiếu hoặc tên công ty, hệ thống phải ngay lập tức hiển thị mã chứng khoán kèm theo tên đầy đủ và sàn giao dịch tương ứng. Dữ liệu này yêu cầu độ chính xác tuyệt đối và cập nhật thời gian thực khi có doanh nghiệp mới niêm yết hoặc đổi mã. Bài toán này giúp bạn thực hành việc thiết kế các bảng danh mục tối ưu cho việc tìm kiếm chính xác và xây dựng các endpoint API phục vụ cho việc truyền tải dữ liệu nhẹ nhàng, ổn định.

### Gợi ý từ khóa phổ biến trên công cụ tìm kiếm video

Tương tự như Youtube, hệ thống cần gợi ý các cụm từ khóa mà nhiều người khác đang tìm kiếm dựa trên những ký tự đầu tiên. Bài toán này tập trung vào việc xử lý dữ liệu lớn từ nhật ký tìm kiếm của người dùng. Bạn cần thiết kế một hệ thống có khả năng thống kê tần suất xuất hiện của các cụm từ theo thời gian, từ đó lưu trữ lại những từ khóa xu hướng vào một bộ nhớ đệm hoặc cơ sở dữ liệu chuyên dụng để phục vụ tính năng autocomplete, giúp người dùng khám phá nội dung mới dễ dàng hơn.

### Tìm kiếm hồ sơ nhân viên trong hệ thống quản trị nội bộ

Trong một doanh nghiệp lớn với hàng chục nghìn nhân sự, việc tìm kiếm đồng nghiệp qua tên, email hoặc mã nhân viên là nhu cầu thiết yếu. Hệ thống autocomplete cần hỗ trợ tìm kiếm đa mục tiêu: người dùng có thể nhập một phần email hoặc một phần tên không dấu mà vẫn ra kết quả đúng. Bài toán yêu cầu bạn thiết kế ERD sao cho quản lý được các phòng ban, chức danh và thông tin liên hệ một cách khoa học, đồng thời thiết kế API hỗ trợ lọc dữ liệu theo nhiều tiêu chí khác nhau một cách linh hoạt.

### Tự động hoàn thiện tên thuốc và biệt dược trong y tế

Hệ thống quản lý nhà thuốc hoặc bệnh viện yêu cầu dược sĩ nhập tên thuốc nhanh chóng để kê đơn. Tên thuốc thường dài, khó nhớ và dễ sai sót nếu nhập thủ công. Bài toán đặt ra là phải gợi ý chính xác tên biệt dược, hàm lượng và đơn vị tính ngay khi gõ vài ký tự đầu. Bạn sẽ cần đối mặt với việc thiết kế database cho danh mục dược phẩm khổng lồ với các thuộc tính đi kèm khắt khe, đồng thời đảm bảo API có khả năng xử lý các lỗi chính tả nhẹ nhàng để vẫn đưa ra được gợi ý phù hợp nhất.

### Gợi ý mã vận đơn và trạng thái đơn hàng cho kho vận

Trong quản lý logistics, nhân viên cần tra cứu nhanh trạng thái đơn hàng bằng cách nhập mã vận đơn. Hệ thống autocomplete sẽ hiển thị các mã vận đơn gần nhất mà nhân viên đó vừa thao tác hoặc các mã đang có sự cố cần xử lý. Bài toán này tập trung vào việc quản lý trạng thái thực thể và lịch sử truy cập. Bạn cần thiết kế hệ thống sao cho dữ liệu về đơn hàng được đồng bộ liên tục và API có thể phản hồi trạng thái sơ bộ của đơn hàng ngay trong danh sách gợi ý để tăng hiệu suất làm việc.
