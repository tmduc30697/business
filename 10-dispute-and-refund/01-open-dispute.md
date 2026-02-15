# Open dispute

### Quản lý quy trình trạng thái khiếu nại theo thời gian thực

Hệ thống cần theo dõi vòng đời của một khiếu nại từ khi người mua khởi tạo cho đến khi đóng lại. Các trạng thái có thể bao gồm: Đang chờ người bán phản hồi, Đang thương lượng, Chờ vận chuyển trả hàng, Đang kiểm định, và Hoàn tất. Thách thức ở đây là việc kiểm soát các quy tắc chuyển đổi trạng thái để đảm bảo người dùng không thể thực hiện các thao tác sai quy trình, ví dụ như không thể hoàn tiền khi hàng trả lại chưa được xác nhận đã về kho.

### Cơ chế tự động phản hồi và thời hạn phản hồi giới hạn

Trong thực tế, các sàn thương mại điện tử luôn đặt ra các mốc thời gian tối đa để các bên phản hồi. Nếu người bán không phản hồi khiếu nại của người mua trong vòng 48 giờ, hệ thống sẽ tự động chấp nhận yêu cầu hoàn tiền. Ngược lại, nếu người mua không cung cấp bằng chứng bổ sung khi được yêu cầu trong một khoảng thời gian nhất định, khiếu nại sẽ tự động bị hủy. Bạn cần giải quyết bài toán quản lý các tác vụ hẹn giờ này trên quy mô hàng triệu đơn hàng.

### Quản lý bằng chứng đa phương tiện và dung lượng lớn

Khi mở khiếu nại, người mua thường phải tải lên hình ảnh hoặc video quay cảnh mở hộp để chứng minh hàng lỗi hoặc thiếu. Bài toán đặt ra là cách lưu trữ và liên kết các tệp tin này với mã khiếu nại sao cho tối ưu. Hệ thống cần phân loại bằng chứng từ phía người mua và bằng chứng phản biện từ phía người bán, đồng thời đảm bảo tính toàn vẹn của dữ liệu để làm căn cứ pháp lý khi có tranh chấp sâu hơn.

### Hệ thống thương lượng giá trị hoàn tiền một phần

Không phải lúc nào khiếu nại cũng dẫn đến việc trả hàng và hoàn tiền toàn bộ. Một bài toán phổ biến là người mua muốn giữ lại sản phẩm bị lỗi nhẹ và yêu cầu hoàn lại một phần tiền. Hệ thống phải cho phép hai bên đưa ra các đề nghị thay đổi số tiền hoàn lại qua lại nhiều lần. Bạn cần thiết kế cách lưu vết lịch sử các lần mặc cả này và đảm bảo số tiền hoàn lại không bao giờ vượt quá số tiền thực tế mà người mua đã thanh toán.

### Tích hợp đơn vị vận chuyển trong quy trình trả hàng

Khi một khiếu nại được chấp nhận theo hình thức trả hàng hoàn tiền, hệ thống cần tự động tạo một mã vận đơn trả hàng. Bài toán này yêu cầu sự kết nối với các đối tác giao vận để theo dõi lộ trình của gói hàng trả về. Tiền chỉ được hoàn lại cho người mua sau khi hệ thống nhận được tín hiệu giao hàng thành công từ phía đơn vị vận chuyển và người bán xác nhận tình trạng hàng hóa thu hồi vẫn ổn định.

### Phân xử trung gian bởi nhân viên sàn thương mại

Khi người mua và người bán không thể đi đến thống nhất sau một số vòng thương lượng, hệ thống cần có cơ chế đẩy khiếu nại lên mức tranh chấp để nhân viên sàn nhảy vào can thiệp. Bài toán này tập trung vào việc thiết kế giao diện quản trị và quyền hạn cho nhân viên hỗ trợ, cho phép họ xem lại toàn bộ lịch sử trò chuyện, bằng chứng của hai bên và đưa ra quyết định cuối cùng có tính cưỡng chế cao nhất.

### Hệ thống chat nội bộ phục vụ tranh chấp

Để giải quyết khiếu nại nhanh chóng, các bên thường cần trao đổi trực tiếp với nhau trong ngữ cảnh của chính khiếu nại đó. Thay vì dùng tin nhắn chung, hệ thống cần một kênh chat riêng biệt gắn liền với mã khiếu nại. Lưu vết hội thoại này không chỉ giúp hai bên hiểu nhau hơn mà còn là dữ liệu quan trọng để nhân viên sàn phân tích đúng sai khi thực hiện bước phân xử trung gian.

### Quản lý ví tiền và dòng tiền hoàn lại

Đây là bài toán liên quan chặt chẽ đến tài chính và kế toán. Khi một khiếu nại được kết thúc với kết quả hoàn tiền, hệ thống phải thực hiện các lệnh điều chuyển dòng tiền từ tài khoản tạm giữ của sàn về lại ví của người mua hoặc hoàn về thẻ tín dụng ban đầu. Bạn cần xử lý các trường hợp phức tạp như đơn hàng được thanh toán bằng nhiều phương thức kết hợp như voucher, điểm thưởng và tiền mặt.
