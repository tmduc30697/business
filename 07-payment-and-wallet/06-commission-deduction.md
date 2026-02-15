# Commission deduction

### Xử lý đơn hàng đa người bán trên sàn thương mại điện tử

Trong mô hình Marketplace, một khách hàng có thể đặt một đơn hàng chứa sản phẩm từ nhiều nhà cung cấp khác nhau. Khi khách hàng thanh toán tổng hóa đơn, hệ thống cần phải bóc tách số tiền đó thành từng phần riêng biệt cho mỗi người bán. Thách thức ở đây là mỗi ngành hàng hoặc mỗi cấp độ người bán lại có một tỷ lệ chiết khấu khác nhau. Hệ thống phải tính toán chính xác số tiền thực nhận của từng seller sau khi đã trừ đi phí sàn và lưu trữ lịch sử đối soát để người bán có thể kiểm tra lại dòng tiền của họ vào cuối tháng.

### Hoàn tiền và thu hồi hoa hồng khi hủy đơn hàng

Một vấn đề phức tạp phát sinh khi khách hàng yêu cầu trả hàng hoặc hoàn tiền sau khi giao dịch đã hoàn tất. Nếu sàn thương mại điện tử đã khấu trừ hoa hồng và ghi nhận số tiền còn lại vào ví của người bán, thì khi việc hoàn tiền xảy ra, hệ thống cần có cơ chế đảo ngược quy trình. Bạn cần giải quyết bài toán: liệu sàn sẽ thu hồi lại phần hoa hồng đã trừ hay người bán phải chịu hoàn toàn chi phí hoàn trả, và làm thế nào để cập nhật số dư ví của các bên mà không gây ra sai lệch trong báo cáo tài chính.

### Phân bổ hoa hồng cho tiếp thị liên kết nhiều tầng

Trong các nền tảng có sử dụng đội ngũ cộng tác viên bán hàng, một đơn hàng thành công không chỉ phát sinh phí cho sàn mà còn phải trích chi phí cho người giới thiệu. Khi một giao dịch được thanh toán, hệ thống cần tự động tính toán hai lớp khấu trừ: lớp thứ nhất là phí dịch vụ của nền tảng và lớp thứ hai là tiền hoa hồng trả cho cộng tác viên. Số tiền còn lại sau cùng mới được chuyển về cho chủ shop. Điều này đòi hỏi một logic tính toán song song và khả năng truy vết nguồn gốc của lượt mua hàng cực kỳ chính xác.

### Thu phí dịch vụ vận chuyển và bảo hiểm từ doanh thu

Ngoài phí hoa hồng cố định trên sản phẩm, nhiều nền tảng còn cung cấp các dịch vụ gia tăng như vận chuyển hỏa tốc hoặc bảo hiểm hàng hóa. Khi khách hàng thanh toán, các khoản phí này thường được thu gộp. Hệ thống xử lý thanh toán phải phân tách được đâu là doanh thu từ sản phẩm, đâu là phí vận chuyển mà sàn thu hộ đơn vị logistics, và đâu là phí bảo hiểm. Sau đó, từ phần doanh thu sản phẩm, hệ thống mới tiếp tục thực hiện bước khấu trừ hoa hồng dựa trên hợp đồng đã ký với người bán.

### Quyết toán tiền lương dựa trên hiệu suất cho đối tác tài xế

Đối với các ứng dụng đặt xe hoặc giao đồ ăn, mỗi chuyến đi là một giao dịch riêng lẻ. Nền tảng sẽ tự động trừ một tỷ lệ phần trăm phí quản lý ngay khi chuyến xe kết thúc. Tuy nhiên, bài toán trở nên khó hơn khi áp dụng các chương trình thưởng đạt mốc hoặc trừ phí phạt. Hệ thống cần ghi nhận đồng thời việc khấu trừ hoa hồng theo từng chuyến và cộng dồn các khoản thưởng/phạt để đưa ra con số cuối cùng mà tài xế có thể rút về ngân hàng theo chu kỳ hàng ngày hoặc hàng tuần.

### Quản lý hoa hồng biến động theo chương trình khuyến mãi

Vào các đợt giảm giá lớn, sàn thương mại điện tử thường hỗ trợ người bán bằng cách giảm tỷ lệ hoa hồng để khuyến khích giảm giá sâu cho người dùng. Bài toán đặt ra là hệ thống phải có khả năng áp dụng các mức chiết khấu linh hoạt theo thời gian thực. Một sản phẩm có thể chịu phí hoa hồng tám phần trăm vào ngày thường nhưng chỉ chịu năm phần trăm vào khung giờ vàng. Database và API cần được thiết kế để phản ánh đúng mức phí tại thời điểm giao dịch phát sinh thay vì chỉ lấy mức phí hiện tại trong cấu hình hệ thống.

### Tích hợp ví điện tử và độ trễ trong thanh toán

Nhiều nền tảng không giữ tiền của người bán mà thanh toán thông qua một bên thứ ba hoặc ví điện tử trung gian. Khi khách hàng bấm xác nhận đã nhận hàng, hệ thống phải gửi lệnh quyết toán đến cổng thanh toán. Lệnh này yêu cầu chia dòng tiền ngay lập tức: một phần về tài khoản ngân hàng của sàn và phần còn lại về ví của người bán. Bạn cần thiết kế hệ thống sao cho đảm bảo tính nhất quán dữ liệu nếu chẳng may có lỗi mạng xảy ra giữa chừng, đảm bảo tiền không bị thất thoát hoặc bị trừ trùng lặp.

### Khấu trừ thuế thu nhập cá nhân tại nguồn cho người bán

Tại một số quốc gia, nền tảng có nghĩa vụ thu hộ thuế thu nhập cho nhà nước từ doanh thu của những người kinh doanh cá thể. Như vậy, quy trình khấu trừ không chỉ dừng lại ở phí hoa hồng của sàn. Sau khi tính toán doanh thu trừ đi hoa hồng, hệ thống phải thực hiện thêm một bước tính toán thuế dựa trên doanh thu lũy kế của người bán đó trong tháng hoặc trong năm. Việc thiết kế database phải lưu trữ được các thông tin định danh thuế và các bảng biểu thuế suất thay đổi theo quy định pháp luật.
