# Soft delete product

### Quản lý giỏ hàng và biến động trạng thái sản phẩm

Trong các hệ thống thương mại điện tử, người dùng thường thêm sản phẩm vào giỏ hàng và để đó trong thời gian dài. Khi người quản trị thực hiện xóa một sản phẩm khỏi danh mục kinh doanh, hệ thống cần xử lý sao cho sản phẩm đó không còn xuất hiện trong kết quả tìm kiếm nhưng vẫn phải hiển thị trong giỏ hàng của người dùng với trạng thái là không còn khả dụng. Bài toán yêu cầu thiết kế cách truy vấn để tách biệt giữa việc hiển thị sản phẩm đang bán và việc kiểm tra sự tồn tại của sản phẩm trong các thực thể liên kết như chi tiết giỏ hàng hoặc danh sách yêu thích.

### Ràng buộc toàn vẹn dữ liệu trong lịch sử đơn hàng

Khi một đơn hàng đã hoàn tất, thông tin sản phẩm tại thời điểm đó đóng vai trò là bằng chứng pháp lý và tài chính. Nếu một sản phẩm bị xóa hoàn toàn khỏi database, các báo cáo doanh thu hoặc lịch sử mua hàng của khách hàng sẽ bị lỗi liên kết hoặc mất thông tin tên sản phẩm, giá bán. Thách thức ở đây là thiết kế bảng dữ liệu sao cho các khóa ngoại vẫn giữ được tính toàn vẹn, đồng thời đảm bảo rằng khi quản trị viên khôi phục lại sản phẩm, các liên kết cũ không bị xung đột với những thay đổi dữ liệu phát sinh trong thời gian sản phẩm bị ẩn.

### Xử lý trùng lặp Unique Constraint khi khôi phục dữ liệu

Một vấn đề kinh điển trong Soft Delete là xung đột nhãn hoặc mã sản phẩm. Giả sử hệ thống yêu cầu mã định danh sản phẩm là duy nhất. Người dùng xóa sản phẩm A có mã là PROD01, sau đó tạo một sản phẩm mới cũng lấy mã PROD01. Nếu sau đó người dùng muốn khôi phục sản phẩm A ban đầu, hệ thống sẽ gặp lỗi trùng lặp dữ liệu trong database. Bạn cần thiết kế giải pháp để quản lý các chỉ mục duy nhất này, ví dụ như đưa thêm mốc thời gian xóa vào tổ hợp khóa chính hoặc xử lý logic đổi tên tự động khi khôi phục.

### Phân quyền và quy trình phê duyệt xóa đa cấp

Trong các doanh nghiệp lớn, việc xóa một sản phẩm cao cấp không diễn ra ngay lập tức. Khi nhân viên kho bấm xóa, sản phẩm sẽ rơi vào trạng thái chờ xóa. Lúc này, sản phẩm bị ẩn khỏi ứng dụng phía khách hàng nhưng vẫn hiển thị trong bảng điều khiển của cấp quản lý để phê duyệt hoặc từ chối. Bài toán này tập trung vào việc thiết kế các trường trạng thái kết hợp với đánh dấu xóa mềm để tạo ra một quy trình làm việc khép kín, đảm bảo dữ liệu không bị mất mát do sai sót cá nhân hoặc hành động ác ý.

### Quản lý tệp tin và tài nguyên đính kèm

Sản phẩm thường đi kèm với hình ảnh, video và tài liệu hướng dẫn được lưu trữ trên các dịch vụ lưu trữ đám mây. Khi thực hiện xóa mềm sản phẩm, các tệp tin này không được phép xóa vật lý ngay lập tức để phục vụ việc khôi phục. Tuy nhiên, nếu để lâu sẽ gây tốn kém chi phí lưu trữ. Bài toán đặt ra yêu cầu thiết kế một tiến trình chạy ngầm để kiểm tra những sản phẩm đã ở trạng thái xóa mềm quá một khoảng thời gian nhất định, sau đó mới tiến hành xóa vĩnh viễn cả bản ghi trong database lẫn tệp tin vật lý trên server.

### Thống kê báo cáo và loại trừ dữ liệu rác

Hệ thống báo cáo kinh doanh cần tính toán doanh thu, tồn kho và hiệu suất bán hàng. Nếu không xử lý khéo léo, các sản phẩm đã bị xóa mềm có thể làm sai lệch dữ liệu thống kê nếu chúng vẫn được tính vào tổng lượng hàng tồn kho hiện có. Bạn cần thiết kế các tầng API hoặc các View trong database sao cho mặc định các truy vấn báo cáo sẽ loại bỏ các sản phẩm đã xóa, nhưng các truy vấn kiểm toán tài chính lại phải bao gồm cả những sản phẩm này để khớp số liệu tiền tệ.

### Đồng bộ hóa dữ liệu sang bộ tìm kiếm bên thứ ba

Nhiều hệ thống sử dụng các công cụ như Elasticsearch để hỗ trợ tìm kiếm sản phẩm nhanh chóng. Khi một sản phẩm được đánh dấu xóa mềm trong cơ sở dữ liệu chính, hệ thống cần một cơ chế để đồng bộ trạng thái này sang bộ chỉ mục tìm kiếm ngay lập tức. Nếu quá trình đồng bộ thất bại, người dùng vẫn sẽ tìm thấy sản phẩm nhưng khi bấm vào chi tiết lại nhận lỗi không tồn tại. Bài toán yêu cầu thiết kế cơ chế Event-driven hoặc Message Queue để đảm bảo tính nhất quán dữ liệu giữa database và search engine.

### Quản lý phiên bản và lịch sử thay đổi trước khi xóa

Trước khi một sản phẩm bị xóa mềm, nó có thể đã trải qua nhiều lần cập nhật giá và thông số. Bài toán yêu cầu thiết kế hệ thống sao cho khi một sản phẩm được khôi phục, người quản trị có thể xem lại toàn bộ lịch sử các phiên bản cũ để quyết định sẽ khôi phục về trạng thái gần nhất hay một trạng thái cụ thể trong quá khứ. Điều này đòi hỏi sự kết hợp giữa bảng lưu trữ lịch sử thay đổi và cơ chế đánh dấu xóa mềm trên bản ghi chính.
