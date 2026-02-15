# Bulk update product

### Cập nhật giá theo chiến dịch khuyến mãi mùa lễ hội

Hệ thống cần cho phép quản trị viên lựa chọn hàng nghìn sản phẩm thuộc một hoặc nhiều ngành hàng cụ thể để áp dụng mức giảm giá đồng loạt. Thay vì sửa từng món, người dùng sẽ nhập tỷ lệ phần trăm giảm giá hoặc số tiền giảm cố định. Bài toán yêu cầu hệ thống phải tính toán lại giá bán cuối cùng dựa trên giá gốc, đồng thời ghi nhận thời gian bắt đầu và kết thúc của đợt điều chỉnh này để tự động khôi phục giá cũ khi hết hạn.

### Điều chỉnh tồn kho từ file Excel của nhà cung cấp

Mỗi sáng, kho hàng nhận được một tệp dữ liệu từ nhà cung cấp chứa danh sách mã SKU và số lượng tồn kho mới nhất. Nhân viên vận hành sẽ tải tệp này lên hệ thống để cập nhật số dư kho cho toàn bộ cửa hàng. Hệ thống phải đối soát mã SKU trong tệp với dữ liệu trong database, xử lý các trường hợp mã không tồn tại và cập nhật số lượng tồn thực tế một cách chính xác mà không làm gián đoạn các giao dịch đang diễn ra.

### Thay đổi danh mục và thuộc tính sản phẩm khi tái cấu trúc gian hàng

Khi một sàn thương mại điện tử thay đổi cấu trúc phân loại, hàng loạt sản phẩm cần được chuyển từ danh mục cũ sang danh mục mới. Ví dụ, toàn bộ sản phẩm trong nhóm Áo sơ mi nam và Áo thun nam sẽ được gộp chung vào nhóm Thời trang nam phía trên. Quá trình này đòi hỏi việc cập nhật lại khóa ngoại của danh mục và đồng bộ lại các thuộc tính đặc thù của ngành hàng mới cho tất cả sản phẩm liên quan.

### Cập nhật trạng thái hiển thị và kênh bán hàng hàng loạt

Một doanh nghiệp muốn tạm ẩn toàn bộ các sản phẩm của một thương hiệu cụ thể do ngừng hợp tác kinh doanh. Người dùng sẽ chọn thương hiệu đó và chuyển trạng thái của tất cả sản phẩm từ Đang bán sang Ngừng kinh doanh hoặc Nháp. Ngoài ra, hệ thống cũng cần hỗ trợ việc bật hoặc tắt quyền bán các sản phẩm này trên các kênh khác nhau như Website, Facebook Store hay Shopee chỉ trong một lần xác nhận.

### Đồng bộ thông tin từ hệ thống quản lý trung tâm ERP

Trong mô hình bán lẻ chuỗi, dữ liệu sản phẩm thường được quản lý tại một hệ thống ERP trung tâm. Khi có sự thay đổi về mô tả sản phẩm, hình ảnh hoặc đơn vị tính trên ERP, một lệnh gọi API hoặc một tệp dữ liệu lớn sẽ được gửi đến hệ thống bán hàng trực tuyến. Bài toán này đòi hỏi hệ thống tiếp nhận phải xử lý cập nhật hàng loạt các trường thông tin văn bản và đường dẫn hình ảnh cho hàng chục nghìn bản ghi cùng lúc.

### Áp dụng bảng giá riêng biệt cho các nhóm khách hàng B2B

Doanh nghiệp có các chính sách giá khác nhau cho đại lý cấp một, đại lý cấp hai và khách lẻ. Khi giá nhập kho thay đổi, người quản lý cần cập nhật lại toàn bộ bảng giá cho từng nhóm đối tượng này. Hệ thống cần xử lý việc cập nhật đa bảng giá trên cùng một danh sách sản phẩm, đảm bảo rằng mỗi nhóm khách hàng khi đăng nhập sẽ nhìn thấy mức giá mới nhất đã được cập nhật đồng bộ.

### Gắn nhãn tag và phân loại sản phẩm cho bộ lọc tìm kiếm

Để tối ưu hóa trải nghiệm tìm kiếm, nhân viên marketing cần gắn thêm các nhãn tag như Sản phẩm mới, Bán chạy hoặc Xu hướng cho một danh sách các sản phẩm được lọc theo tiêu chí doanh số. Việc cập nhật này ảnh hưởng đến các bảng quan hệ nhiều-nhiều trong cơ sở dữ liệu. Hệ thống phải đảm bảo việc thêm mới hoặc xóa bỏ các tag hàng loạt diễn ra nhanh chóng để bộ lọc trên giao diện người dùng hiển thị kết quả chính xác ngay lập tức.

### Cập nhật thông tin vận chuyển và kích thước đóng gói

Khi đơn vị vận chuyển thay đổi quy định về cách tính phí dựa trên trọng lượng quy đổi, chủ cửa hàng cần cập nhật lại cân nặng, chiều dài, chiều rộng và chiều cao cho toàn bộ sản phẩm cồng kềnh. Thông tin này rất quan trọng để API tính phí giao hàng hoạt động chính xác. Bài toán yêu cầu cập nhật hàng loạt các trường dữ liệu kỹ thuật này và đảm bảo chúng được đồng bộ sang các đơn vị giao vận tích hợp.
