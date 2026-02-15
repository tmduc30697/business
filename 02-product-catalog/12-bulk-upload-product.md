# Bulk upload product

### Xử lý dữ liệu không đồng nhất từ nhiều nhà cung cấp

Trong mô hình sàn thương mại điện tử, mỗi nhà cung cấp thường gửi file sản phẩm với định dạng cột và quy ước đặt tên khác nhau. Bài toán đặt ra là làm thế nào để xây dựng một hệ thống trung gian có khả năng cho phép người dùng tự định nghĩa ánh xạ các cột từ file Excel của họ vào đúng các trường thông tin trong cơ sở dữ liệu của hệ thống. Bạn cần giải quyết việc lưu trữ cấu hình ánh xạ này cho từng nhà cung cấp để những lần upload sau diễn ra tự động.

### Kiểm soát dữ liệu lỗi và phản hồi chi tiết cho người dùng

Khi người dùng upload một file chứa hàng nghìn sản phẩm, việc file dừng lại ngay khi gặp một dòng lỗi sẽ gây ức chế. Bài toán yêu cầu hệ thống phải thực hiện kiểm tra tính hợp lệ của toàn bộ file, sau đó trả về một báo cáo chi tiết chỉ rõ dòng nào bị lỗi, cột nào sai định dạng và lý do cụ thể là gì. Thách thức ở đây là thiết kế quy trình xử lý sao cho người dùng có thể tải về chính file lỗi đó, sửa nhanh và upload lại mà không bị trùng lặp những dòng đã thành công.

### Quản lý phiên bản và lịch sử các lần cập nhật hàng loạt

Hệ thống cần lưu lại vết của mọi đợt bulk upload để quản trị viên có thể theo dõi ai đã upload file nào vào thời điểm nào. Trong trường hợp dữ liệu mới upload làm sai lệch giá hoặc thông tin sản phẩm trên diện rộng, hệ thống phải cung cấp cơ chế cho phép hoàn tác toàn bộ các thay đổi của một phiên bản upload cụ thể để đưa dữ liệu sản phẩm quay trở về trạng thái trước khi thực hiện lệnh đó.

### Xử lý tải lên hình ảnh đi kèm qua đường dẫn URL

Thay vì chỉ upload thông tin văn bản, file bulk thường chứa các cột là đường dẫn URL dẫn đến hình ảnh sản phẩm được lưu trữ ở nơi khác. Bài toán thực tế là hệ thống sau khi đọc file phải kích hoạt các tiến trình chạy ngầm để tải các hình ảnh này về, kiểm tra kích thước, nén ảnh, tạo các bản thu nhỏ và lưu trữ vào kho chứa của hệ thống. Bạn cần xử lý trạng thái hiển thị của sản phẩm khi hình ảnh vẫn đang trong quá trình được xử lý.

### Cập nhật tồn kho và giá theo thời gian thực từ API bên thứ ba

Nhiều doanh nghiệp sử dụng phần mềm quản lý kho riêng và muốn đồng bộ dữ liệu sang trang bán hàng thông qua API bulk update. Bài toán là thiết kế một endpoint API có khả năng tiếp nhận hàng loạt ID sản phẩm kèm theo số lượng tồn kho mới với tần suất cao. Hệ thống phải đảm bảo việc cập nhật này không gây ra tình trạng khóa bảng dữ liệu quá lâu, ảnh hưởng đến việc khách hàng đang đặt mua sản phẩm đó trên giao diện web.

### Phân loại sản phẩm và thuộc tính động theo danh mục

Mỗi danh mục sản phẩm như điện tử, thời trang hay thực phẩm đều có các thuộc tính đặc thù khác nhau. Khi upload qua file, hệ thống phải tự động nhận diện danh mục để kiểm tra xem các thuộc tính bắt buộc đi kèm có đầy đủ hay không. Việc thiết kế cơ sở dữ liệu sao cho có thể lưu trữ linh hoạt hàng trăm loại thuộc tính khác nhau mà không phải thay đổi cấu trúc bảng mỗi khi thêm ngành hàng mới là một thử thách trọng tâm.

### Xử lý xung đột dữ liệu khi nhiều người cùng upload

Trong một doanh nghiệp lớn, có thể xảy ra tình huống hai nhân viên cùng thực hiện cập nhật giá cho cùng một danh sách sản phẩm thông qua hai file khác nhau tại cùng một thời điểm. Bài toán yêu cầu thiết kế cơ chế khóa bản ghi hoặc sử dụng hàng đợi để đảm bảo tính toàn vẹn dữ liệu, tránh tình trạng dữ liệu cuối cùng trong cơ sở dữ liệu là sự pha trộn không nhất quán giữa hai phiên bản file.

### Hệ thống hàng đợi và thông báo trạng thái xử lý thời gian thực

Việc xử lý một file Excel có hàng chục nghìn dòng không thể diễn ra tức thời trong một request HTTP thông thường vì sẽ gây ra lỗi hết thời gian chờ. Bạn cần thiết kế một kiến trúc sử dụng hàng đợi tin nhắn để xử lý file dưới nền. Bài toán đặt ra là làm thế nào để giao diện người dùng có thể cập nhật tiến độ xử lý theo phần trăm và thông báo ngay lập tức cho người dùng thông qua trình duyệt khi toàn bộ tiến trình đã hoàn tất.

### Tự động phân tách và xử lý song song các tệp dữ liệu lớn

Để tối ưu hóa tốc độ khi gặp các tệp dữ liệu cực lớn, hệ thống cần có khả năng tự động chia nhỏ một file chính thành nhiều phần nhỏ hơn và phân phối chúng cho nhiều máy chủ xử lý cùng lúc. Bài toán này đòi hỏi việc quản lý trạng thái của từng phần nhỏ và tổng hợp kết quả cuối cùng sao cho chính xác, đảm bảo rằng nếu một máy chủ gặp sự cố thì phần dữ liệu đó sẽ được phân phối lại cho máy chủ khác.

### Ràng buộc dữ liệu phức tạp giữa các bảng liên quan

Một sản phẩm khi upload không chỉ đứng đơn lẻ mà còn liên quan đến thương hiệu, kho hàng, chương trình khuyến mãi và các biến thể sản phẩm như màu sắc, kích cỡ. Bài toán yêu cầu khi xử lý file bulk, hệ thống phải kiểm tra sự tồn tại của các khóa ngoại này trong cơ sở dữ liệu. Nếu thương hiệu hoặc màu sắc đó chưa tồn tại, hệ thống cần có cơ chế tự động khởi tạo mới hoặc từ chối dòng dữ liệu đó dựa trên cấu hình thiết lập trước của người dùng.
