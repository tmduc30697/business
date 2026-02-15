# Release reserved stock

### Quản lý giỏ hàng và thời hạn thanh toán trên sàn thương mại điện tử

Trong mô hình này, khi người dùng tiến hành thanh toán, hệ thống sẽ giữ hàng trong kho khoảng 15 đến 30 phút. Nếu người dùng không hoàn tất chuyển khoản hoặc thanh toán qua ví điện tử trong thời gian này, hệ thống cần tự động nhả kho để người khác có thể mua. Bài toán yêu cầu bạn thiết kế cơ chế theo dõi trạng thái đơn hàng cùng với một worker hoặc scheduler để quét các đơn hàng hết hạn và thực hiện hoàn trả số lượng tồn kho khả dụng.

### Đặt vé máy bay hoặc vé xem phim theo thời gian thực

Đây là kịch bản mà sơ đồ ghế ngồi là tài sản quan trọng nhất. Khi người dùng chọn một ghế cụ thể, hệ thống sẽ tạm khóa ghế đó để tránh tình trạng trùng lặp. Tuy nhiên, nếu trình duyệt bị đóng đột ngột hoặc phiên làm việc bị ngắt kết nối mà chưa thanh toán thành công, ghế đó phải được giải phóng ngay lập tức. Bạn cần xử lý việc giữ chỗ ở mức độ chi tiết cao và đảm bảo tính nguyên tử của giao dịch để không xảy ra hiện tượng hai người cùng đặt một ghế.

### Sự kiện Flash Sale với lưu lượng truy cập đột biến

Tại các sự kiện giảm giá sâu, hàng nghìn người cùng nhấn nút mua một lúc cho một số lượng sản phẩm rất ít. Bài toán đặt ra là làm thế nào để giữ chỗ hiệu quả trên bộ nhớ đệm như Redis trước khi ghi xuống cơ sở dữ liệu chính. Khi người dùng hủy đơn ở bước xác nhận cuối cùng, hệ thống phải cập nhật lại số dư trên cache thật nhanh để người dùng tiếp theo có cơ hội mua hàng, tránh tình trạng kho ảo hoặc mất mát doanh thu do hàng bị giữ oan.

### Hệ thống đặt bàn nhà hàng hoặc dịch vụ làm đẹp

Khác với sản phẩm vật lý, việc giữ chỗ ở đây gắn liền với khung giờ và nhân sự cụ thể. Khi khách hàng đặt lịch nhưng không đến hoặc hủy lịch sát giờ, hệ thống cần có cơ chế giải phóng khung giờ đó để mở lại cho khách hàng khác. Bài toán này đòi hỏi thiết kế database có tính đến yếu tố thời gian và tài nguyên đi kèm, đồng thời quản lý các trạng thái từ chờ xác nhận đến đã hủy hoặc quá hạn.

### Quản lý kho hàng đa kênh tích hợp với POS

Một cửa hàng bán cả trực tuyến lẫn tại quầy. Khi nhân viên tại quầy quét mã vạch để tạo hóa đơn cho khách nhưng khách đột ngột đổi ý không mua nữa, hoặc khi đơn hàng từ website bị lỗi vận hành, số lượng hàng phải được trả về kho tổng ngay lập tức. Bạn cần thiết kế một hệ thống quản lý tồn kho tập trung sao cho việc cập nhật giữ chỗ và giải phóng hàng từ nhiều nguồn khác nhau luôn đồng bộ và chính xác.

### Đặt trước sản phẩm mới ra mắt theo hình thức đặt cọc

Đối với các sản phẩm hot sắp ra mắt, khách hàng thường thực hiện đặt cọc để giữ chỗ. Nếu khách hàng không thanh toán phần tiền còn lại đúng hạn, khoản giữ chỗ này sẽ bị hủy bỏ. Bài toán yêu cầu quản lý logic phức tạp hơn về việc giữ hàng trong thời gian dài, theo dõi tiến độ thanh toán nhiều giai đoạn và xử lý các kịch bản hoàn tiền đi kèm với hoàn hàng vào kho.

### Hệ thống phân phối voucher giảm giá số lượng giới hạn

Mỗi voucher có một mã định danh duy nhất và số lượng phát hành hạn chế. Khi người dùng áp dụng mã vào đơn hàng nhưng chưa thanh toán, mã đó được coi là đang được giữ. Nếu đơn hàng bị hủy do lỗi cổng thanh toán, mã voucher phải được mở lại để người dùng đó hoặc người khác có thể sử dụng. Điều này đòi hỏi thiết kế bảng lưu trữ lịch sử sử dụng voucher và trạng thái liên kết với từng mã đơn hàng cụ thể.

### Xử lý hoàn kho trong chuỗi cung ứng logistics

Khi một đơn hàng đã được đóng gói và xuất kho nhưng đơn vị vận chuyển không thể liên lạc được với người nhận hoặc người nhận từ chối nhận hàng. Lúc này hàng hóa sẽ được chuyển trạng thái sang hàng hoàn. Hệ thống cần ghi nhận quy trình hàng quay về kho, kiểm tra chất lượng rồi mới thực hiện giải phóng số lượng này vào kho bán hàng. Đây là bài toán về luồng dữ liệu giữa hệ thống quản lý kho và hệ thống quản lý đơn hàng.
