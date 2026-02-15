# Heatmap tracking

### Thu thập và nén tọa độ click của người dùng theo thời gian thực

Mỗi khi người dùng nhấp chuột vào bất kỳ vị trí nào trên trang web, hệ thống cần ghi lại tọa độ X và Y tương đối so với kích thước khung hình cùng với định danh của phần tử bị tác động. Thách thức ở đây là số lượng người dùng có thể lên tới hàng triệu, tạo ra hàng tỷ sự kiện nhấp chuột. Bạn cần thiết kế một hệ thống tiếp nhận dữ liệu có khả năng chịu tải cao và cấu trúc lưu trữ sao cho tiết kiệm dung lượng bộ nhớ nhưng vẫn đảm bảo truy xuất nhanh để vẽ lại bản đồ mật độ nhấp chuột.

### Theo dõi độ sâu cuộn trang để xác định điểm rơi nội dung

Trong các trang báo điện tử hoặc trang giới thiệu sản phẩm dài, việc biết người dùng dừng lại ở đâu là rất quan trọng. Bài toán yêu cầu ghi lại tỷ lệ phần trăm chiều dài trang mà người dùng đã cuộn qua. Hệ thống phải ghi nhận các mốc thời gian và vị trí cuộn để xác định xem nội dung nào được xem nhiều nhất và tại vị trí nào thì người dùng bắt đầu thoát trang. Dữ liệu này giúp bộ phận thiết kế biết được nên đặt các nút kêu gọi hành động ở vị trí nào để đạt hiệu quả cao nhất.

### Ghi vết di chuyển chuột để dự đoán sự chú ý của người dùng

Khác với hành động nhấp chuột, việc di chuyển chuột diễn ra liên tục và tạo ra lượng dữ liệu khổng lồ. Bài toán đặt ra là làm thế nào để lấy mẫu dữ liệu di chuyển chuột một cách thông minh, ví dụ cứ mỗi 100 mil giây lấy một điểm tọa độ, để tái hiện lại luồng chú ý của mắt người dùng. Hệ thống cần phân biệt được các vùng người dùng rê chuột qua nhanh và những vùng họ dừng lại lâu để tô màu bản đồ nhiệt tương ứng với mức độ quan tâm.

### Phân tích heatmap theo các loại thiết bị và độ phân giải màn hình

Một trang web hiển thị trên máy tính để bàn sẽ có bố cục khác hoàn toàn so với trên điện thoại di động do cơ chế phản hồi giao diện. Bài toán yêu cầu hệ thống phải phân loại dữ liệu tương tác theo loại thiết bị, hệ điều hành và kích thước trình duyệt. Khi truy vấn dữ liệu để vẽ heatmap, bạn phải lọc và nhóm các tọa độ sao cho chúng khớp với đúng phiên bản giao diện mà người dùng đã trải nghiệm, tránh việc chồng chéo dữ liệu của di động lên bản đồ của máy tính.

### Theo dõi tương tác trên các phần tử động như menu thả xuống và cửa sổ bật lên

Các hệ thống heatmap cơ bản thường chỉ chụp ảnh màn hình tĩnh, nhưng trang web hiện đại có rất nhiều thành phần động. Bài toán là làm sao để ghi nhận hành vi click hoặc hover vào một phần tử chỉ xuất hiện khi người dùng thực hiện một thao tác nhất định, ví dụ như menu đa cấp hoặc modal thông báo. Bạn cần thiết kế database để lưu trữ trạng thái của giao diện tại thời điểm tương tác diễn ra nhằm tái hiện chính xác vị trí của phần tử đó trên bản đồ nhiệt.

### Quản lý phiên làm việc và bảo mật thông tin cá nhân trong heatmap

Để phân tích hành trình người dùng, hệ thống cần nhóm các tương tác theo phiên làm việc. Tuy nhiên, một vấn đề lớn là bảo mật dữ liệu. Bài toán yêu cầu bạn thiết kế hệ thống sao cho vẫn theo dõi được hành vi nhưng phải tự động loại bỏ hoặc che khuất các thông tin nhạy cảm như nội dung người dùng nhập vào ô mật khẩu, số thẻ tín dụng hoặc thông tin cá nhân hiển thị trên màn hình. Việc thiết kế API và Database phải đảm bảo tính ẩn danh nhưng vẫn giữ được giá trị phân tích UX.

### So sánh hiệu quả giữa hai phiên bản giao diện bằng bản đồ nhiệt

Trong các chiến dịch thử nghiệm phân tách, một nửa người dùng thấy giao diện phiên bản A và nửa còn lại thấy phiên bản B. Bài toán yêu cầu hệ thống heatmap phải hỗ trợ việc so sánh trực quan giữa hai phiên bản này. Bạn cần thiết kế hệ thống gắn thẻ cho các sự kiện tương tác tương ứng với từng phiên bản thử nghiệm, từ đó tính toán và hiển thị hai bản đồ nhiệt cạnh nhau để người quản lý sản phẩm thấy được phiên bản nào có tỷ lệ tương tác tốt hơn.

### Tích hợp bản đồ nhiệt với phễu chuyển đổi và sự kiện thanh toán

Mục tiêu cuối cùng của việc theo dõi hành vi là thúc đẩy chuyển đổi. Bài toán đặt ra là kết nối dữ liệu heatmap với các sự kiện kinh doanh như thêm vào giỏ hàng hoặc hoàn tất đơn hàng. Bạn cần thiết kế hệ thống sao cho khi xem heatmap của một trang, bạn có thể lọc để chỉ xem hành vi của những người dùng đã thực hiện mua hàng thành công. Điều này giúp nhận diện những điểm chạm quan trọng dẫn đến quyết định mua sắm của khách hàng.
