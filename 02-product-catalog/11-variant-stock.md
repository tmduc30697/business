# Variant stock

### Quản lý tồn kho đa thuộc tính cho ngành thời trang

Trong ngành thời trang, một mẫu áo có thể có hàng chục biến thể dựa trên sự kết hợp giữa màu sắc, kích thước và chất liệu. Bài toán đặt ra là làm thế nào để lưu trữ cấu trúc thuộc tính động nhằm cho phép người dùng thêm mới các loại thuộc tính tùy ý mà không phải thay đổi cấu trúc bảng dữ liệu. Hệ thống cần quản lý mã định danh duy nhất cho từng biến thể để phục vụ việc kiểm kho và bán hàng, đồng thời vẫn phải giữ liên kết với sản phẩm cha để hiển thị trên giao diện người dùng.

### Đồng bộ tồn kho thời gian thực trên đa kênh bán hàng

Khi một doanh nghiệp bán hàng cùng lúc trên website riêng, Facebook và các sàn thương mại điện tử, việc một biến thể cụ thể bị hết hàng cần được cập nhật ngay lập tức lên tất cả các kênh. Thách thức ở đây là thiết kế hệ thống xử lý hàng đợi và API để đảm bảo rằng khi khách hàng đặt mua biến thể cuối cùng trên sàn Shopee, hệ thống sẽ tự động khóa kho hoặc cập nhật số lượng về không trên website để tránh tình trạng bán quá số lượng thực tế đang có.

### Quản lý tồn kho theo nhiều kho hàng vật lý

Doanh nghiệp có thể có nhiều chi nhánh hoặc kho hàng tại các khu vực địa lý khác nhau. Một biến thể sản phẩm có thể còn hàng ở kho Quận 1 nhưng đã hết ở kho Quận 7. Bài toán yêu cầu thiết kế cơ sở dữ liệu cho phép theo dõi số lượng tồn kho của từng biến thể tại từng địa điểm cụ thể. Điều này phục vụ cho việc điều hướng đơn hàng thông minh, giúp hệ thống tự động chọn kho gần khách hàng nhất còn hàng để tối ưu chi phí vận chuyển.

### Cơ chế giữ hàng tạm thời trong giỏ hàng và thanh toán

Khi khách hàng thêm một biến thể vào giỏ hàng hoặc bắt đầu bước thanh toán, số lượng tồn kho thực tế chưa bị trừ đi nhưng cần được tạm giữ để tránh người khác mua mất. Hệ thống cần phân biệt giữa tồn kho thực tế trong kho, tồn kho đang bị giữ bởi các đơn hàng chờ xử lý và tồn kho khả dụng có thể bán. Bạn cần thiết kế logic để giải phóng số lượng tạm giữ này nếu khách hàng không hoàn tất thanh toán sau một khoảng thời gian nhất định.

### Quản lý lô hàng và hạn sử dụng cho từng biến thể

Đối với các mặt hàng như mỹ phẩm hoặc thực phẩm, cùng một biến thể sản phẩm nhưng các lô nhập hàng khác nhau sẽ có ngày sản xuất và hạn sử dụng khác nhau. Bài toán yêu cầu quản lý tồn kho chi tiết đến mức số lô. Khi xuất kho, hệ thống cần hỗ trợ các nguyên tắc như nhập trước xuất trước để đảm bảo hàng cũ được bán đi trước, tránh lãng phí do hết hạn sử dụng. Điều này đòi hỏi cấu trúc bảng dữ liệu phải có tầng trung gian giữa biến thể và số lượng thực tế.

### Định giá khác biệt và khuyến mãi cho từng biến thể

Không phải tất cả các biến thể của một sản phẩm đều có giá bằng nhau. Ví dụ, một chiếc iPhone màu vàng có thể đắt hơn màu đen, hoặc dung lượng 512GB có giá cao hơn 128GB. Bài toán đặt ra là thiết kế hệ thống giá bán và chương trình khuyến mãi linh hoạt. Hệ thống phải cho phép áp dụng giảm giá cho một biến thể cụ thể đang tồn kho nhiều mà không ảnh hưởng đến giá của các biến thể khác trong cùng một sản phẩm cha.

### Quy trình kiểm kê và điều chỉnh kho định kỳ

Trong quá trình vận hành, số lượng thực tế trong kho có thể sai lệch so với số liệu trên phần mềm do hư hỏng, mất mát hoặc nhầm lẫn khi đóng gói. Hệ thống cần một chức năng phiếu kiểm kho để nhân viên cập nhật lại số lượng cho từng biến thể. Bài toán này đòi hỏi việc thiết kế bảng lịch sử biến động kho để ghi lại ai đã điều chỉnh, điều chỉnh khi nào, lý do là gì và số lượng thay đổi là bao nhiêu nhằm phục vụ mục đích đối soát và kiểm toán sau này.

### Cảnh báo ngưỡng tồn kho tối thiểu cho từng biến thể

Để đảm bảo hoạt động kinh doanh liên tục, nhà quản lý cần biết khi nào một biến thể sắp hết hàng để kịp thời nhập thêm. Tuy nhiên, mỗi biến thể có tốc độ bán khác nhau nên ngưỡng cảnh báo cũng khác nhau. Bài toán yêu cầu thiết kế hệ thống cấu hình ngưỡng tồn kho an toàn cho từng biến thể riêng biệt. Khi số lượng khả dụng chạm mức này, hệ thống sẽ tự động gửi thông báo hoặc tạo một đề nghị nhập hàng dự kiến để người quản lý phê duyệt.
