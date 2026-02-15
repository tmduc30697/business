# Product publish/unpublish

### Quản lý hiển thị sản phẩm theo biến thể và kho hàng

Trong thực tế, một sản phẩm thường có nhiều phiên bản như kích cỡ hoặc màu sắc khác nhau. Bài toán đặt ra là khi tất cả các biến thể của một sản phẩm đều hết hàng trong kho, hệ thống cần tự động chuyển trạng thái sản phẩm sang chưa xuất bản để tránh khách hàng đặt nhầm. Ngược lại, khi có ít nhất một biến thể được nhập thêm hàng, sản phẩm phải tự động hiển thị trở lại. Bạn cần thiết kế cơ chế đồng bộ giữa dữ liệu kho hàng và trạng thái hiển thị để đảm bảo tính nhất quán dữ liệu theo thời gian thực.

### Lên lịch xuất bản sản phẩm cho chiến dịch khuyến mãi

Các nhãn hàng thường chuẩn bị bộ sưu tập mới hoặc các sản phẩm giảm giá sốc trước hàng tuần nhưng chỉ muốn chúng xuất hiện đúng vào khung giờ vàng như nửa đêm ngày lễ. Bài toán yêu cầu hệ thống cho phép người dùng thiết lập thời gian bắt đầu hiển thị và thời gian tự động ẩn sản phẩm. Điều này đòi hỏi một cơ chế xử lý các tác vụ nền hoặc hàng đợi công việc để quét và cập nhật trạng thái hàng loạt sản phẩm mà không làm nghẽn hệ thống hay gây trễ so với thời gian thực tế đã cài đặt.

### Quy trình phê duyệt nội dung trước khi xuất bản

Đối với các sàn thương mại điện tử có nhiều nhà bán hàng tham gia, việc một sản phẩm được bật trạng thái xuất bản không có nghĩa là nó sẽ hiện lên trang chủ ngay lập tức. Sản phẩm cần trải qua một quy trình kiểm duyệt nội dung bởi đội ngũ quản trị sàn để đảm bảo không vi phạm chính sách. Bạn cần giải quyết bài toán về các trạng thái trung gian như chờ duyệt, bị từ chối, hoặc yêu cầu chỉnh sửa, đồng thời lưu trữ lịch sử thay đổi để biết ai là người đã phê duyệt hoặc từ chối sản phẩm đó.

### Quản lý hiển thị đa kênh và đa nền tảng

Một sản phẩm có thể được quản lý tập trung nhưng lại được xuất bản lên nhiều kênh bán hàng khác nhau như ứng dụng di động, trang web, hoặc các nền tảng mạng xã hội tích hợp. Bài toán thực tế là sản phẩm có thể được hiển thị ở kênh này nhưng lại bị ẩn ở kênh kia do chính sách kinh doanh hoặc giới hạn về mặt địa lý. Bạn cần thiết kế cấu trúc dữ liệu sao cho việc bật tắt trạng thái có thể tùy biến linh hoạt theo từng kênh bán hàng riêng biệt thay vì chỉ dùng một biến trạng thái duy nhất cho toàn bộ hệ thống.

### Xử lý bộ nhớ đệm khi thay đổi trạng thái sản phẩm

Khi một sản phẩm được bật hoặc tắt hiển thị, thông tin này cần được cập nhật ngay lập tức trên giao diện người dùng để đảm bảo trải nghiệm mua sắm. Tuy nhiên, các hệ thống lớn thường sử dụng bộ nhớ đệm như Redis để tăng tốc độ truy xuất. Bài toán đặt ra là làm thế nào để xóa hoặc cập nhật bộ nhớ đệm một cách hiệu quả ngay khi trạng thái sản phẩm thay đổi, tránh tình trạng khách hàng vẫn nhìn thấy sản phẩm và bấm vào mua nhưng hệ thống phía sau lại báo sản phẩm không tồn tại.

### Kiểm soát hiển thị sản phẩm theo nhóm khách hàng đặc biệt

Nhiều doanh nghiệp muốn triển khai các chương trình bán hàng nội bộ hoặc dành riêng cho khách hàng thân thiết. Bài toán yêu cầu sản phẩm chỉ được xuất bản và hiển thị đối với một nhóm người dùng nhất định đã đăng nhập và thỏa mãn các điều kiện về hạng thành viên. Đối với người dùng vãng lai hoặc không đủ điều kiện, sản phẩm sẽ được coi như ở trạng thái chưa xuất bản. Việc này đòi hỏi sự kết hợp chặt chẽ giữa logic hiển thị sản phẩm và hệ thống phân quyền người dùng khi thiết kế API.

### Đồng bộ trạng thái sản phẩm với các dịch vụ tìm kiếm

Khi sản phẩm bị chuyển sang trạng thái chưa xuất bản, nó không chỉ biến mất khỏi danh mục hàng hóa mà còn phải bị loại bỏ khỏi kết quả tìm kiếm trên trang web. Bài toán thực tế là làm thế nào để đồng bộ hóa trạng thái này với các công cụ tìm kiếm bên thứ ba như Elasticsearch hay Algolia. Nếu việc đồng bộ không tốt, khách hàng vẫn có thể tìm thấy sản phẩm qua thanh tìm kiếm nhưng khi nhấn vào trang chi tiết lại gặp lỗi, gây ra trải nghiệm người dùng không tốt.

### Quản lý phiên bản nội dung khi tái xuất bản sản phẩm

Khi một sản phẩm cũ đã bị ẩn đi một thời gian và người bán muốn xuất bản lại với thông tin hình ảnh hoặc mô tả mới, hệ thống cần có khả năng lưu giữ các phiên bản cũ để đối soát hoặc báo cáo. Bài toán yêu cầu thiết kế hệ thống sao cho việc thay đổi nội dung và thay đổi trạng thái hiển thị được tách biệt, cho phép người bán chuẩn bị nội dung mới ở trạng thái bản nháp trong khi phiên bản cũ vẫn đang hiển thị hoặc đang bị ẩn, sau đó mới thực hiện việc ghi đè và xuất bản chính thức.
