# Address management

### Quản lý địa chỉ mặc định và phân loại mục đích sử dụng

Người dùng thường có nhiều địa chỉ khác nhau như nhà riêng, cơ quan hoặc nhà người thân. Hệ thống cần cho phép lưu trữ danh sách địa chỉ này nhưng phải phân biệt rõ địa chỉ nào dùng để nhận hàng và địa chỉ nào dùng để xuất hóa đơn tài chính. Thách thức ở đây là tại một thời điểm, chỉ được phép có duy nhất một địa chỉ được đánh dấu là mặc định cho mỗi loại mục đích. Khi người dùng chọn một địa chỉ mới làm mặc định, hệ thống phải tự động gỡ bỏ trạng thái mặc định của địa chỉ cũ để đảm bảo tính nhất nhất quán dữ liệu.

### Ràng buộc dữ liệu địa chính đa cấp

Để tránh việc người dùng nhập lung tung gây khó khăn cho đơn vị vận chuyển, hệ thống cần quản lý địa chỉ theo cấu trúc hình cây gồm Tỉnh/Thành phố, Quận/Huyện và Phường/Xã. Mỗi cấp hành chính sẽ có mã định danh riêng và phụ thuộc trực tiếp vào cấp trên nó. Khi thiết kế, bạn cần giải quyết vấn đề truy vấn nhanh danh sách các đơn vị hành chính con khi biết mã đơn vị cha và đảm bảo rằng một địa chỉ được lưu xuống phải khớp hoàn toàn với cơ sở dữ liệu địa chính chính thống đã định nghĩa sẵn.

### Lưu vết địa chỉ trong lịch sử đơn hàng

Một sai lầm phổ biến là chỉ lưu ID của địa chỉ vào bảng đơn hàng. Khi người dùng thay đổi hoặc xóa địa chỉ trong sổ địa chỉ cá nhân, các đơn hàng cũ đã giao sẽ bị sai lệch thông tin lịch sử. Bài toán đặt ra là làm thế nào để khi đơn hàng được tạo, thông tin địa chỉ tại thời điểm đó phải được đóng băng hoặc sao chép nguyên trạng vào đơn hàng. Điều này giúp bộ phận đối soát có thể xem lại chính xác địa điểm giao hàng trong quá khứ kể cả khi người dùng đã chuyển nhà hoặc cập nhật lại thông tin cá nhân.

### Tính toán phí giao hàng dựa trên tọa độ và khoảng cách

Ngoài việc lưu tên đường, hệ thống cần tích hợp tọa độ địa lý gồm vĩ độ và kinh độ cho mỗi địa chỉ. Khi người dùng chọn một địa chỉ giao hàng, hệ thống sẽ dựa vào tọa độ của kho hàng gần nhất để tính toán khoảng cách thực tế. Bài toán này yêu cầu bạn thiết kế cách lưu trữ dữ liệu không gian sao cho việc tìm kiếm các địa chỉ trong một bán kính nhất định hoặc tính toán phí ship theo km được thực hiện nhanh chóng, đặc biệt là trong các ứng dụng giao đồ ăn nhanh.

### Gợi ý địa chỉ thông minh dựa trên lịch sử và vị trí hiện tại

Để tối ưu trải nghiệm người dùng, hệ thống cần có khả năng gợi ý các địa chỉ mà người dùng thường xuyên sử dụng nhất hoặc các địa chỉ gần với vị trí GPS hiện tại của họ. Bạn cần thiết kế cấu trúc dữ liệu để lưu lại tần suất sử dụng của từng địa chỉ và thời gian sử dụng gần nhất. Khi người dùng mở màn hình thanh toán, hệ thống sẽ tự động đưa ra danh sách ưu tiên giúp họ hoàn tất thao tác chỉ với một lần chạm thay vì phải cuộn qua danh sách dài các địa chỉ cũ.

### Quản lý địa chỉ cho mô hình doanh nghiệp B2B

Khác với người dùng cá nhân, một khách hàng doanh nghiệp có thể có cấu trúc phân cấp phức tạp như Tổng công ty, các Chi nhánh và các kho bãi con. Mỗi chi nhánh lại có danh sách địa chỉ nhận hàng riêng nhưng chung một địa chỉ xuất hóa đơn của trụ sở chính. Bài toán yêu cầu thiết kế hệ thống phân quyền sao cho nhân viên của chi nhánh A chỉ thấy và chọn được địa chỉ của chi nhánh A, trong khi quản lý cấp cao có thể quản lý toàn bộ sổ địa chỉ của tất cả các chi nhánh thuộc tập đoàn.

### Chuẩn hóa địa chỉ quốc tế và định dạng vùng miền

Khi hệ thống mở rộng ra nhiều quốc gia, cấu trúc địa chỉ không còn đơn thuần là Tỉnh hay Quận. Mỗi quốc gia có định dạng khác nhau như mã Zip code, Bang, hoặc số hòm thư bưu điện. Bài toán này đòi hỏi thiết kế một cấu trúc dữ liệu linh hoạt (Dynamic Schema) hoặc sử dụng các cột mở rộng để có thể lưu trữ mọi loại định dạng địa chỉ trên thế giới mà không cần phải thay đổi cấu trúc bảng liên tục mỗi khi mở rộng thị trường sang một nước mới.

### Kiểm soát giới hạn và ngăn chặn rác dữ liệu địa chỉ

Trong các chương trình khuyến mãi cho người dùng mới, nhiều đối tượng có thể tạo hàng loạt địa chỉ ảo hoặc trùng lặp để trục lợi. Hệ thống cần có cơ chế kiểm soát số lượng địa chỉ tối đa một tài khoản được phép lưu trữ và cơ chế nhận diện các địa chỉ trùng lặp (ví dụ: cùng số nhà, tên đường nhưng viết khác cách định dạng). Bạn cần thiết kế các ràng buộc ở mức database hoặc logic ở API để đảm bảo dữ liệu luôn sạch và ngăn chặn các hành vi spam làm tràn ngập hệ thống.
