# Fraud analytics

### Phát hiện mạng lưới tài khoản ảo thông qua định danh thiết bị và địa chỉ mạng

Trong các chiến dịch tặng quà cho người dùng mới, kẻ gian thường tạo hàng nghìn tài khoản bằng sim rác hoặc email ảo. Tuy nhiên, các tài khoản này thường truy cập từ cùng một địa chỉ IP hoặc có cùng một mã định danh phần cứng của thiết bị di động. Bài toán đặt ra là thiết kế hệ thống có khả năng lưu trữ và đối chiếu các thông tin ẩn này để phát hiện ra một nhóm hàng trăm tài khoản thực chất chỉ thuộc về một người điều khiển, từ đó ngăn chặn việc phân phối ưu đãi hàng loạt.

### Nhận diện hành vi lạm dụng mã giảm giá bằng cách thay đổi thông tin nhận hàng

Kẻ gian có thể lách luật giới hạn theo địa chỉ bằng cách thay đổi nhẹ thông tin như thêm các ký tự lạ vào tên đường, viết tắt tên phường xã hoặc thay đổi số điện thoại liên hệ nhưng vẫn giữ nguyên vị trí giao hàng thực tế. Hệ thống cần một cơ chế chuẩn hóa dữ liệu hoặc tính toán độ tương đồng giữa các địa chỉ và số điện thoại mới với các địa chỉ đã từng nhận ưu đãi trước đó để đưa ra cảnh báo về các đơn hàng có dấu hiệu trục lợi mã giảm giá.

### Cảnh báo sớm các giao dịch có nguy cơ bị hoàn tiền bất thường

Trong thanh toán quốc tế, rủi ro lớn nhất là khách hàng sử dụng thẻ ăn cắp để mua hàng, sau đó chủ thẻ thực sự sẽ yêu cầu ngân hàng hoàn tiền. Bài toán yêu cầu hệ thống phải theo dõi các dấu hiệu bất thường như một tài khoản mới đăng ký nhưng thực hiện liên tiếp nhiều giao dịch giá trị lớn trong thời gian ngắn, hoặc thông tin quốc gia phát hành thẻ khác hoàn toàn với vị trí địa lý của địa chỉ IP đang thực hiện giao dịch để tạm dừng thanh toán và xác minh thủ công.

### Phát hiện gian lận kép giữa người bán và người mua trong sàn thương mại điện tử

Một hình thức gian lận phổ biến là người bán tự tạo tài khoản người mua ảo để đặt hàng của chính mình nhằm chiếm đoạt tiền khuyến mãi từ sàn hoặc tăng lượt bán ảo để leo hạng uy tín. Hệ thống cần phân tích các mối liên hệ như người mua và người bán thường xuyên dùng chung mạng wifi, có cùng lịch sử đăng nhập trên một thiết bị hoặc có dòng tiền luân chuyển vòng quanh để đánh dấu các giao dịch này là không hợp lệ.

### Theo dõi tốc độ sử dụng mã giảm giá để phát hiện tấn công bằng công cụ tự động

Kẻ gian thường sử dụng các đoạn mã tự động để săn mã giảm giá ngay khi chúng vừa được phát hành, khiến người dùng thật không thể tiếp cận được. Bài toán này đòi hỏi hệ thống phải ghi lại nhật ký thời gian chính xác đến từng mili giây của các yêu cầu áp dụng mã. Nếu một địa chỉ IP hoặc một nhóm tài khoản có tốc độ gửi yêu cầu vượt quá khả năng thao tác của con người, hệ thống cần kích hoạt các lớp bảo vệ như yêu cầu xác thực hoặc tạm thời chặn truy cập.

### Phân tích hành vi nạp và rút tiền để phát hiện rửa tiền quy mô nhỏ

Trên các ví điện tử hoặc cổng thanh toán, kẻ gian có thể chia nhỏ số tiền bất chính để nạp vào nhiều tài khoản khác nhau, sau đó thực hiện các giao dịch mua bán ảo để hợp thức hóa dòng tiền rồi rút về một tài khoản đích. Hệ thống cần thiết kế các bảng lưu trữ dòng tiền đi và đến một cách chặt chẽ, cho phép truy vấn ngược dòng tiền qua nhiều cấp độ trung gian để tìm ra điểm cuối cùng của dòng tiền đáng ngờ.

### Phát hiện các giao dịch bị chia nhỏ để tránh ngưỡng kiểm soát rủi ro

Nhiều hệ thống có quy định các giao dịch trên một mức giá nhất định mới cần xác minh danh tính hoặc duyệt thủ công. Kẻ gian sẽ lợi dụng điều này bằng cách chia một đơn hàng lớn thành nhiều đơn hàng nhỏ nằm ngay dưới ngưỡng kiểm soát. Bài toán yêu cầu hệ thống phải có khả năng gom nhóm các giao dịch diễn ra trong khoảng thời gian ngắn có cùng thông tin thẻ hoặc cùng địa chỉ nhận hàng để tính tổng giá trị và áp dụng các quy tắc kiểm soát rủi ro như một giao dịch lớn duy nhất.

### Nhận diện hành vi đầu cơ mã giảm giá để bán lại trên thị trường đen

Một số người dùng chuyên nghiệp thu gom hàng nghìn mã giảm giá bằng cách đăng ký hàng loạt, sau đó bán lại các tài khoản có sẵn mã này cho người khác. Đặc điểm của loại gian lận này là tài khoản sau khi nhận mã sẽ có trạng thái chờ rất lâu, sau đó đột ngột thay đổi thông tin email hoặc số điện thoại ngay trước khi thực hiện giao dịch. Hệ thống cần theo dõi lịch sử thay đổi thông tin nhạy cảm của tài khoản để ngăn chặn việc áp dụng mã khi tài khoản có dấu hiệu bị chuyển nhượng trái phép.
