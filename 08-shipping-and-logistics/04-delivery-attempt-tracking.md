# Delivery attempt tracking

### Quản lý vòng đời trạng thái đơn hàng và lịch sử tái giao hàng

Bài toán này tập trung vào việc lưu trữ chi tiết từng lần nhân viên giao hàng đến địa chỉ người nhận nhưng không thành công. Hệ thống cần phân biệt rõ ràng giữa trạng thái tổng quát của đơn hàng và nhật ký chi tiết của các lần thử. Mỗi lần giao thất bại phải ghi lại mốc thời gian chính xác, vị trí tọa độ của tài xế lúc đó, và mã lý do cụ thể. Điều này giúp bạn thiết kế bảng quan hệ một-nhiều giữa đơn hàng và các lượt nỗ lực giao hàng, phục vụ cho việc đối soát dữ liệu sau này.

### Phân loại và xử lý quy trình theo lý do giao hàng thất bại

Mỗi lý do giao hàng thất bại sẽ dẫn đến một luồng xử lý khác nhau trong hệ thống. Ví dụ, nếu lý do là người nhận hẹn ngày khác, đơn hàng sẽ được đưa vào hàng chờ tái giao; nếu lý do là sai địa chỉ, đơn hàng cần chuyển sang bộ phận chăm sóc khách hàng để cập nhật thông tin. Bài toán yêu cầu bạn thiết kế bảng danh mục lý do thông minh và các cờ trạng thái để điều hướng quy trình tự động, giúp giảm thiểu sự can thiệp thủ công của điều phối viên.

### Xác thực nỗ lực giao hàng qua bằng chứng hình ảnh và định vị

Để tránh việc tài xế báo cáo ảo nhằm chạy KPI, hệ thống cần yêu cầu minh chứng cho mỗi lần giao thất bại. Bài toán đặt ra là lưu trữ và quản lý các tệp tin hình ảnh hiện trường hoặc ảnh chụp cuộc gọi không thành công gắn liền với từng nỗ lực giao hàng. Bạn sẽ cần cân nhắc cách thiết kế API để tải lên dữ liệu đa phương tiện và cách liên kết các đường dẫn hình ảnh này vào cơ sở dữ liệu sao cho tối ưu tốc độ truy vấn và dung lượng lưu trữ.

### Giới hạn số lần giao lại và quy trình chuyển hoàn tự động

Hầu hết các đơn vị vận chuyển đều có quy định tối đa ba lần giao hàng trước khi trả hàng về cho người gửi. Bài toán này yêu cầu hệ thống phải tự động đếm số lần thất bại dựa trên lịch sử giao hàng. Khi số lần này đạt đến ngưỡng cấu hình, hệ thống phải tự động kích hoạt lệnh chuyển hoàn. Việc này giúp bạn luyện tập tư duy về các hàm điều kiện, trigger trong cơ sở dữ liệu hoặc các worker chạy ngầm để quét và cập nhật trạng thái đơn hàng hàng loạt.

### Hệ thống thông báo và tương tác với người nhận sau mỗi lần hụt

Khi một lần giao hàng thất bại được ghi nhận, hệ thống cần ngay lập tức gửi thông báo qua ứng dụng hoặc tin nhắn cho người mua. Bài toán yêu cầu thiết kế các điểm cuối API để kích hoạt dịch vụ thông báo và cho phép người dùng phản hồi nhanh, chẳng hạn như xác nhận thời gian giao lại mong muốn. Điều này giúp bạn hình dung về sự tương tác giữa hệ thống quản lý vận hành và giao diện người dùng cuối, cũng như cách xử lý dữ liệu phản hồi từ khách hàng.

### Phân tích hiệu suất tài xế dựa trên tỷ lệ giao hàng thành công lần đầu

Bài toán này phục vụ mục đích quản trị và báo cáo. Dựa trên dữ liệu nỗ lực giao hàng, bạn cần tr xuất thông tin để tính toán tỷ lệ thành công ngay trong lần đầu tiên của từng tài xế hoặc từng khu vực. Dữ liệu này đòi hỏi cấu trúc database phải hỗ trợ các truy vấn gộp và thống kê phức tạp. Đây là bài toán thực tế giúp bạn thiết kế các bảng trung gian hoặc view để tối ưu hóa hiệu suất cho các báo cáo quản trị lớn.

### Quản lý kho hàng tạm giữ cho các đơn hàng chờ giao lại

Sau một nỗ lực giao hàng không thành công, hàng hóa thường được mang về kho cục bộ thay vì để trên xe tài xế qua đêm. Bài toán yêu cầu quản lý vị trí lưu kho tạm thời của các đơn hàng này. Bạn cần thiết kế hệ thống sao cho biết được chính xác đơn hàng đang nằm ở túi hàng nào, kệ nào trong kho sau khi giao trượt, giúp việc tìm kiếm và bàn giao cho tài xế vào ngày hôm sau trở nên nhanh chóng.

### Tối ưu hóa lộ trình dựa trên lịch sử giao thất bại theo khung giờ

Dữ liệu về các lần giao hàng thất bại thường chứa đựng thông tin về thói quen của người nhận tại một khu vực. Bài toán này đặt ra vấn đề phân tích các mốc thời gian thường xuyên không liên lạc được để gợi ý lộ trình giao hàng tốt hơn cho lần sau. Việc thiết kế cơ sở dữ liệu phải đảm bảo tính nhất quán của dữ liệu thời gian và địa điểm để các thuật toán tối ưu hóa hoặc hệ thống gợi ý có thể khai thác hiệu quả.

### Xử lý tranh chấp và đối soát giữa người bán và đơn vị vận chuyển

Khi một đơn hàng bị chuyển hoàn do giao không thành công nhiều lần, người bán thường yêu cầu bằng chứng xác thực để chấp nhận chịu phí vận chuyển. Bài toán yêu cầu thiết kế hệ thống xuất dữ liệu đối soát minh bạch, bao gồm đầy đủ lịch sử các lần thử, lý do, và phản hồi của người mua. Đây là phần quan trọng để thiết kế các module liên quan đến tài chính, công nợ và báo cáo minh chứng trong hệ thống logistics.

### Thiết kế hệ thống ghi log và kiểm soát thay đổi dữ liệu giao hàng

Vì thông tin giao hàng thất bại có thể bị thay đổi bởi tài xế hoặc nhân viên điều phối, bài toán yêu cầu một cơ chế lưu vết mọi thay đổi. Bạn cần thiết kế các bảng nhật ký hệ thống để ghi lại ai đã cập nhật lý do giao thất bại, cập nhật vào lúc nào và giá trị cũ là gì. Điều này cực kỳ quan trọng trong việc bảo mật dữ liệu và giải quyết các vấn đề gian lận trong quá trình vận hành thực tế.
