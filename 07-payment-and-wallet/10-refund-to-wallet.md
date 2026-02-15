# Refund to wallet

### Xử lý hoàn tiền từng phần cho đơn hàng có nhiều sản phẩm

Khách hàng đặt một đơn hàng gồm năm món đồ khác nhau và thanh toán toàn bộ bằng thẻ tín dụng. Sau khi nhận hàng, khách hàng phát hiện hai món bị lỗi và yêu cầu trả hàng. Thay vì đợi quy trình đối soát ngân hàng kéo dài từ bảy đến mười bốn ngày, hệ thống cho phép khách hàng chọn nhận lại tiền ngay lập tức vào ví nội bộ của ứng dụng. Bài toán yêu cầu hệ thống phải tính toán chính xác số tiền tương ứng của hai sản phẩm đó, bao gồm cả việc trừ đi các chi phí khuyến mãi đã phân bổ, và cập nhật số dư ví đồng thời với việc lưu lại lịch sử giao dịch để đối chiếu với mã đơn hàng gốc.

### Quy đổi giá trị đơn hàng hủy sang voucher hoặc số dư ví

Một nền tảng đặt phòng khách sạn trực tuyến có chính sách hủy phòng sát giờ sẽ không được hoàn tiền về tài khoản ngân hàng. Tuy nhiên, để giữ chân khách hàng, nền tảng đề xuất một lựa chọn là hoàn lại tám mươi phần trăm giá trị đơn đặt phòng vào ví tích lũy trên ứng dụng. Số tiền này chỉ có giá trị sử dụng để đặt các dịch vụ khác trên cùng hệ thống trong vòng sáu tháng. Người thiết kế cần giải quyết vấn đề về thời hạn sử dụng của dòng tiền trong ví và cách thức ưu tiên trừ tiền khi khách hàng có cả tiền nạp thủ công và tiền được hoàn từ chính sách hủy phòng.

### Hoàn tiền tự động khi giao dịch thanh toán bị lỗi kỹ thuật

Trong quá trình thanh toán qua cổng điện tử, người dùng đã bị trừ tiền ở ngân hàng nhưng phía nhà cung cấp dịch vụ chưa nhận được phản hồi thành công do nghẽn mạng, dẫn đến đơn hàng ở trạng thái thất bại. Để xử lý trải nghiệm khách hàng một cách nhanh chóng mà không cần chờ đợi tra soát thủ công giữa các bên, hệ thống tự động ghi nhận một khoản tiền tương đương vào ví nội bộ của người dùng. Bài toán này tập trung vào tính nhất quán dữ liệu giữa bảng giao dịch thanh toán lỗi và bảng tăng số dư ví để đảm bảo không xảy ra tình trạng hoàn tiền hai lần.

### Quản lý nguồn tiền hoàn từ các chiến dịch khuyến mãi Cashback

Công ty thương mại điện tử chạy chương trình hoàn tiền mười phần trăm giá trị đơn hàng vào ví thành viên sau khi đơn hàng được giao thành công. Khác với tiền khách hàng nạp vào, nguồn tiền từ cashback này thường có những điều kiện sử dụng khắt khe hơn như không được rút về ngân hàng và chỉ được dùng để thanh toán tối đa năm mươi phần trăm giá trị đơn hàng tiếp theo. Việc thiết kế database phải phân biệt được các loại "nguồn tiền" khác nhau trong cùng một chiếc ví để áp dụng các quy tắc kiểm tra (validation) khi thanh toán.

### Xử lý hoàn tiền khi đơn hàng được thanh toán bằng nhiều phương thức

Người dùng mua một món đồ điện tử giá cao bằng cách kết hợp dùng hai triệu đồng từ ví nội bộ và năm triệu đồng thanh toán qua thẻ ngân hàng. Khi đơn hàng bị hủy, người dùng yêu cầu toàn bộ bảy triệu đồng được hoàn vào ví nội bộ để họ có thể mua sản phẩm khác ngay lập tức. Hệ thống cần phải quản lý được luồng tiền chảy ngược từ hai nguồn khác nhau về một điểm tập trung duy nhất, đồng thời phải lưu trữ vết (traceability) để phục vụ công tác kiểm toán tài chính sau này về việc tại sao số dư ví lại tăng đột biến.

### Chính sách hoàn tiền bù đắp cho dịch vụ vận chuyển chậm trễ

Một ứng dụng giao đồ ăn có cam kết giao hàng trong ba mươi phút, nếu chậm trễ sẽ hoàn lại phí vận chuyển cho khách hàng. Hệ thống cần một cơ chế giám sát thời gian thực, khi đơn hàng được đánh dấu hoàn thành quá giờ quy định, một tiến trình chạy ngầm sẽ tính toán phí giao hàng và thực hiện lệnh nạp tiền vào ví nội bộ của khách hàng như một hình thức xin lỗi. Bài toán này đòi hỏi sự phối hợp giữa dịch vụ vận chuyển, dịch vụ đơn hàng và dịch vụ ví điện tử để thực hiện các giao dịch nhỏ (micro-transactions) một cách chính xác.

### Thu hồi tiền hoàn khi phát hiện gian lận hoặc trả hàng ngược

Sau khi khách hàng nhận được tiền hoàn vào ví nội bộ cho một đơn hàng bị lỗi, bộ phận kiểm tra phát hiện khách hàng có hành vi gian lận hoặc khách hàng thay đổi ý định và muốn lấy lại sản phẩm đó. Hệ thống cần có cơ chế "đóng băng" số tiền trong ví hoặc thực hiện giao dịch điều chỉnh giảm nếu số tiền hoàn chưa được sử dụng. Nếu người dùng đã dùng hết tiền hoàn để mua đơn hàng mới, hệ thống phải xử lý kịch bản số dư âm hoặc tạo ra một khoản nợ cần thu hồi trong lần nạp tiền tiếp theo.

### Hoàn tiền từ phí đăng ký thành viên theo gói tháng

Một dịch vụ xem phim trực tuyến cho phép người dùng đăng ký gói thành viên theo năm. Nếu người dùng muốn hủy gói ở tháng thứ sáu, hệ thống sẽ tính toán số tiền còn lại sau khi trừ đi phí sử dụng của các tháng đã qua theo giá bán lẻ và hoàn phần chênh lệch vào ví tài khoản. Bài toán đặt ra thách thức về việc thiết kế logic tính toán số tiền hoàn dựa trên thời gian thực tế sử dụng và cách thức ghi nhận doanh thu chưa thực hiện (unearned revenue) trong hệ thống kế toán khi tiền chuyển từ trạng thái phí dịch vụ sang số dư ví.
