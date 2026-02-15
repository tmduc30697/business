# Stock movement log

### Truy vết sai lệch tồn kho sau kiểm kho định kỳ

Trong quá trình vận hành, số lượng hàng hóa thực tế trên kệ thường lệch so với số liệu trên phần mềm do thất thoát hoặc sai sót khi quét mã. Khi nhân viên kho thực hiện điều chỉnh số dư, hệ thống cần ghi lại một bản ghi log đặc biệt cho phép đối chiếu giữa số lượng cũ, số lượng mới và lý do điều chỉnh. Thách thức ở đây là làm thế nào để liên kết bản ghi điều chỉnh này với một mã phiếu kiểm kho cụ thể nhằm phục vụ mục đích hậu kiểm và quy trách nhiệm cho ca trực liên quan.

### Quản lý luồng hàng hoàn trả từ khách hàng và NCC

Hàng hóa khi quay về kho có thể đến từ hai nguồn là khách hàng trả hàng hoặc nhà cung cấp đổi trả hàng lỗi. Mỗi loại hoàn trả lại có những quy trình xử lý khác nhau như nhập lại kho bán hàng, đưa vào kho chờ thanh lý hoặc tiêu hủy. Bản ghi log cần phải phân loại chính xác trạng thái của hàng hóa tại thời điểm nhập lại và tham chiếu được tới mã đơn hàng gốc để kế toán có thể tính toán lại công nợ hoặc doanh thu chính xác.

### Đồng bộ tồn kho giữa các chi nhánh trong chuỗi cửa hàng

Khi một đơn hàng được luân chuyển từ kho tổng sang kho chi nhánh, lịch sử biến động cần được ghi nhận ở cả hai đầu cầu. Một bên sẽ ghi nhận log xuất kho điều chuyển và một bên ghi nhận log nhập kho điều chuyển. Bài toán đặt ra là làm sao để duy trì tính toàn vẹn dữ liệu khi một bên đã xuất nhưng bên kia chưa nhận, và làm thế nào để thiết kế log giúp nhân viên vận hành biết được lượng hàng đang nằm trên đường vận chuyển là bao nhiêu.

### Theo dõi thời hạn sử dụng và số lô của hàng dược phẩm

Đối với các mặt hàng có hạn sử dụng, việc nhập xuất kho không chỉ đơn thuần là tăng giảm số lượng tổng mà phải gắn liền với số lô sản xuất cụ thể. Lịch sử biến động kho lúc này phải chi tiết đến từng lô để đảm bảo nguyên tắc hàng hết hạn trước xuất trước. Khi có sự cố thu hồi sản phẩm, hệ thống log phải cho phép truy xuất nhanh chóng danh sách các khách hàng hoặc đại lý đã nhận hàng từ đúng số lô bị lỗi đó.

### Xử lý tranh chấp dữ liệu khi nhiều nhân viên cùng thao tác

Trong một kho hàng lớn, nhiều nhân viên có thể cùng thực hiện đóng gói hoặc nhập hàng cho cùng một mã sản phẩm tại một thời điểm. Nếu hệ thống ghi log không được thiết kế tốt để xử lý tranh chấp, số dư cuối kỳ trong log có thể bị sai lệch so với thực tế. Bài toán này yêu cầu thiết kế cơ chế ghi log sao cho mỗi thay đổi đều có tính tuần tự, lưu trữ được số dư tức thời trước và sau mỗi giao dịch để dễ dàng phát hiện ra điểm gây lỗi trong luồng dữ liệu.

### Tối ưu hóa hiệu năng truy vấn báo cáo xuất nhập tồn

Theo thời gian, bảng ghi chép biến động kho sẽ lên tới hàng triệu bản ghi, khiến việc tính toán báo cáo xuất nhập tồn trong một khoảng thời gian trở nên rất chậm. Bài toán thực tế là thiết kế cấu trúc log và các bảng tổng hợp dữ liệu trung gian sao cho người quản lý có thể xem báo cáo tổng hợp theo ngày hoặc theo tháng mà không phải quét lại toàn bộ lịch sử từ đầu. Điều này ảnh hưởng trực tiếp đến cách bạn phân loại Index và phân vùng dữ liệu trong database.

### Quản lý hàng giữ chỗ cho đơn hàng online đang chờ xử lý

Khi khách hàng đặt hàng trực tuyến nhưng chưa thanh toán, số lượng hàng đó cần được chuyển sang trạng thái giữ chỗ thay vì trừ trực tiếp vào tồn kho khả dụng. Hệ thống log cần ghi nhận sự thay đổi về trạng thái tồn kho từ sẵn sàng sang giữ chỗ và ngược lại nếu đơn hàng bị hủy. Việc này giúp bộ phận bán hàng không bán quá số lượng thực tế trong khi bộ phận kho vẫn biết chính xác số hàng đang nằm trên kệ chưa đóng gói.

### Tự động hóa việc ghi log từ các thiết bị IoT và máy quét

Trong các kho hàng hiện đại, việc ghi log không được thực hiện thủ công bằng tay mà thông qua các máy quét cầm tay hoặc cảm biến trên băng chuyền. Bài toán ở đây là thiết kế API nhận dữ liệu log từ nhiều thiết bị ngoại vi cùng lúc với tần suất cao. Log cần phải lưu trữ thêm thông tin về định danh thiết bị và vị trí vị trí thực tế trong kho để người quản lý có thể giám sát được hiệu suất làm việc của từng khu vực hoặc từng thiết bị cụ thể.

### Phân tích xu hướng luân chuyển hàng hóa để dự báo nhập hàng

Dựa trên dữ liệu lịch sử biến động kho trong quá khứ, doanh nghiệp muốn phân tích xem loại hàng nào có tần suất xuất kho cao nhất theo mùa. Bài toán yêu cầu cấu trúc log phải đủ thông tin về thời gian chi tiết và loại hình giao dịch để các công cụ phân tích dữ liệu có thể trích xuất. Việc thiết kế các trường thông tin phân loại trong log sẽ quyết định tính khả thi của việc xây dựng các mô hình dự báo nhu cầu nhập hàng trong tương lai.

### Kiểm soát quyền hạn và lịch sử chỉnh sửa log của quản trị viên

Vì lý do an ninh, các bản ghi biến động kho sau khi đã ghi lại thì không được phép xóa hoặc sửa đổi tùy tiện. Tuy nhiên, trong một số trường hợp đặc biệt, quản trị viên cấp cao cần điều chỉnh dữ liệu bị sai do lỗi hệ thống. Bài toán đặt ra là thiết kế một cơ chế log của log để ghi lại bất kỳ tác động nào vào bảng lịch sử kho, bao gồm người thực hiện, nội dung thay đổi và bằng chứng phê duyệt, nhằm đảm bảo tính minh bạch tối đa cho quá trình audit.
