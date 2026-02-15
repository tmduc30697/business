# Verified purchase badge

### Quản lý vòng đời đơn hàng và quyền đánh giá

Bài toán này tập trung vào việc xác định điều kiện cần và đủ để một tài khoản được phép để lại đánh giá có gắn nhãn xác nhận. Bạn cần xử lý logic sao cho nhãn chỉ xuất hiện khi đơn hàng đã chuyển sang trạng thái thành công và người dùng không thực hiện yêu cầu trả hàng hoặc hoàn tiền. Việc thiết kế cần đảm bảo tính nhất quán giữa bảng lưu trữ đơn hàng và bảng đánh giá để tránh tình trạng nhãn hiển thị sai lệch khi trạng thái đơn hàng thay đổi sau đó.

### Hệ thống ngăn chặn đánh giá ảo và spam nhãn xác thực

Vấn đề nằm ở việc các nhà bán hàng có thể tự tạo đơn hàng ảo hoặc cấu kết với người mua để lấy nhãn xác thực nhằm tăng uy tín giả tạo. Bài toán yêu cầu thiết kế cơ chế kiểm soát dựa trên tần suất mua hàng, địa chỉ IP, và phương thức thanh toán. Bạn sẽ phải tính toán cách lưu trữ các siêu dữ liệu của thiết bị và lịch sử giao dịch để phát hiện các hành vi bất thường trước khi hệ thống tự động gán nhãn cho một đánh giá mới.

### Tích hợp đánh giá từ nhiều nguồn cung cấp khác nhau

Trong mô hình kinh doanh đa kênh, một sản phẩm có thể được bán qua website chính thức, ứng dụng di động hoặc các đối tác phân phối bên thứ ba. Bài toán đặt ra là làm thế nào để đồng bộ dữ liệu mua hàng từ nhiều nguồn khác nhau về một hệ thống trung tâm để xác thực nhãn. Bạn cần thiết kế cấu trúc dữ liệu linh hoạt để nhận diện định danh người dùng từ các nền tảng khác nhau nhưng vẫn đảm bảo tính chính xác của nhãn xác thực trên trang chi tiết sản phẩm.

### Xử lý cập nhật nhãn khi có biến động về giao dịch

Đây là bài toán về tính nhất quán dữ liệu theo thời gian thực. Một người dùng có thể viết đánh giá ngay khi nhận hàng, nhưng vài ngày sau họ thực hiện khiếu nại và hoàn trả sản phẩm. Hệ thống cần có cơ chế tự động thu hồi hoặc ẩn nhãn xác thực khi giao dịch mua hàng không còn hiệu lực. Việc thiết kế các trigger hoặc các dịch vụ lắng nghe sự kiện từ hệ thống thanh toán và kho vận là yếu tố then chốt ở đây.

### Phân quyền và kiểm soát nội dung đánh giá của quản trị viên

Bài toán yêu cầu thiết kế hệ thống quản trị cho phép nhân viên vận hành kiểm tra lại các đánh giá bị báo cáo vi phạm. Hệ thống cần lưu trữ lịch sử thay đổi nhãn xác thực nếu có sự can thiệp thủ công từ con người. Bạn sẽ cần thiết kế các bảng lưu vết thao tác và cơ chế phê duyệt nhiều cấp để đảm bảo rằng nhãn xác thực không bị gán sai mục đích bởi nhân viên nội bộ hoặc bị thay đổi trái phép.

### Tối ưu hóa hiệu suất truy vấn nhãn xác thực cho trang sản phẩm

Khi một sản phẩm có hàng chục nghìn lượt đánh giá, việc lọc và hiển thị danh sách các bài viết có nhãn xác thực lên đầu trang sẽ gây áp lực lớn cho cơ sở dữ liệu. Bài toán yêu cầu bạn thiết kế cấu trúc bảng và các lớp đệm dữ liệu sao cho việc phân trang, sắp xếp theo độ ưu tiên của nhãn xác thực diễn ra nhanh chóng. Bạn phải cân nhắc giữa việc chuẩn hóa dữ liệu để tiết kiệm bộ nhớ và phi chuẩn hóa dữ liệu để tăng tốc độ đọc.

### Thống kê và báo cáo độ tin cậy của nhà bán hàng

Dựa trên tỉ lệ các đánh giá có nhãn xác thực so với tổng số đánh giá, hệ thống cần tính toán điểm uy tín cho từng nhà bán hàng hoặc từng dòng sản phẩm. Bài toán này đòi hỏi thiết kế các bảng tổng hợp dữ liệu và các tiến trình chạy ngầm để cập nhật chỉ số định kỳ. Dữ liệu này không chỉ dùng để hiển thị cho người mua mà còn dùng để hệ thống xếp hạng tìm kiếm ưu tiên các sản phẩm có chất lượng thực tế tốt hơn.

### Quản lý hình ảnh và video đi kèm đánh giá xác thực

Người dùng thường tin tưởng hơn vào các đánh giá có nhãn xác thực kèm theo hình ảnh thực tế của sản phẩm. Bài toán đặt ra là quản lý lưu trữ và phân phối tệp tin đa phương tiện gắn liền với từng mã đánh giá đã xác thực. Bạn cần thiết kế cách thức liên kết giữa các tệp tin trên máy chủ lưu trữ với bản ghi trong cơ sở dữ liệu, đồng thời xử lý các kịch bản như người dùng xóa ảnh hoặc cập nhật nội dung sau khi đã đăng bài.
