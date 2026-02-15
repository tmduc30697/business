# Tax configuration

### Cấu hình thuế suất thay đổi theo danh mục loại hàng hóa

Trong cùng một quốc gia, các loại hàng hóa khác nhau thường chịu mức thuế suất khác nhau. Ví dụ, các mặt hàng thiết yếu như thực phẩm tươi sống có thể chịu mức thuế thấp hoặc miễn thuế, trong khi các mặt hàng xa xỉ như rượu bia, thuốc lá hoặc đồ điện tử lại chịu mức thuế cao hơn. Hệ thống cần cho phép thiết lập bảng tra cứu thuế dựa trên mã phân loại sản phẩm để khi người dùng thêm bất kỳ món hàng nào vào giỏ hàng, hệ thống sẽ tự động áp dụng đúng mức phần trăm thuế tương ứng cho món hàng đó.

### Tính thuế dựa trên địa điểm giao hàng của người mua

Tại các quốc gia có cấu trúc hành chính phức tạp như Mỹ hoặc Canada, thuế bán hàng không chỉ phụ thuộc vào quốc gia mà còn thay đổi theo từng bang, thậm chí từng mã bưu chính hoặc thành phố cụ thể. Một đơn hàng gửi đến bang California sẽ có mức thuế khác hoàn toàn với đơn hàng gửi đến bang Texas. Bài toán này yêu cầu thiết kế cơ sở dữ liệu vùng lãnh thổ đa cấp và logic tìm kiếm mức thuế ưu tiên theo địa chỉ chi tiết nhất mà người dùng cung cấp khi đặt hàng.

### Quản lý thay đổi thuế suất theo thời điểm hiệu lực

Chính phủ có thể ban hành quy định thay đổi mức thuế giá trị gia tăng từ mức hiện tại sang một mức mới kể từ một ngày cụ thể trong tương lai. Hệ thống không được phép ghi đè trực tiếp lên cấu hình cũ vì sẽ làm sai lệch báo cáo tài chính của các đơn hàng trong quá khứ. Bạn cần thiết kế một cơ chế lưu trữ phiên bản thuế có ngày bắt đầu và ngày kết thúc hiệu lực, giúp hệ thống biết chính xác tại thời điểm chốt đơn hàng đó thì mức thuế nào đang được áp dụng.

### Cấu hình thuế suất khác nhau giữa các mô hình kinh doanh B2B và B2C

Trong mô hình kinh doanh giữa doanh nghiệp với doanh nghiệp, mức thuế thường được xử lý khác so với bán lẻ cho người tiêu dùng cá nhân. Ví dụ, nếu một doanh nghiệp có mã số thuế hợp lệ, họ có thể được miễn thuế trực tiếp trên hóa đơn hoặc được áp dụng cơ chế hoàn thuế sau. Hệ thống cần quản lý hồ sơ thuế của khách hàng và đối chiếu với loại hình giao dịch để quyết định xem có thu thuế hay không và hiển thị số tiền thuế tách biệt với giá bán gốc.

### Xử lý thuế cho các dịch vụ số và sản phẩm xuyên biên giới

Khi bán một khóa học online hoặc phần mềm cho khách hàng ở nước ngoài, việc tính thuế trở nên phức tạp do quy định thuế tại nơi người mua cư trú. Một khách hàng ở châu Âu mua phần mềm từ một công ty Việt Nam có thể phải chịu thuế giá trị gia tăng theo quy định của nước họ. Bài toán này đòi hỏi hệ thống phải xác định được vị trí địa lý của người dùng qua địa chỉ IP hoặc quốc gia đăng ký để áp dụng các quy tắc thuế quốc tế một cách tự động trước khi thanh toán.

### Thuế suất hỗn hợp cho các bộ sản phẩm đóng gói kèm nhau

Doanh nghiệp thường tạo ra các combo sản phẩm bao gồm nhiều mặt hàng có mức thuế khác nhau, ví dụ một giỏ quà gồm rượu (thuế cao) và bánh kẹo (thuế thấp). Khi khách hàng mua cả combo với một mức giá tổng duy nhất, hệ thống cần có cơ chế phân bổ giá trị combo cho từng món hàng thành phần để tính toán số tiền thuế tổng cộng một cách chính xác nhất, tránh việc thất thoát thuế hoặc thu sai quy định của cơ quan chức năng.

### Cấu hình thuế bao gồm hoặc loại trừ khỏi giá bán sản phẩm

Tùy vào quốc gia hoặc cài đặt của chủ cửa hàng, giá hiển thị trên website có thể đã bao gồm thuế hoặc chưa bao gồm thuế. Nếu giá đã bao gồm thuế, hệ thống phải thực hiện phép tính ngược để bóc tách tiền thuế và tiền hàng thực tế trên hóa đơn. Nếu giá chưa bao gồm thuế, tiền thuế sẽ được cộng thêm ở bước thanh toán cuối cùng. Hệ thống cần một cờ cấu hình linh hoạt để thay đổi cách hiển thị và cách tính toán này trên toàn bộ ứng dụng mà không cần sửa đổi dữ liệu giá của từng sản phẩm.

### Miễn giảm thuế cho các đối tượng hoặc trường hợp đặc biệt

Trong một số trường hợp đặc biệt như hàng xuất khẩu hoặc bán cho các tổ chức phi lợi nhuận, đơn hàng có thể được hưởng mức thuế suất không phần trăm hoặc miễn thuế hoàn toàn dù loại hàng đó bình thường vẫn có thuế. Hệ thống cần thiết lập các quy tắc ưu tiên để ghi đè mức thuế mặc định khi đơn hàng thỏa mãn các điều kiện cụ thể về đối tượng mua hàng hoặc mục đích sử dụng, đồng thời lưu trữ lý do miễn giảm để phục vụ việc kiểm toán sau này.
