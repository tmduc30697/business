# Product approval workflow

### Chế độ kiểm duyệt hậu kiểm cho người bán uy tín

Trong một sàn thương mại điện tử lớn, việc bắt mọi sản phẩm đều phải chờ duyệt sẽ làm chậm tốc độ đăng bán. Hệ thống cần phân loại người bán dựa trên điểm uy tín. Những người bán có điểm cao sẽ được áp dụng cơ chế hậu kiểm, nghĩa là sản phẩm hiện công khai ngay lập tức nhưng vẫn được đưa vào hàng đợi để admin kiểm tra sau. Ngược lại, người bán mới hoặc có lịch sử vi phạm phải trải qua tiền kiểm, tức là sản phẩm ở trạng thái chờ cho đến khi có quyết định của admin. Bài toán này đòi hỏi việc quản lý trạng thái hiển thị song song với trạng thái phê duyệt.

### Quy trình duyệt đa cấp cho sản phẩm giá trị cao

Đối với các mặt hàng đặc thù như bất động sản hoặc xe hơi, một lần duyệt là không đủ để đảm bảo tính pháp lý. Quy trình yêu cầu tối thiểu hai cấp phê duyệt: cấp một là nhân viên thẩm định nội dung hình ảnh, cấp hai là quản lý kiểm tra giấy tờ pháp lý kèm theo. Sản phẩm chỉ được hiển thị công khai khi cả hai cấp đều nhấn phê duyệt. Nếu bất kỳ cấp nào từ chối, quy trình sẽ kết thúc và gửi thông báo lý do cụ thể cho người dùng. Điều này yêu cầu thiết kế workflow động và lưu vết lịch sử phê duyệt qua từng cấp.

### Cập nhật phiên bản và bảo toàn dữ liệu đang hiển thị

Khi một sản phẩm đang được bán công khai, người bán có nhu cầu cập nhật giá hoặc mô tả mới. Tuy nhiên, những thay đổi này không được đè trực tiếp lên dữ liệu cũ ngay lập tức vì cần chờ admin duyệt thông tin mới. Hệ thống phải duy trì đồng thời phiên bản cũ đang hiển thị cho khách hàng và phiên bản nháp đang chờ duyệt. Sau khi admin phê duyệt bản nháp, dữ liệu mới chính thức được cập nhật vào bản ghi chính và phiên bản cũ sẽ được lưu vào lịch sử để đối soát khi có tranh chấp xảy ra.

### Tự động hóa kiểm duyệt bằng AI và từ khóa cấm

Để giảm tải cho nhân sự, hệ thống cần tích hợp một lớp lọc tự động trước khi chuyển đến tay admin. Khi người dùng nhấn gửi duyệt, hệ thống sẽ tự động quét qua danh sách từ khóa cấm hoặc sử dụng API nhận diện hình ảnh để phát hiện nội dung nhạy cảm. Nếu tỷ lệ vi phạm thấp, sản phẩm được chuyển vào hàng đợi của admin. Nếu vi phạm nghiêm trọng, hệ thống tự động từ chối và khóa tài khoản người bán mà không cần sự can thiệp của con người. Bài toán này tập trung vào việc thiết kế các service trung gian và xử lý bất đồng bộ.

### Quản lý hàng đợi phê duyệt theo mức độ ưu tiên

Trong các đợt khuyến mãi lớn, lượng sản phẩm đẩy lên chờ duyệt tăng đột biến gây nghẽn hệ thống. Cần thiết kế một cơ chế hàng đợi thông minh, trong đó các sản phẩm thuộc gói dịch vụ trả phí hoặc của các nhãn hàng đối tác chiến lược sẽ được đẩy lên đầu danh sách ưu tiên để admin duyệt trước. Các sản phẩm thông thường sẽ được xếp hàng theo thời gian gửi. Admin sẽ nhận được các nhiệm vụ phê duyệt theo cơ chế phân bổ tự động để tránh việc nhiều admin cùng duyệt một sản phẩm một lúc.

### Phê duyệt chỉnh sửa hình ảnh và bản quyền thương hiệu

Một số sàn giao dịch yêu cầu hình ảnh sản phẩm phải đồng nhất về phông nền hoặc không có logo của đối thủ cạnh tranh. Khi người bán đăng ảnh, admin có quyền yêu cầu người bán chỉnh sửa lại chỉ riêng phần hình ảnh mà không cần bắt họ nhập lại thông tin văn bản. Hệ thống cần ghi nhận trạng thái phê duyệt riêng lẻ cho từng thuộc tính của sản phẩm thay vì chỉ phê duyệt toàn bộ. Người bán sẽ nhận được danh sách các mục cụ thể cần sửa đổi và chỉ khi tất cả các mục đạt yêu cầu thì sản phẩm mới được kích hoạt.

### Tạm ẩn và thu hồi quyền hiển thị sản phẩm

Sau khi sản phẩm đã được duyệt và công khai, nếu có báo cáo vi phạm từ người tiêu dùng hoặc phát hiện hàng giả, admin cần có công cụ để thu hồi quyền hiển thị ngay lập tức. Bài toán đặt ra là khi một sản phẩm bị gỡ bỏ, hệ thống phải xử lý các liên kết liên quan như các đơn hàng đang chờ xử lý hoặc các chiến dịch quảng cáo đang chạy. Admin cần để lại lý do thu hồi và người bán có quyền khiếu nại để mở lại quy trình duyệt lại từ đầu mà không cần tạo mới sản phẩm.

### Theo dõi hiệu suất và nhật ký hoạt động của Admin

Để đảm bảo tính minh bạch và tối ưu quy trình vận hành, hệ thống cần một cơ chế ghi lại chi tiết mọi thao tác của admin bao gồm thời gian tiếp nhận yêu cầu, thời gian ra quyết định, và các ghi chú nội bộ. Quản trị viên cấp cao có thể xem báo cáo về số lượng sản phẩm mỗi admin đã duyệt trong ngày và tỷ lệ sai sót. Việc này đòi hỏi một thiết kế database cho phần Logging và Audit Trail rất chặt chẽ để phục vụ việc tra cứu và phân tích hiệu suất làm việc của đội ngũ vận hành.
