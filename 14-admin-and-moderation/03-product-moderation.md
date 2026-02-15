# Product moderation

### Quy trình kiểm duyệt tiền kiểm cho người bán mới

Khi một người bán mới đăng tải sản phẩm lần đầu tiên, hệ thống không cho phép sản phẩm hiển thị ngay lập tức trên sàn. Sản phẩm sẽ rơi vào một hàng đợi kiểm duyệt ở trạng thái chờ. Nhân viên kiểm duyệt nội dung sẽ kiểm tra hình ảnh, mô tả và danh mục sản phẩm xem có vi phạm chính sách hay không. Chỉ khi nhân viên nhấn phê duyệt thì trạng thái sản phẩm mới chuyển sang hiển thị công khai. Nếu bị từ chối, người bán phải nhận được lý do cụ thể để chỉnh sửa và gửi yêu cầu kiểm duyệt lại từ đầu.

### Cơ chế hậu kiểm dựa trên báo cáo vi phạm từ cộng đồng

Sản phẩm đã được đăng tải và đang bán bình thường nhưng có thể bị người mua báo cáo là hàng giả hoặc hình ảnh gây phản cảm. Hệ thống cần một cơ chế tiếp nhận các báo cáo này và tự động tạm ẩn sản phẩm nếu số lượng báo cáo vượt quá một ngưỡng nhất định trong một khoảng thời gian ngắn. Sau đó, một phiếu ghi kiểm duyệt sẽ được tạo ra để điều tra viên vào cuộc. Kết quả kiểm duyệt cuối cùng có thể là gỡ bỏ vĩnh viễn sản phẩm hoặc khôi phục lại trạng thái hiển thị nếu báo cáo là sai sự thật.

### Kiểm duyệt tự động bằng bộ lọc từ khóa và AI

Để giảm tải cho con người, hệ thống áp dụng một lớp kiểm duyệt tự động ngay khi người bán nhấn nút đăng bài. Bộ lọc sẽ quét qua tiêu đề và mô tả sản phẩm để tìm các từ khóa cấm, số điện thoại rác hoặc các liên kết dẫn ra ngoài sàn. Nếu phát hiện vi phạm ở mức độ nhẹ, hệ thống sẽ cảnh báo người bán chỉnh sửa ngay. Nếu vi phạm nặng như buôn bán chất cấm, hệ thống sẽ tự động khóa sản phẩm và đánh dấu tài khoản người bán để theo dõi đặc biệt.

### Quản lý phiên bản sản phẩm trong quá trình kiểm duyệt

Một bài toán khó là khi sản phẩm đang được bán công khai, người bán thực hiện cập nhật giá hoặc thay đổi mô tả. Hệ thống cần quyết định xem có cho phép hiển thị nội dung mới ngay lập tức hay phải giữ nguyên phiên bản cũ để chờ kiểm duyệt nội dung mới. Điều này yêu cầu thiết kế cơ sở dữ liệu có khả năng lưu trữ nhiều phiên bản của cùng một sản phẩm, trong đó một phiên bản đang hiển thị cho khách hàng và một phiên bản đang nằm trong hàng đợi kiểm duyệt.

### Hệ thống phân bổ phiếu ghi cho nhân viên kiểm duyệt

Trong một sàn thương mại lớn với hàng triệu sản phẩm, việc phân bổ công việc cho đội ngũ nhân viên kiểm duyệt cần sự tối ưu. Phiếu ghi kiểm duyệt cần được đẩy vào các hàng đợi dựa trên loại mặt hàng hoặc ngôn ngữ. Ví dụ, nhân viên am hiểu về điện tử sẽ ưu tiên duyệt các sản phẩm công nghệ. Hệ thống cũng cần ghi lại thời gian xử lý của từng nhân viên và đảm bảo một phiếu ghi không bị hai nhân viên cùng xử lý một lúc để tránh xung đột dữ liệu.

### Kiểm duyệt hàng loạt và xử lý theo chiến dịch

Vào các dịp lễ hoặc chiến dịch giảm giá, số lượng sản phẩm đăng mới tăng đột biến. Hệ thống cần hỗ trợ tính năng cho phép kiểm duyệt viên chọn nhiều sản phẩm cùng lúc để phê duyệt hoặc từ chối theo danh sách. Bài toán này đặt ra thách thức về hiệu năng khi cập nhật trạng thái hàng loạt trong cơ sở dữ liệu và việc gửi thông báo đồng loạt cho người bán mà không làm nghẽn hệ thống xử lý ngầm.

### Thiết lập mức độ tin cậy cho người bán để miễn kiểm duyệt

Để tối ưu nguồn lực, hệ thống xây dựng một chỉ số tin cậy cho người bán dựa trên lịch sử hoạt động. Những người bán có tỷ lệ sản phẩm vi phạm thấp và doanh số cao sẽ được đưa vào danh sách trắng. Sản phẩm của họ khi đăng tải sẽ được tự động chuyển sang trạng thái hiển thị mà không cần qua bước kiểm duyệt thủ công. Tuy nhiên, hệ thống vẫn thực hiện kiểm tra xác suất ngẫu nhiên để đảm bảo người bán không lợi dụng quyền ưu tiên này để đăng hàng kém chất lượng.

### Lưu vết lịch sử và bằng chứng kiểm duyệt phục vụ khiếu nại

Mọi hành động phê duyệt hoặc từ chối đều phải được lưu lại lịch sử chi tiết bao gồm người thực hiện, thời gian, trạng thái trước và sau khi thay đổi, cùng hình ảnh bằng chứng tại thời điểm đó. Điều này cực kỳ quan trọng khi người bán thực hiện khiếu nại về việc sản phẩm bị gỡ bỏ oan sai. Hệ thống cần một bảng lưu trữ nhật ký kiểm duyệt có khả năng truy vấn nhanh và không được phép chỉnh sửa để đảm bảo tính minh bạch và phục vụ công tác thanh tra nội bộ.
