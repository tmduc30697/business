# Caching

### Lưu trữ cấu hình hệ thống và danh mục sản phẩm ít thay đổi

Trong một website thương mại điện tử lớn, các dữ liệu như danh mục ngành hàng, danh sách tỉnh thành, hoặc các cấu hình phí vận chuyển mặc định hầu như rất ít khi thay đổi nhưng lại được truy vấn ở mọi trang web. Thay vì bắt cơ sở dữ liệu phải thực hiện các lệnh kết nối bảng phức tạp mỗi khi người dùng tải trang, hệ thống sẽ lưu toàn bộ các danh mục này vào bộ nhớ tạm. Thách thức ở đây là làm sao để khi người quản trị cập nhật một tên ngành hàng mới, toàn bộ các máy chủ đang chạy đều nhận biết được sự thay đổi để xóa bộ nhớ tạm cũ và nạp lại dữ liệu mới nhất.

### Hệ thống bảng xếp hạng thời gian thực cho trò chơi trực tuyến

Một ứng dụng trò chơi có hàng triệu người chơi và cần hiển thị bảng xếp hạng top 100 người có điểm số cao nhất liên tục. Việc thực hiện câu lệnh sắp xếp trên bảng dữ liệu có hàng triệu dòng trong cơ sở dữ liệu quan hệ mỗi giây sẽ gây quá tải ngay lập tức. Bài toán đặt ra là sử dụng một cấu trúc dữ liệu lưu trữ trong bộ nhớ tạm để cập nhật điểm số và tự động sắp xếp thứ hạng ngay khi người chơi kết thúc ván đấu. Hệ thống chỉ ghi nhận kết quả cuối cùng vào cơ sở dữ liệu chính sau một khoảng thời gian nhất định để đảm bảo hiệu suất.

### Giới hạn tần suất gọi API để chống tấn công và quá tải

Để bảo vệ hệ thống khỏi các cuộc tấn công từ chối dịch vụ hoặc việc lạm dụng API từ phía người dùng, bạn cần triển khai cơ chế kiểm soát số lượng yêu cầu trong một khoảng thời gian. Ví dụ, mỗi địa chỉ mạng chỉ được phép gửi tối đa 10 yêu cầu đăng nhập trong vòng 1 phút. Hệ thống cần một bộ lưu trữ tạm có tốc độ cực nhanh để đếm và kiểm tra số lần yêu cầu của từng người dùng dựa trên địa chỉ mạng hoặc mã định danh. Nếu vượt quá giới hạn, hệ thống sẽ từ chối xử lý mà không cần phải truy vấn vào cơ sở dữ liệu chính.

### Lưu trữ thông tin phiên đăng nhập của người dùng trên nhiều máy chủ

Trong các hệ thống phân tán có nhiều máy chủ chạy song song, thông tin đăng nhập của người dùng không thể chỉ lưu ở bộ nhớ của một máy chủ duy nhất vì người dùng có thể được điều hướng sang máy chủ khác ở lần yêu cầu tiếp theo. Bài toán yêu cầu thiết kế một kho lưu trữ tập trung nằm ngoài các máy chủ ứng dụng để chứa thông tin phiên làm việc hoặc mã xác thực. Mỗi khi có yêu cầu gửi đến, máy chủ bất kỳ đều có thể truy cập vào kho lưu trữ tạm này để xác minh danh tính người dùng một cách nhanh chóng mà không cần giải mã lại hoặc truy vấn bảng người dùng trong database.

### Tăng tốc độ hiển thị chi tiết sản phẩm cho các chiến dịch khuyến mãi

Khi một sản phẩm hot được mở bán, hàng vạn người dùng sẽ cùng lúc truy cập vào trang chi tiết sản phẩm đó. Việc truy xuất thông tin từ mô tả, hình ảnh đến các thông số kỹ thuật từ cơ sở dữ liệu cho mỗi lượt xem sẽ tạo ra áp lực khổng lồ. Hệ thống cần cơ chế lưu tạm toàn bộ nội dung trang chi tiết sản phẩm. Tuy nhiên, một vấn đề khó là số lượng tồn kho thay đổi liên tục, do đó bạn cần thiết kế sao cho các thông tin tĩnh được lưu tạm lâu hơn, trong khi thông tin về tồn kho phải được cập nhật hoặc truy vấn với cơ chế riêng biệt để đảm bảo khách hàng không đặt mua hàng đã hết.

### Giảm tải cho các dịch vụ bên thứ ba thông qua lưu trữ kết quả trung gian

Nhiều ứng dụng cần gọi API từ các đối tác bên ngoài như tỉ giá ngoại tệ, thông tin thời tiết hoặc phí giao hàng từ đơn vị vận chuyển. Các dịch vụ này thường giới hạn số lượt gọi hoặc tính phí trên mỗi yêu cầu. Để tiết kiệm chi phí và tăng tốc độ phản hồi, hệ thống sẽ lưu lại kết quả của các lần gọi thành công vào bộ nhớ tạm trong một khoảng thời gian ngắn. Khi có yêu cầu tương tự từ người dùng khác, hệ thống sẽ trả về kết quả từ bộ nhớ tạm thay vì phải thực hiện một cuộc gọi mạng tốn kém ra bên ngoài.

### Lưu trữ nội dung tin nhắn và thông báo mới nhất trong ứng dụng trò chuyện

Trong một ứng dụng nhắn tin, người dùng thường có xu hướng xem lại các tin nhắn gần nhất hoặc các thông báo mới chưa đọc khi vừa mở ứng dụng. Thay vì quét toàn bộ lịch sử tin nhắn khổng lồ trong cơ sở dữ liệu, hệ thống sẽ ưu tiên lưu giữ một số lượng tin nhắn mới nhất của mỗi cuộc hội thoại vào bộ nhớ tạm. Điều này giúp giao diện người dùng hiển thị tức thì các nội dung quan trọng nhất, tạo cảm giác mượt mà trong khi các tin nhắn cũ hơn sẽ được tải dần từ cơ sở dữ liệu chính khi người dùng cuộn trang lên trên.

### Cơ chế hàng đợi tạm thời cho các tác vụ xử lý hậu trường

Khi người dùng thực hiện một thao tác nặng như xuất báo cáo PDF hoặc tải lên hàng nghìn tấm ảnh, hệ thống không thể bắt người dùng chờ đợi phản hồi trực tiếp. Thay vào đó, yêu cầu sẽ được đẩy vào một hàng đợi lưu trong bộ nhớ tạm. Một tiến trình khác chạy ngầm sẽ lấy các yêu cầu này ra để xử lý dần. Trong thời gian đó, người dùng có thể tiếp tục sử dụng các tính năng khác và hệ thống sẽ cập nhật trạng thái tiến độ xử lý vào bộ nhớ tạm để người dùng có thể theo dõi thời gian thực mà không làm nghẽn luồng xử lý chính.
