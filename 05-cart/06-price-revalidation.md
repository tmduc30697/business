# Price revalidation

### Thay đổi giá theo thời gian thực trong phiên flash sale

Trong các sự kiện giảm giá chớp nhoáng, giá của sản phẩm có thể thay đổi ngay lập tức khi đồng hồ đếm ngược kết thúc hoặc khi số lượng hàng khuyến mãi hết sạch. Người dùng thường thêm hàng vào giỏ từ trước đó cả tiếng đồng hồ. Khi họ nhấn nút thanh toán, hệ thống cần so sánh giá tại thời điểm đó với giá lưu trong giỏ hàng. Nếu giá đã quay về mức gốc, hệ thống phải thông báo rõ ràng và yêu cầu người dùng xác nhận lại tổng tiền mới trước khi tiến hành trừ tiền.

### Biến động tỷ giá hối đoái cho sàn thương mại điện tử quốc tế

Đối với các nền tảng bán hàng xuyên biên giới, giá sản phẩm thường được niêm yết bằng một loại tiền tệ gốc nhưng hiển thị cho người dùng bằng tiền tệ địa phương dựa trên tỷ giá hối đoái liên ngân hàng. Tỷ giá này biến động theo từng phút. Bài toán đặt ra là khi người dùng thanh toán, hệ thống phải thực hiện revalidation để đảm bảo số tiền quy đổi cuối cùng khớp với tỷ giá mới nhất, tránh việc sàn giao dịch chịu lỗ do chênh lệch tỷ giá phát sinh trong quá trình người dùng cân nhắc mua hàng.

### Cập nhật giá dựa trên vị trí địa lý của người mua

Một số dịch vụ giao đồ ăn hoặc vận tải áp dụng mô hình giá động dựa trên khu vực. Khi người dùng chọn món ăn vào giỏ hàng tại văn phòng nhưng sau đó di chuyển về nhà mới bấm thanh toán, hoặc đơn giản là phí dịch vụ tại khu vực đó tăng lên do thời tiết xấu đột ngột. Hệ thống cần kiểm tra lại tọa độ hiện tại của người dùng hoặc địa chỉ giao hàng cuối cùng để tính toán lại toàn bộ bảng giá và phí dịch vụ liên quan trước khi tạo hóa đơn.

### Áp dụng chồng chéo các mã giảm giá và chương trình khách hàng thân thiết

Người dùng có thể thêm sản phẩm vào giỏ khi đang là thành viên hạng đồng, nhưng sau một vài đơn hàng khác, họ được nâng cấp lên hạng vàng với mức chiết khấu cao hơn. Hoặc một mã giảm giá đính kèm trong giỏ hàng đột ngột hết hạn hoặc hết lượt sử dụng. Quá trình revalidation lúc này không chỉ kiểm tra giá gốc mà còn phải tính toán lại toàn bộ logic ưu đãi, đảm bảo các điều kiện áp dụng mã giảm giá vẫn thỏa mãn tại giây phút thanh toán cuối cùng.

### Thay đổi giá do cập nhật tồn kho từ nhà cung cấp thứ ba

Trong mô hình Dropshipping hoặc Marketplace, giá sản phẩm trong giỏ hàng của người dùng phụ thuộc vào dữ liệu từ các nhà cung cấp khác nhau. Khi nhà cung cấp cập nhật bảng giá mới trên hệ thống quản lý kho của họ, thông tin này cần được đồng bộ và kiểm tra lại ở bước thanh toán của người mua. Nếu giá nhập đầu vào tăng lên khiến biên lợi nhuận của sàn bị âm, hệ thống phải ngăn chặn giao dịch và cập nhật lại mức giá bán lẻ mới cho người dùng.

### Điều chỉnh giá theo số lượng mua sỉ và lẻ

Hệ thống áp dụng chính sách giá bậc thang, ví dụ mua dưới mười sản phẩm tính giá khác và trên mười sản phẩm tính giá ưu đãi hơn. Người dùng có thể thêm mười sản phẩm vào giỏ để hưởng giá sỉ, nhưng sau đó giảm số lượng xuống còn hai ngay tại bước thanh toán. Cơ chế revalidation phải đảm bảo rằng đơn giá của mỗi sản phẩm được điều chỉnh tăng lên tương ứng với khung số lượng mới, tránh việc người dùng lợi dụng kẽ hở để mua lẻ với giá sỉ.

### Đồng bộ giá giữa cửa hàng vật lý và ứng dụng trực tuyến

Đối với mô hình bán lẻ kết hợp, giá sản phẩm tại cửa hàng có thể được điều chỉnh bởi quản lý chi nhánh để đẩy hàng tồn. Một người dùng quét mã sản phẩm qua ứng dụng và để trong giỏ hàng. Khi họ đến quầy thanh toán, hệ thống POS phải thực hiện revalidation với cơ sở dữ liệu trung tâm để đảm bảo giá hiển thị trên điện thoại khớp với giá niêm yết hiện tại tại chi nhánh đó, bao gồm cả các loại thuế phí đặc thù của từng vùng.

### Quản lý giá sản phẩm theo thuộc tính và tùy chọn đi kèm

Các sản phẩm phức tạp như máy tính cấu hình tùy chỉnh hoặc gói bảo hiểm có giá thay đổi dựa trên các lựa chọn thành phần. Trong khoảng thời gian từ lúc người dùng cấu hình xong đến lúc thanh toán, giá của một linh kiện cụ thể như RAM hoặc ổ cứng có thể thay đổi do khan hiếm nguồn cung. Hệ thống cần bóc tách từng thành phần trong giỏ hàng để revalidate giá của từng option thay vì chỉ kiểm tra tổng giá trị đơn hàng, giúp minh bạch hóa các khoản chênh lệch cho khách hàng.
