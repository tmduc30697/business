# Stock quantity update

### Đồng bộ tồn kho giữa các kênh bán hàng đa kênh

Trong mô hình bán hàng Omnichannel, một sản phẩm được niêm yết đồng thời trên website riêng, Shopee, Lazada và cửa hàng vật lý. Khi có một đơn hàng phát sinh từ Shopee, hệ thống cần ngay lập tức khấu trừ số lượng tồn kho tương ứng và phát lệnh cập nhật số dư mới lên tất cả các kênh còn lại để tránh tình trạng bán quá số lượng thực tế. Thách thức nằm ở việc xử lý độ trễ của API từ các sàn thương mại điện tử và đảm bảo tính nhất quán dữ liệu trên toàn hệ thống.

### Quản lý tồn kho theo biến thể thuộc tính phức tạp

Một sản phẩm thời trang như áo thun có thể có nhiều thuộc tính như màu sắc, kích cỡ và chất liệu. Mỗi sự kết hợp giữa các thuộc tính này tạo ra một mã SKU riêng biệt với số lượng tồn kho độc lập. Bài toán yêu cầu hệ thống phải cập nhật chính xác đến từng SKU cụ thể khi nhập hàng hoặc bán lẻ, đồng thời phải có khả năng tổng hợp dữ liệu để báo cáo tổng lượng tồn kho của nhóm sản phẩm cha.

### Giữ hàng tạm thời trong giỏ hàng và thanh toán

Khi khách hàng thêm sản phẩm vào giỏ hàng hoặc tiến hành checkout nhưng chưa thanh toán ngay, hệ thống cần có cơ chế giữ hàng trong một khoảng thời gian nhất định. Trong thời gian này, số lượng tồn kho khả dụng để bán sẽ giảm xuống nhưng số lượng tồn thực tế trong kho chưa thay đổi. Nếu khách hàng hủy đơn hoặc hết thời gian chờ, số lượng giữ hàng phải được hoàn lại vào kho khả dụng một cách tự động và chính xác.

### Cập nhật tồn kho hàng loạt qua tệp tin lớn

Các nhà bán lẻ lớn thường cập nhật tồn kho định kỳ bằng cách tải lên các tệp CSV hoặc Excel chứa hàng chục nghìn mã hàng. Hệ thống cần xử lý tác vụ này dưới nền để không làm gián đoạn các hoạt động khác. Quá trình này bao gồm việc kiểm tra tính hợp lệ của dữ liệu, đối soát mã SKU, cập nhật hàng loạt vào cơ sở dữ liệu và ghi lại nhật ký chi tiết về các dòng cập nhật thành công hoặc thất bại.

### Kiểm kê định kỳ và điều chỉnh sai lệch kho

Trong quá trình vận hành, số lượng hàng hóa trên hệ thống thường có sự sai lệch so với thực tế do thất thoát, hỏng hóc hoặc sai sót khi kiểm đếm. Bài toán đặt ra yêu cầu thiết kế một chức năng kiểm kê, cho phép nhân viên kho nhập số lượng thực tế kiểm được. Hệ thống sau đó tự động tính toán sự chênh lệch, tạo ra các phiếu điều chỉnh tăng hoặc giảm và lưu lại lý do điều chỉnh để phục vụ mục đích đối soát tài chính sau này.

### Xử lý tranh chấp tài nguyên trong các phiên flash sale

Trong các sự kiện giảm giá mạnh với lưu lượng truy cập cực lớn, hàng nghìn người dùng có thể cùng nhấn nút mua một sản phẩm có số lượng giới hạn tại cùng một thời điểm. Hệ thống phải giải quyết bài toán tranh chấp dữ liệu để đảm bảo không xảy ra tình trạng bán vượt mức. Điều này đòi hỏi các giải pháp về hàng đợi xử lý hoặc cơ chế khóa dữ liệu thông minh để đảm bảo hiệu năng và tính chính xác tuyệt đối.

### Quản lý tồn kho tại nhiều kho hàng vật lý

Một chuỗi cửa hàng có nhiều kho hàng đặt tại các vị trí địa lý khác nhau. Khi cập nhật tồn kho, hệ thống cần định danh rõ ràng số lượng thay đổi thuộc về kho nào. Bài toán này yêu cầu thiết kế database có khả năng quản lý quan hệ nhiều-nhiều giữa sản phẩm và kho hàng, đồng thời hỗ trợ các nghiệp vụ điều chuyển hàng hóa nội bộ giữa các kho với các trạng thái như đang vận chuyển, đã nhận hoặc thất thoát trong quá trình chuyển.

### Cập nhật tồn kho dựa trên đơn nhập hàng từ nhà cung cấp

Số lượng tồn kho không chỉ thay đổi do bán hàng mà còn tăng lên thông qua quy trình thu mua. Khi một đơn nhập hàng được phê duyệt và xác nhận đã nhập kho thành công, hệ thống phải tự động cộng dồn số lượng vào kho tương ứng. Quy trình này thường đi kèm với việc cập nhật giá vốn bình quân gia quyền cho sản phẩm, đòi hỏi sự liên kết chặt chẽ giữa module kho và module kế toán mua hàng.
