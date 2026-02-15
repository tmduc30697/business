# Edit product

### Quản lý phiên bản và lịch sử thay đổi thông tin sản phẩm

Trong thực tế, chủ cửa hàng thường vô tình cập nhật sai giá hoặc mô tả sản phẩm và muốn quay lại trạng thái cũ. Bài toán đặt ra là hệ thống cần lưu trữ lại toàn bộ các phiên bản cũ mỗi khi có một lệnh cập nhật được thực thi. Bạn cần thiết kế sao cho có thể truy vấn được ai là người sửa, sửa vào thời gian nào, giá trị cũ là gì và giá trị mới là gì để hỗ trợ tính năng khôi phục dữ liệu khi cần thiết.

### Cập nhật đồng bộ giá và tồn kho cho các biến thể sản phẩm

Một sản phẩm thường có nhiều thuộc tính như màu sắc và kích cỡ tạo thành các phiên bản khác nhau. Khi người bán thay đổi giá của sản phẩm cha, họ có thể muốn áp dụng mức giá đó cho tất cả các biến thể hoặc chỉ một vài biến thể nhất định. Việc cập nhật này đòi hỏi hệ thống xử lý tính nhất quán của dữ liệu để tránh tình trạng sản phẩm cha hiển thị một giá nhưng khi khách hàng chọn màu sắc cụ thể thì giá lại không thay đổi.

### Kiểm duyệt nội dung sau khi người bán chỉnh sửa

Để đảm bảo chất lượng sàn thương mại điện tử, các thay đổi về tên sản phẩm, hình ảnh hoặc mô tả nhạy cảm không được hiển thị ngay lập tức. Khi người bán nhấn lưu, trạng thái của sản phẩm sẽ chuyển sang chờ phê duyệt và thông tin mới sẽ được lưu vào một bảng tạm. Trong lúc đó, khách hàng vẫn nhìn thấy thông tin cũ của sản phẩm. Chỉ sau khi quản trị viên phê duyệt, các thông tin mới này mới chính thức ghi đè lên dữ liệu cũ.

### Quản lý quyền chỉnh sửa trong mô hình gian hàng nhiều nhân viên

Trên các hệ thống lớn, một gian hàng có thể có nhiều nhân viên với các vai trò khác nhau như nhân viên kho, nhân viên content và quản lý. Bài toán yêu cầu thiết kế hệ thống phân quyền sao cho nhân viên kho chỉ được phép cập nhật số lượng tồn kho, nhân viên content chỉ được sửa mô tả và hình ảnh, còn chỉ có chủ cửa hàng mới có quyền thay đổi giá bán hoặc áp dụng các chương trình khuyến mãi.

### Tối ưu hóa cập nhật hình ảnh và quản lý tài nguyên lưu trữ

Khi người bán cập nhật hình ảnh sản phẩm, họ có thể xóa ảnh cũ, thêm ảnh mới hoặc thay đổi thứ tự hiển thị. Hệ thống cần xử lý việc xóa các tập tin vật lý trên máy chủ lưu trữ đối với những ảnh không còn được sử dụng để tiết kiệm tài nguyên. Ngoài ra, việc thay đổi thứ tự ảnh cũng cần một cơ chế đánh số thứ tự linh hoạt trong cơ sở dữ liệu để đảm bảo trải nghiệm người dùng trên ứng dụng di động và website đồng nhất.

### Xử lý tranh chấp dữ liệu khi nhiều người cùng chỉnh sửa một sản phẩm

Trong môi trường doanh nghiệp, có trường hợp hai nhân viên cùng mở trang chỉnh sửa một sản phẩm tại một thời điểm. Nếu nhân viên A cập nhật giá và lưu trước, sau đó nhân viên B cập nhật mô tả và lưu sau, hành động của nhân viên B có thể vô tình ghi đè và làm mất dữ liệu giá mà nhân viên A vừa cập nhật. Bạn cần giải quyết bài toán khóa dữ liệu hoặc kiểm tra tính toàn vẹn để đảm bảo không có thay đổi nào bị mất mát một cách vô lý.

### Tự động tính toán lại các chỉ số sau khi cập nhật thông tin

Khi các thông tin cốt lõi như giá nhập, giá bán hoặc trọng lượng sản phẩm thay đổi, hệ thống cần tự động tính toán lại các thông tin liên quan như phần trăm giảm giá, phí vận chuyển dự kiến và biên lợi nhuận. Nếu sản phẩm đang tham gia một chiến dịch khuyến mãi, việc thay đổi giá gốc có thể vi phạm điều lệ của chiến dịch, yêu cầu hệ thống phải thực hiện các bước kiểm tra logic phức tạp để cảnh báo người dùng.

### Cập nhật dữ liệu hàng loạt và đồng bộ hóa với hệ thống tìm kiếm

Khi người bán cập nhật hàng loạt thông tin cho hàng nghìn sản phẩm cùng lúc thông qua file excel, việc ghi trực tiếp vào cơ sở dữ liệu quan hệ có thể gây nghẽn cổ chai. Bên cạnh đó, các công cụ tìm kiếm bên ngoài như Elasticsearch cần được thông báo để cập nhật lại chỉ mục ngay lập tức. Bài toán này yêu cầu bạn thiết kế một cơ chế hàng đợi để xử lý việc cập nhật dưới nền nhằm đảm bảo hệ thống vẫn hoạt động mượt mà cho người mua hàng.
