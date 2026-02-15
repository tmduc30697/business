# Category assignment

### Hệ thống quản lý sàn thương mại điện tử đa cấp

Trong bài toán này, bạn cần xây dựng một cấu trúc cây danh mục nhiều cấp độ, ví dụ: Điện thoại > Smartphone > iPhone. Một sản phẩm khi được đăng bán chỉ được chọn vào danh mục lá cuối cùng nhưng hệ thống phải tự hiểu nó thuộc về tất cả các danh mục cha phía trên. Thách thức ở đây là việc truy vấn ngược từ một danh mục cha để lấy toàn bộ sản phẩm của các danh mục con, cũng như việc giới hạn thuộc tính sản phẩm tùy theo danh mục đã chọn.

### Phân loại sản phẩm linh hoạt cho chiến dịch Marketing

Các sản phẩm trong kho đã có danh mục cố định, nhưng bộ phận Marketing muốn tạo ra các danh mục tạm thời hoặc danh mục ảo như "Quà tặng Valentine", "Deal hời cuối tuần" hoặc "Bộ sưu tập mùa hè". Một sản phẩm có thể thuộc về danh mục chính thống của kho và đồng thời nằm trong nhiều chiến dịch khác nhau. Bạn cần thiết kế hệ thống sao cho việc thêm hoặc xóa sản phẩm khỏi các danh mục chiến dịch này không ảnh hưởng đến cấu trúc phân loại gốc.

### Danh mục dựa trên đặc tính kỹ thuật và thuộc tính động

Ở các trang web bán linh kiện máy tính hoặc vật liệu xây dựng, mỗi danh mục lại đi kèm với một bộ thuộc tính hoàn toàn khác nhau. Ví dụ, danh mục Laptop cần các trường như RAM, CPU, trong khi danh mục Ổ cứng cần dung lượng và tốc độ đọc ghi. Bài toán đặt ra là làm sao để khi gán một sản phẩm vào danh mục, hệ thống sẽ tự động yêu cầu người dùng nhập đúng các thông số kỹ thuật tương ứng của danh mục đó để phục vụ bộ lọc tìm kiếm.

### Hệ thống gợi ý danh mục tự động bằng AI

Khi người bán đăng tải một sản phẩm mới với tên và mô tả thô, hệ thống cần gợi ý các danh mục phù hợp nhất để tiết kiệm thời gian. Bạn cần thiết kế một luồng xử lý dữ liệu nơi kết quả từ model AI được trả về dưới dạng danh sách các danh mục kèm theo điểm tin cậy. Người dùng có thể chấp nhận gợi ý hoặc chọn thủ công, và hệ thống cần lưu lại lịch sử thay đổi này để kiểm soát chất lượng dữ liệu.

### Phân loại sản phẩm theo khu vực địa lý và thị trường

Một chuỗi cửa hàng bán lẻ hoạt động trên nhiều quốc gia có danh mục sản phẩm khác nhau tùy theo văn hóa và ngôn ngữ. Sản phẩm A có thể nằm trong danh mục Thực phẩm tại quốc gia này nhưng thuộc danh mục Đồ uống tại quốc gia khác. Bài toán yêu cầu thiết kế hệ thống hỗ trợ đa ngôn ngữ cho tên danh mục và cho phép cấu hình hiển thị danh mục tùy biến theo mã vùng hoặc chi nhánh cửa hàng cụ thể.

### Quản lý danh mục cho hệ thống thực phẩm và Menu nhà hàng

Trong ngành F&B, một món ăn có thể xuất hiện trong nhiều phân loại như "Món khai vị", "Món đặc trưng" hoặc "Combo gia đình". Điểm đặc biệt là các danh mục này thường gắn liền với khung giờ bán hoặc thực đơn theo buổi. Bạn cần thiết kế làm sao để khi người dùng tìm kiếm theo danh mục vào buổi sáng, hệ thống chỉ hiển thị các danh mục và sản phẩm có hiệu lực trong khung giờ đó.

### Đồng bộ danh mục giữa kho tổng và các sàn Marketplace bên thứ ba

Khi bán hàng trên Shopee, Lazada hay Amazon, mỗi sàn lại có một bộ quy tắc danh mục riêng không khớp với danh mục của kho nội bộ. Bài toán là tạo ra một bảng ánh xạ (mapping) giữa danh mục nội bộ và danh mục của từng sàn. Khi sản phẩm được cập nhật ở kho chính, hệ thống phải tự động xác định sản phẩm đó sẽ rơi vào danh mục nào trên các sàn tương ứng để đẩy dữ liệu lên chính xác qua API.

### Hệ thống danh mục quyền hạn cho trang tin tức và nội dung số

Trên các trang báo điện tử hoặc nền tảng học trực tuyến, danh mục không chỉ dùng để điều hướng mà còn dùng để phân quyền truy cập. Một bài viết hoặc khóa học có thể thuộc danh mục "Miễn phí" hoặc "Premium". Việc thiết kế cần đảm bảo khi truy vấn danh mục, hệ thống phải kiểm tra được quyền của người dùng để ẩn hoặc hiện các nội dung tương ứng, đồng thời xử lý được các bài viết thuộc nhiều chủ đề khác nhau.

### Phân loại sản phẩm theo trạng thái vòng đời và tồn kho

Sản phẩm có thể được gán vào các danh mục đặc biệt dựa trên trạng thái kinh doanh như "Hàng mới về", "Hàng sắp hết" hoặc "Hàng thanh lý". Các danh mục này thường có tính chất thay đổi liên tục dựa trên số lượng tồn kho thực tế. Bạn cần thiết kế một cơ chế cập nhật tự động hoặc bán tự động để di chuyển sản phẩm giữa các nhóm này mà không làm gián đoạn trải nghiệm của khách hàng.

### Quản lý danh mục nhãn trắng cho hệ thống Dropshipping

Trong mô hình Dropshipping, một nhà cung cấp gốc chia sẻ danh mục sản phẩm cho hàng nghìn người bán lẻ. Mỗi người bán lại muốn đổi tên danh mục hoặc sắp xếp lại thứ tự ưu tiên theo ý thích cá nhân trên cửa hàng riêng của họ. Bài toán yêu cầu thiết kế một hệ thống quản lý danh mục gốc nhưng cho phép các bên bán lẻ ghi đè (override) thông tin hiển thị mà vẫn giữ nguyên liên kết dữ liệu với sản phẩm gốc của nhà cung cấp.
