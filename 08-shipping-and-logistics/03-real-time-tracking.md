# Real-time tracking

### Quản lý hành trình đa chặng qua các kho trung chuyển

Bài toán này tập trung vào việc theo dõi một kiện hàng đi qua nhiều điểm dừng khác nhau từ kho người gửi đến kho phân loại, kho trung tâm và cuối cùng là kho giao hàng. Bạn cần xử lý việc ghi nhận thời điểm kiện hàng "nhập kho" và "xuất kho" tại mỗi điểm, đồng thời tính toán thời gian lưu kho dự kiến. Việc thiết kế database phải đảm bảo lưu trữ được lịch sử chi tiết các trạng thái để người dùng biết chính xác kiện hàng đang nằm ở phân đoạn nào trong chuỗi cung ứng.

### Đồng bộ trạng thái vận chuyển từ nhiều đơn vị vận chuyển thứ ba

Trong thực tế, một sàn thương mại điện tử thường hợp tác với nhiều đối tác logistics khác nhau như GHTK, GHN, hay Viettel Post. Mỗi đối tác lại có một bảng mã trạng thái và hệ thống webhook khác nhau. Bài toán đặt ra là làm thế nào để thiết kế một hệ thống trung gian có khả năng tiếp nhận dữ liệu từ nhiều nguồn, chuẩn hóa các trạng thái này về một chuẩn chung của hệ thống mình và cập nhật ngay lập tức cho khách hàng mà không làm nghẽn hệ thống khi có lượng lớn dữ liệu đổ về cùng lúc.

### Theo dõi vị trí tài xế trên bản đồ theo thời gian thực

Đây là bài toán điển hình cho các ứng dụng giao đồ ăn hoặc gọi xe, nơi vị trí tọa độ của tài xế cần được cập nhật liên tục mỗi vài giây. Bạn cần giải quyết vấn đề lưu trữ dữ liệu tọa độ thay đổi nhanh chóng, cách truy vấn vị trí mới nhất để hiển thị trên bản đồ phía người dùng và cách tối ưu hóa băng thông truyền tải giữa thiết bị tài xế và máy chủ. Ngoài ra, việc lưu lại vết đường đi để vẽ lại hành trình sau khi đơn hàng hoàn tất cũng là một điểm quan trọng cần lưu ý.

### Hệ thống cảnh báo và xử lý sự cố vận chuyển tự động

Không phải đơn hàng nào cũng đi đúng lộ trình dự kiến. Bài toán này yêu cầu hệ thống phải tự động phát hiện các bất thường dựa trên dữ liệu thời gian thực, ví dụ như một kiện hàng đứng yên tại một kho quá 24 giờ hoặc tài xế đi chệch khỏi tuyến đường quy định. Bạn cần thiết kế cơ chế kích hoạt các thông báo đẩy hoặc email cho bộ phận vận hành để xử lý kịp thời, đòi hỏi sự phối hợp chặt chẽ giữa dữ liệu tracking và logic nghiệp vụ kiểm soát thời gian.

### Tính toán thời gian giao hàng dự kiến linh hoạt

Dựa trên dữ liệu vận chuyển thực tế và tình trạng giao thông hoặc thời tiết, hệ thống cần cập nhật lại thời gian giao hàng dự kiến thay vì chỉ đưa ra một con số cố định lúc đặt hàng. Bài toán này đòi hỏi bạn thiết kế database sao cho có thể so sánh giữa thời gian cam kết ban đầu và thời gian thực tế đang diễn ra, từ đó đưa ra các điều chỉnh về mặt hiển thị để khách hàng luôn có kỳ vọng chính xác nhất về thời điểm nhận hàng.

### Quản lý bằng chứng giao hàng bằng hình ảnh và chữ ký số

Một phần quan trọng của trạng thái giao hàng thực tế là bằng chứng xác nhận đã giao thành công. Bài toán yêu cầu hệ thống phải đính kèm được các tệp tin phương tiện như ảnh chụp kiện hàng tại cửa nhà khách hàng hoặc chữ ký điện tử của người nhận vào bản ghi trạng thái cuối cùng. Bạn cần cân nhắc cách tổ chức lưu trữ các tệp tin này sao cho việc truy xuất từ API diễn ra nhanh chóng và đảm bảo tính toàn vẹn, không thể sửa đổi sau khi đã xác nhận giao hàng.

### Phân quyền và bảo mật dữ liệu hành trình đơn hàng

Thông tin vận chuyển chứa nhiều dữ liệu nhạy cảm như số điện thoại, địa chỉ cụ thể và lộ trình di chuyển của tài xế. Bài toán đặt ra là thiết kế một hệ thống phân quyền sao cho khách hàng chỉ thấy được lộ trình của đơn hàng mình mua, tài xế chỉ thấy thông tin các đơn mình đang giao, và người quản lý kho chỉ thấy dữ liệu các đơn đi qua kho đó. Việc thiết kế API và cơ sở dữ liệu phải đảm bảo kiểm soát truy cập chặt chẽ ở mức bản ghi để tránh rò rỉ thông tin cá nhân.

### Tối ưu hóa truy vấn lịch sử vận chuyển cho hàng triệu đơn hàng

Khi hệ thống phát triển lớn, bảng lưu trữ lịch sử tracking sẽ tăng trưởng cực kỳ nhanh chóng với hàng tỷ bản ghi. Bài toán thực tế ở đây là làm sao để thiết kế cấu trúc bảng và đánh chỉ mục sao cho việc truy vấn lịch sử của một đơn hàng cụ thể vẫn diễn ra trong vài mili giây, đồng thời việc ghi thêm dữ liệu mới từ các đối tác logistics không bị chậm trễ. Bạn cũng cần tính đến phương án lưu trữ dữ liệu cũ vào các kho lưu trữ lâu dài để giảm tải cho cơ sở dữ liệu chính.
