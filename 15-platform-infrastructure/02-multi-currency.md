# Multi-currency

### Quản lý bảng giá sản phẩm theo từng thị trường mục tiêu

Một nền tảng bán hàng quốc tế muốn thiết lập giá sản phẩm cố định cho từng quốc gia thay vì chỉ quy đổi tự động từ một đơn vị tiền tệ gốc. Ví dụ, một chiếc áo có giá gốc là 20 USD, nhưng tại thị trường Châu Âu chủ sàn muốn bán với giá cố định là 19 EUR và tại Việt Nam là 500.000 VND để phù hợp với sức mua địa phương. Hệ thống cần lưu trữ nhiều mức giá khác nhau cho cùng một sản phẩm và ưu tiên hiển thị mức giá tương ứng với loại tiền tệ mà người dùng đã chọn hoặc dựa trên khu vực địa lý của họ.

### Lưu trữ lịch sử tỷ giá hối đoái theo thời gian thực

Tỷ giá hối đoái giữa các đồng tiền như USD, EUR, JPY biến động liên tục từng giờ. Để hệ thống có thể quy đổi giá chính xác tại thời điểm khách hàng xem hàng, bạn cần một cơ chế cập nhật tỷ giá từ các nguồn trung gian và lưu trữ chúng vào cơ sở dữ liệu. Quan trọng hơn, hệ thống phải lưu lại lịch sử thay đổi này để phục vụ việc tra cứu xem tại một thời điểm cụ thể trong quá khứ, tỷ giá giữa hai đồng tiền bất kỳ là bao nhiêu.

### Đảm bảo tính nhất quán của giá trị đơn hàng tại thời điểm thanh toán

Khách hàng có thể thêm sản phẩm vào giỏ hàng lúc tỷ giá đang ở mức thấp, nhưng đến khi họ thực hiện thanh toán thì tỷ giá đã thay đổi. Bài toán đặt ra là hệ thống phải chốt được số tiền chính xác mà khách hàng phải trả tại giây phút họ nhấn nút đặt hàng. Giá trị này cùng với loại tiền tệ và tỷ giá áp dụng tại thời điểm đó phải được đóng băng và lưu trữ vĩnh viễn vào thông tin chi tiết của đơn hàng để phục vụ việc đối soát tài chính sau này, bất kể tỷ giá thị trường có biến động ra sao.

### Xử lý hoàn tiền cho đơn hàng đa tiền tệ sau biến động tỷ giá

Một khách hàng thanh toán đơn hàng bằng đồng EUR cho một sản phẩm có giá gốc niêm yết bằng USD. Một tuần sau, khách hàng yêu cầu hoàn tiền do hàng lỗi. Trong khoảng thời gian đó, tỷ giá giữa EUR và USD đã thay đổi đáng kể. Hệ thống cần có logic để quyết định sẽ hoàn lại số tiền chính xác theo đơn vị EUR mà khách hàng đã trả, hay hoàn theo giá trị sản phẩm quy đổi tại thời điểm hiện tại. Điều này ảnh hưởng trực tiếp đến việc ghi nhận lỗ lãi do chênh lệch tỷ giá trong sổ cái kế toán của doanh nghiệp.

### Quản lý ví số dư đa tiền tệ cho người bán trên Marketplace

Trên một sàn thương mại điện tử quốc tế, người bán có thể nhận được tiền thanh toán từ người mua ở nhiều quốc gia khác nhau với nhiều loại tiền tệ khác nhau. Hệ thống cần thiết kế một cấu trúc ví cho phép người bán theo dõi số dư của họ theo từng loại tiền tệ riêng biệt hoặc hiển thị tổng số dư quy đổi về một đồng tiền chủ chốt. Khi người bán thực hiện lệnh rút tiền về ngân hàng địa phương, hệ thống phải xử lý việc quy đổi nội bộ và tính phí chuyển đổi ngoại tệ một cách minh bạch.

### Hiển thị giá ước tính và tiền tệ thanh toán thực tế

Nhiều trang web cho phép người dùng xem giá bằng tiền tệ địa phương để dễ hình dung nhưng khi thanh toán thực tế lại bắt buộc dùng một đồng tiền chủ chốt như USD để giảm thiểu rủi ro cho sàn. Hệ thống cần phân biệt rõ ràng giữa loại tiền tệ hiển thị và loại tiền tệ thanh toán. Bạn phải thiết kế API sao cho trả về cả giá gốc kèm loại tiền tệ dùng để trừ tiền trong thẻ, lẫn giá quy đổi ước tính để người dùng không bị bỡ ngỡ khi nhìn thấy hóa đơn ngân hàng.

### Thiết lập quy tắc làm tròn số tiền theo đặc thù từng loại tiền tệ

Mỗi loại tiền tệ có quy định về số chữ số thập phân khác nhau. Ví dụ, đồng USD hay EUR thường có hai chữ số thập phân, nhưng đồng VND hay JPY thường là số nguyên. Khi hệ thống tự động quy đổi giá dựa trên tỷ giá, kết quả thường là những con số lẻ rất dài. Bạn cần thiết kế một hệ thống quy tắc làm tròn cho từng loại tiền tệ cụ thể để đảm bảo giá hiển thị trên giao diện chuyên nghiệp và không gây lỗi khi truyền dữ liệu qua các cổng thanh toán quốc tế vốn rất khắt khe về định dạng số thập phân.

### Báo cáo doanh thu tổng hợp từ nhiều loại tiền tệ khác nhau

Cuối tháng, người quản trị hệ thống cần một báo cáo tổng doanh thu của toàn sàn. Vì các đơn hàng đến từ nhiều loại tiền tệ khác nhau, hệ thống không thể đơn giản là cộng tất cả các con số lại với nhau. Bài toán yêu cầu thiết kế một công cụ tổng hợp dữ liệu, tự động quy đổi tất cả các giao dịch trong tháng về một đơn vị tiền tệ báo cáo duy nhất theo tỷ giá tại thời điểm phát sinh giao dịch hoặc tỷ giá chốt ngày, từ đó đưa ra con số tăng trưởng chính xác cho doanh nghiệp.
