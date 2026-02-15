# Product video upload

### Quản lý đa phiên bản và tối ưu hóa độ phân giải video

Khi người dùng tải lên một video gốc có chất lượng cao, hệ thống không thể dùng trực tiếp file đó để hiển thị cho tất cả khách hàng vì sẽ gây lag và tốn băng thông. Bài toán đặt ra là cần lưu trữ và quản lý nhiều phiên bản của cùng một video với các độ phân giải khác nhau như 480p, 720p, và 1080p. Việc thiết kế database phải thể hiện được mối quan hệ giữa sản phẩm, video gốc và các bản thực thi kỹ thuật của video đó để trình phát có thể tự động chọn phiên bản phù hợp với tốc độ mạng của người xem.

### Quy trình xử lý video không đồng bộ và cập nhật trạng thái

Việc xử lý video sau khi tải lên thường mất nhiều thời gian do quá trình kiểm tra định dạng và nén dữ liệu. Hệ thống cần một cơ chế để ghi nhận các trạng thái chuyển đổi của video từ lúc đang tải lên, đang xử lý, cho đến khi thành công hoặc thất bại. Bạn cần thiết kế các bảng lưu trữ hàng đợi công việc và các webhook hoặc cơ chế thông báo để cập nhật lại trạng thái hiển thị trên giao diện quản trị của người bán ngay khi video sẵn sàng.

### Phân quyền và giới hạn tài nguyên lưu trữ theo gói thành viên

Trong các hệ thống thương mại điện tử đa người bán, không phải ai cũng được phép tải lên dung lượng video giống nhau. Bài toán yêu cầu thiết lập các hạn mức về tổng dung lượng lưu trữ, số lượng video tối đa trên mỗi sản phẩm hoặc giới hạn thời lượng video dựa trên cấp độ tài khoản của người dùng. Điều này đòi hỏi thiết kế database phải liên kết chặt chẽ giữa thông tin gói dịch vụ, định danh người dùng và các thông số metadata của từng file video đã tải lên.

### Tối ưu hóa trải nghiệm người dùng với Thumbnail và Preview

Để tăng khả năng chuyển đổi, thay vì chỉ hiện một khung hình đen, hệ thống cần hiển thị ảnh đại diện hấp dẫn hoặc một đoạn video xem thử ngắn khoảng vài giây khi người dùng di chuột qua. Bài toán này yêu cầu quản lý việc trích xuất các khung hình từ video gốc, lưu trữ chúng như các thực thể hình ảnh riêng biệt nhưng vẫn gắn liền với video chủ thể. Cấu trúc dữ liệu cần hỗ trợ việc chọn lựa một ảnh cụ thể làm ảnh bìa mặc định cho video đó.

### Kiểm soát nội dung và phê duyệt video tự động hoặc thủ công

Để đảm bảo an toàn cho sàn thương mại điện tử, các video tải lên cần được kiểm duyệt để loại bỏ nội dung vi phạm pháp luật hoặc không phù hợp. Quy trình này có thể bao gồm việc sử dụng trí tuệ nhân tạo để quét nội dung hoặc chờ nhân viên quản trị phê duyệt thủ công. Hệ thống cần các bảng lưu trữ lịch sử kiểm duyệt, lý do từ chối và các cờ đánh dấu trạng thái hiển thị công khai để đảm bảo video chỉ xuất hiện trên trang sản phẩm sau khi đã vượt qua vòng kiểm soát.

### Phân tích hiệu quả và hành vi người xem video

Người bán cần biết liệu video của họ có thực sự giúp bán được hàng hay không. Bài toán này tập trung vào việc thu thập các chỉ số như số lượt xem, thời gian xem trung bình, và tỷ lệ người dùng nhấn vào nút mua hàng sau khi xem video. Việc thiết kế hệ thống cần tính đến chuyện lưu trữ dữ liệu log theo thời gian thực và cách tổng hợp chúng thành các báo cáo định kỳ mà không làm ảnh hưởng đến hiệu năng của các bảng dữ liệu chính.

### Quản lý vị trí hiển thị và thứ tự ưu tiên trong bộ sưu tập

Một sản phẩm có thể có nhiều hình ảnh và nhiều video giới thiệu ở các góc độ khác nhau. Bài toán đặt ra là làm thế nào để người bán có thể tùy chỉnh thứ tự xuất hiện của video xen kẽ với hình ảnh trong slide trình chiếu sản phẩm. Database cần một cơ chế sắp xếp linh hoạt để khi API trả về dữ liệu, ứng dụng front-end có thể hiển thị đúng danh sách các phương tiện truyền thông theo đúng ý đồ của người bán.

### Lưu trữ phân tán và phân phối qua mạng lưới CDN

Khi hệ thống có quy mô lớn với người dùng ở nhiều vùng địa lý khác nhau, việc lưu trữ video tập trung tại một máy chủ sẽ khiến tốc độ tải trang bị chậm. Bài toán này yêu cầu thiết kế hệ thống lưu trữ có khả năng tích hợp với các dịch vụ lưu trữ đám mây và mạng lưới phân phối nội dung. Bạn cần thiết kế cách lưu trữ đường dẫn URL sao cho có thể linh hoạt thay đổi tên miền phân phối hoặc hỗ trợ việc ký xác thực quyền truy cập vào các file video riêng tư.
