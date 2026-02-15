# Warehouse management

### Tối ưu hóa phân vùng và lưu kho theo sức chứa

Bài toán này tập trung vào việc quản lý không gian vật lý bên trong một kho hàng. Một kho không chỉ là một khoảng trống lớn mà được chia thành các khu vực, dãy kệ, tầng và ô chứa cụ thể. Mỗi ô chứa có giới hạn về tải trọng và thể tích khác nhau. Hệ thống cần ghi nhận chính xác tọa độ của từng vị trí lưu trữ và cập nhật trạng thái lấp đầy theo thời gian thực để người quản lý biết chính xác vị trí nào còn trống và vị trí nào đã đạt ngưỡng sức chứa tối đa.

### Quản lý chuỗi kho đa chi nhánh và điều chuyển nội bộ

Trong thực tế, một doanh nghiệp thường sở hữu nhiều kho hàng đặt tại các địa điểm địa lý khác nhau để phục vụ khách hàng nhanh nhất. Bài toán đặt ra là phải quản lý danh mục địa chỉ kho, thông tin liên hệ và trạng thái hoạt động của từng chi nhánh. Hệ thống cần hỗ trợ việc luân chuyển hàng hóa giữa các kho này, đồng thời ghi lại vết lịch sử để đảm bảo hàng hóa không bị thất thoát trong quá trình vận chuyển từ kho nguồn đến kho đích.

### Phân cấp quyền hạn và trách nhiệm của người phụ trách

Một kho hàng thường có nhiều nhân sự với các vai trò khác nhau như quản lý kho, nhân viên kiểm kho và nhân viên bốc xếp. Bài toán yêu cầu thiết lập mối quan hệ giữa nhân sự và kho hàng mà họ trực thuộc. Bạn cần giải quyết vấn đề một nhân viên có thể phụ trách một hoặc nhiều kho, hoặc một kho có thể có một nhóm quản lý chung. Điều này giúp xác định ai là người chịu trách nhiệm cuối cùng khi có sự cố xảy ra tại một địa điểm cụ thể.

### Kiểm soát trạng thái vận hành và bảo trì định kỳ

Các kho hàng không phải lúc nào cũng hoạt động bình thường. Có những thời điểm kho cần tạm dừng để bảo trì, phun khử trùng hoặc kiểm kê định kỳ. Bài toán này yêu cầu hệ thống phải theo dõi trạng thái hoạt động của kho như đang mở cửa, tạm đóng hoặc ngưng hoạt động vĩnh viễn. Khi một kho ở trạng thái tạm đóng, hệ thống phải ngăn chặn các thao tác nhập xuất hàng hóa nhưng vẫn cho phép truy xuất dữ liệu tồn kho hiện tại.

### Theo dõi lịch sử biến động và kiểm toán dữ liệu kho

Để đảm bảo tính minh bạch, mọi thay đổi liên quan đến thông tin cơ bản của kho như thay đổi người phụ trách hoặc điều chỉnh sức chứa thiết kế đều cần được lưu vết. Bài toán này đòi hỏi việc thiết kế hệ thống ghi nhật ký chi tiết bao gồm thời gian thay đổi, giá trị cũ, giá trị mới và người thực hiện thay đổi đó. Đây là cơ sở để chủ doanh nghiệp thực hiện các hoạt động kiểm toán và truy cứu trách nhiệm khi có sai lệch thông tin.

### Quản lý danh mục loại kho và điều kiện lưu trữ đặc thù

Không phải hàng hóa nào cũng có thể lưu trữ trong cùng một điều kiện môi trường. Bài toán thực tế là phân loại kho theo các đặc tính kỹ thuật như kho lạnh, kho khô, kho hóa chất hay kho ngoài trời. Mỗi loại kho sẽ có các thuộc tính đi kèm riêng biệt như ngưỡng nhiệt độ, độ ẩm cho phép. Việc thiết kế database phải linh hoạt để có thể mở rộng các thuộc tính này mà không làm ảnh hưởng đến cấu trúc chung của toàn bộ hệ thống quản lý.

### Hệ thống cảnh báo ngưỡng lấp đầy và hiệu suất khai thác

Chủ doanh nghiệp cần biết hiệu suất sử dụng của từng kho hàng để đưa ra quyết định kinh doanh như thuê thêm kho hoặc giải phóng hàng tồn. Bài toán yêu cầu tính toán tỷ lệ lấp đầy dựa trên dữ liệu sức chứa thiết kế và lượng hàng thực tế đang lưu trữ. Hệ thống cần đưa ra các mức cảnh báo khi kho sắp hết chỗ hoặc khi một kho đang bị bỏ trống quá lâu gây lãng phí chi phí vận hành, giúp tối ưu hóa dòng tiền và tài sản.
