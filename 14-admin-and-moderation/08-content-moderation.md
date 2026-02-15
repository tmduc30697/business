# Content moderation

### Hệ thống hàng đợi phê duyệt nội dung theo phân cấp

Trên một trang thương mại điện tử, khi người bán thay đổi mô tả sản phẩm hoặc tải lên banner quảng cáo mới, các nội dung này không được hiển thị ngay lập tức. Hệ thống cần đưa các yêu cầu này vào một hàng đợi phê duyệt để đội ngũ quản trị viên kiểm tra thủ công. Bài toán yêu cầu thiết kế trạng thái của nội dung từ lúc chờ duyệt, đang duyệt, đã từ chối cho đến khi được xuất bản, đồng thời phải lưu lại dấu vết ai là người đã phê duyệt và lý do nếu nội dung bị từ chối.

### Cơ chế tự động chặn từ khóa nhạy cảm trong khung chat

Trong hệ thống chat trực tuyến giữa người mua và người bán, hệ thống cần ngăn chặn việc chia sẻ số điện thoại, link website ngoài hoặc các từ ngữ thô tục ngay thời điểm tin nhắn được gửi đi. Bài toán này đòi hỏi việc quản lý một danh mục từ điển các từ khóa bị cấm và khả năng kiểm tra cực nhanh để không làm gián đoạn trải nghiệm trò chuyện. Bạn cần thiết kế cách lưu trữ từ điển sao cho dễ dàng cập nhật mà không làm ảnh hưởng đến hiệu suất của API nhắn tin.

### Kiểm duyệt đánh giá sản phẩm có kèm hình ảnh và video

Người dùng sau khi mua hàng thường để lại review bao gồm cả văn bản, hình ảnh thực tế và video clip ngắn. Hệ thống kiểm duyệt không chỉ xử lý phần chữ mà còn phải gửi các tệp đa phương tiện này sang một dịch vụ AI bên thứ ba để nhận diện hình ảnh nhạy cảm hoặc không phù hợp. Sau khi có kết quả từ AI, hệ thống cần cập nhật lại trạng thái của từng tệp tin và quyết định xem toàn bộ bài đánh giá đó có được hiển thị lên trang sản phẩm hay không.

### Quản lý báo cáo vi phạm từ phía người dùng cộng đồng

Hệ thống cho phép người dùng phổ thông báo cáo một nội dung bất kỳ mà họ cho là vi phạm tiêu chuẩn cộng đồng. Bài toán đặt ra là phải thiết kế cơ chế tiếp nhận báo cáo, gom nhóm các báo cáo trùng lặp về cùng một nội dung để tránh làm quá tải đội ngũ kiểm duyệt. Hệ thống cần lưu trữ thông tin người báo cáo, loại vi phạm, bằng chứng đi kèm và phản hồi cuối cùng của hệ thống sau khi đã xử lý báo cáo đó để thông báo lại cho người dùng.

### Hệ thống tin tưởng người dùng và tự động phê duyệt

Để giảm bớt khối lượng công việc cho quản trị viên, hệ thống áp dụng cơ chế chấm điểm uy tín cho người dùng. Những người dùng có lịch sử hoạt động tốt, chưa từng bị cảnh báo hoặc xóa bài sẽ được xếp vào nhóm tin cậy và nội dung của họ sẽ được tự động xuất bản ngay lập tức. Ngược lại, những người dùng mới hoặc từng vi phạm sẽ bị kiểm soát chặt chẽ hơn. Điều này yêu cầu thiết kế database phải theo dõi được hành vi và lịch sử vi phạm của từng định danh người dùng.

### Lưu trữ và quản lý các phiên bản nội dung sau khi chỉnh sửa

Khi một mô tả sản phẩm bị từ chối do vi phạm, người bán sẽ tiến hành chỉnh sửa và gửi duyệt lại. Hệ thống cần lưu trữ lại toàn bộ lịch sử các phiên bản nội dung khác nhau để người kiểm duyệt có thể so sánh sự thay đổi giữa bản cũ và bản mới. Bài toán này tập trung vào việc thiết kế cấu trúc dữ liệu để quản lý phiên bản (versioning) sao cho hiệu quả, tránh việc phình to dữ liệu nhưng vẫn đảm bảo khả năng truy xuất lại lịch sử khi cần đối soát.

### Xử lý hậu kiểm nội dung bằng phương pháp lấy mẫu ngẫu nhiên

Đối với các hệ thống có lượng dữ liệu khổng lồ như bình luận dưới bài viết, việc kiểm duyệt 100% là bất khả thi. Hệ thống áp dụng chiến lược hậu kiểm bằng cách lấy mẫu ngẫu nhiên một tỷ lệ phần trăm nhất định các nội dung đã được xuất bản để quản trị viên rà soát lại. Nếu phát hiện vi phạm ở khâu hậu kiểm, nội dung sẽ bị gỡ bỏ và người dùng sẽ bị xử lý. Bài toán này yêu cầu thiết kế logic chọn mẫu và quy trình xử lý đơn hàng/nội dung đã ở trạng thái hoạt động.

### Cơ chế kháng cáo và xử lý tranh chấp nội dung bị khóa

Khi một nội dung bị hệ thống hoặc quản trị viên khóa, người dùng có quyền gửi đơn kháng cáo nếu họ cho rằng đó là sự nhầm lẫn. Hệ thống cần một quy trình làm việc riêng để xử lý các đơn kháng cáo này, bao gồm việc mở lại phiên làm việc với nội dung cũ, cho phép người dùng bổ sung giải trình và người kiểm duyệt cấp cao hơn sẽ đưa ra quyết định cuối cùng. Đây là bài toán về workflow phức tạp kết nối giữa người dùng cuối và nhiều cấp bậc quản trị.
