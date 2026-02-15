# Multi-warehouse

### Điều phối đơn hàng thông minh dựa trên vị trí địa lý

Khi một khách hàng đặt hàng trên hệ thống, bài toán đặt ra là làm sao để tự động chọn ra kho hàng tối ưu nhất để xử lý đơn hàng đó. Hệ thống cần tính toán khoảng cách từ địa chỉ nhận hàng của khách đến các kho đang còn hàng trong kho. Việc ưu tiên kho gần nhất không chỉ giúp giảm chi phí vận chuyển mà còn rút ngắn thời gian giao hàng. Bạn sẽ cần xử lý các trường hợp như kho gần nhất hết hàng thì phải nhảy sang kho gần thứ nhì, hoặc một đơn hàng có nhiều sản phẩm mà không kho nào có đủ tất cả, dẫn đến việc phải tách đơn thành nhiều kiện từ các kho khác nhau.

### Quản lý chuyển kho nội bộ và lộ trình hàng hóa

Trong quá trình kinh doanh, chủ cửa hàng thường xuyên phải luân chuyển hàng hóa giữa các kho để cân bằng tồn kho hoặc chuẩn bị cho các chương trình khuyến mãi tại các khu vực cụ thể. Bài toán này yêu cầu quản lý trạng thái của hàng hóa khi rời kho xuất nhưng chưa tới kho nhập. Bạn cần ghi nhận số lượng hàng đang đi đường, người chịu trách nhiệm vận chuyển, thời gian dự kiến tới nơi và các bước xác nhận nhập kho thực tế để tránh thất thoát. Việc thiết kế hệ thống phải đảm bảo tồn kho tổng không thay đổi nhưng tồn kho khả dụng tại từng kho phải được cập nhật chính xác theo thời gian thực.

### Phân vùng quyền hạn nhân viên theo từng kho cụ thể

Một hệ thống lớn với hàng chục kho hàng đòi hỏi sự phân quyền chặt chẽ để bảo mật và tránh sai sót dữ liệu. Bài toán này tập trung vào việc thiết kế cơ chế phân quyền sao cho mỗi nhân viên kho chỉ có thể xem, tạo phiếu nhập xuất hoặc kiểm kê tại kho mà họ được gán quyền. Quản lý cấp cao có thể xem toàn bộ dữ liệu tất cả các kho, trong khi quản lý vùng chỉ xem được cụm kho trong khu vực của mình. Điều này ảnh hưởng trực tiếp đến cách bạn thiết kế các API lấy danh sách sản phẩm hoặc báo cáo, đảm bảo dữ liệu trả về luôn được lọc theo phạm vi quyền hạn của người dùng.

### Kiểm kê định kỳ và xử lý lệch tồn kho tại từng chi nhánh

Hoạt động kiểm kê diễn ra thường xuyên để đảm bảo số lượng hàng thực tế trên kệ khớp với số liệu trên phần mềm. Thách thức ở đây là cho phép nhân viên tạo các phiếu kiểm kê riêng biệt cho từng kho mà không làm gián đoạn việc bán hàng của các kho khác. Hệ thống cần ghi lại sự chênh lệch giữa tồn kho lý thuyết và tồn kho thực tế, sau đó tự động tạo ra các phiếu bù hoặc phiếu xuất hủy để điều chỉnh lại con số chính xác. Bạn cũng cần lưu lại lịch sử biến động để chủ doanh nghiệp có thể truy cứu trách nhiệm khi có thất thoát hàng hóa xảy ra ở một kho cụ thể.

### Chiến lược ưu tiên xuất hàng theo cấu hình kho

Mỗi doanh nghiệp có một triết lý bán hàng khác nhau, do đó hệ thống cần cho phép cấu hình thứ tự ưu tiên xuất hàng giữa các kho. Ví dụ, chủ cửa hàng muốn ưu tiên xuất hàng từ kho cũ nhất để giải phóng mặt bằng, hoặc ưu tiên xuất từ kho tổng trước khi động vào kho tại cửa hàng bán lẻ. Bài toán yêu cầu thiết kế một hệ thống luật cho phép người dùng thiết lập trọng số hoặc thứ tự cho các kho. Khi có đơn hàng mới, hệ thống sẽ quét qua danh sách kho theo đúng thứ tự đã cài đặt để trừ tồn kho, giúp tự động hóa quy trình vận hành mà không cần sự can thiệp thủ công.

### Quản lý tồn kho an toàn và cảnh báo nhập hàng riêng biệt

Mức tiêu thụ hàng hóa ở mỗi khu vực là khác nhau, nên mỗi kho cần có một định mức tồn kho an toàn riêng. Ví dụ, kho ở thành phố lớn cần dự trữ 500 đơn vị sản phẩm, trong khi kho ở tỉnh lẻ chỉ cần 50 đơn vị. Bài toán yêu cầu hệ thống phải theo dõi ngưỡng tồn kho tối thiểu cho từng SKU tại từng kho. Khi số lượng giảm xuống dưới mức này, hệ thống sẽ tự động gửi thông báo hoặc tạo gợi ý nhập hàng cho kho đó. Điều này giúp bạn luyện tập cách thiết kế các dịch vụ chạy ngầm hoặc các cơ chế trigger để giám sát dữ liệu liên tục.

### Xử lý đơn hàng hoàn trả về đúng kho đã xuất

Khi khách hàng trả lại hàng, một vấn đề đau đầu là xác định hàng hóa đó sẽ được nhập lại vào kho nào. Thông thường, hàng nên được trả về đúng kho đã đóng gói để dễ dàng quản lý dòng tiền và chi phí. Tuy nhiên, cũng có trường hợp khách trả hàng tại cửa hàng gần nhất thay vì gửi về kho gốc. Hệ thống cần quản lý được mối liên kết giữa đơn hàng, phiếu xuất kho và phiếu nhập hàng hoàn trả. Việc thiết kế database phải đủ linh hoạt để ghi nhận hàng trả về là hàng có thể bán tiếp hay hàng lỗi cần thanh lý, gắn liền với vị trí vật lý của kho đó.

### Báo cáo doanh thu và lợi nhuận phân tách theo kho

Để đánh giá hiệu quả kinh doanh, chủ doanh nghiệp cần biết kho nào đang hoạt động tốt nhất và kho nào đang lãng phí chi phí vận hành. Bài toán này yêu cầu bạn tổng hợp dữ liệu từ nhiều bảng như đơn hàng, chi phí vận chuyển, giá vốn hàng bán tại từng kho để đưa ra các báo cáo phân tích. Bạn cần xử lý việc tính toán giá vốn bình quân gia quyền theo từng kho hoặc toàn hệ thống, đồng thời ghi nhận các chi phí phát sinh riêng lẻ của từng địa điểm. Đây là bài toán tuyệt vời để rèn luyện kỹ năng viết các câu truy vấn phức tạp hoặc thiết kế các bảng tổng hợp dữ liệu cho Dashboard.
