# Invoice generation

### Quản lý thông tin pháp lý đa thực thể của người bán

Trong thực tế, một hệ thống hóa đơn có thể phục vụ cho một công ty có nhiều chi nhánh hoặc nhiều hộ kinh doanh khác nhau trên cùng một nền tảng. Mỗi thực thể này có mã số thuế riêng, địa chỉ đăng ký kinh doanh riêng và con dấu kỹ thuật số khác nhau. Bài toán đặt ra là làm thế nào để lưu trữ và truy xuất đúng bộ thông tin pháp lý của người bán tại thời điểm phát hành hóa đơn, đảm bảo rằng ngay cả khi công ty thay đổi địa chỉ trong tương lai, các hóa đơn cũ vẫn giữ nguyên thông tin địa chỉ tại thời điểm chúng được xuất bản.

### Xử lý logic thuế suất đa tầng và thuế đặc thù

Một đơn hàng có thể chứa nhiều loại mặt hàng với các quy định thuế khác nhau như mặt hàng không chịu thuế, mặt hàng chịu thuế suất 5%, 8% hoặc 10%. Ngoài ra, một số ngành hàng đặc thù còn phải chịu thêm thuế tiêu thụ đặc biệt trước khi tính thuế giá trị gia tăng. Hệ thống cần ghi nhận chi tiết tiền thuế cho từng dòng sản phẩm thay vì chỉ tính tổng ở cuối hóa đơn. Việc thiết kế dữ liệu phải phân tách được giá trước thuế, tỷ lệ thuế áp dụng, số tiền thuế tuyệt đối và tổng giá sau thuế cho từng hạng mục để phục vụ báo cáo thuế định kỳ.

### Quản lý trạng thái và quy trình điều chỉnh hóa đơn

Hóa đơn chính thức sau khi đã xuất và có mã của cơ quan thuế thì không thể xóa bỏ một cách tùy tiện. Bài toán thực tế yêu cầu hệ thống phải xử lý được các nghiệp vụ như hủy hóa đơn do sai sót thông tin, xuất hóa đơn thay thế hoặc xuất hóa đơn điều chỉnh giảm khi khách hàng trả hàng. Mỗi hành động này cần được lưu vết nghiêm ngặt, liên kết chặt chẽ với số hóa đơn gốc và phải tuân thủ đúng trình tự trạng thái từ bản nháp đến khi được ký số và gửi lên hệ thống của cơ quan quản lý.

### Quy đổi ngoại tệ và tỷ giá tại thời điểm giao dịch

Nhiều doanh nghiệp thực hiện giao dịch bằng ngoại tệ nhưng khi xuất hóa đơn chính thức bắt buộc phải quy đổi ra đồng tiền nội tệ theo tỷ giá của ngân hàng tại thời điểm xuất hóa đơn. Bài toán này yêu cầu hệ thống phải lưu trữ thông tin về loại tiền tệ giao dịch ban đầu, tỷ giá quy đổi được áp dụng và số tiền quy đổi tương ứng. Điều này cực kỳ quan trọng cho việc đối soát kế toán và giải trình với cơ quan thuế về sự chênh lệch tỷ giá giữa lúc đặt hàng và lúc phát hành hóa đơn chính thức.

### Tích hợp chữ ký số và xác thực điện tử

Để một hóa đơn có giá trị pháp lý, nó phải được ký bởi chữ ký số của doanh nghiệp. Quá trình này tạo ra các dữ liệu kỹ thuật số phức tạp bao gồm chuỗi ký tự mã hóa và thông tin chứng thư số. Bài toán đặt ra là thiết kế cấu trúc dữ liệu để lưu trữ các thông tin xác thực này sao cho có thể kiểm tra tính toàn vẹn của hóa đơn bất kỳ lúc nào. Ngoài ra, hệ thống cần quản lý được danh sách các chứng thư số còn hạn dùng và cơ chế gọi các dịch vụ ký số từ bên thứ ba (ca-provider) một cách ổn định.

### Phân tách thông tin khách hàng cá nhân và khách hàng doanh nghiệp

Hóa đơn chính thức yêu cầu thông tin khách hàng rất khắt khe. Đối với khách hàng cá nhân, thông tin có thể đơn giản, nhưng đối với khách hàng doanh nghiệp, bắt buộc phải có tên công ty đầy đủ theo giấy phép, mã số thuế và địa chỉ trụ sở chính. Hệ thống cần một cấu trúc dữ liệu linh hoạt để lưu trữ thông tin người mua trên hóa đơn sao cho nó độc lập với hồ sơ người dùng trong hệ thống bán hàng, vì khách hàng có thể mua hàng cho cá nhân hoặc mua hộ cho công ty của họ.

### Đánh số hóa đơn và quản lý dải ký hiệu

Hóa đơn chính thức không được đánh số tự động tăng một cách đơn giản như ID trong cơ sở dữ liệu. Nó bao gồm ký hiệu hóa đơn, mẫu số hóa đơn và số thứ tự thường có độ dài cố định. Các quy định pháp lý yêu cầu số hóa đơn phải liên tục và không được ngắt quãng trong một năm tài chính. Bài toán này đòi hỏi việc thiết kế logic cấp số hóa đơn đảm bảo tính duy nhất, liên tục và khả năng quản lý nhiều dải hóa đơn khác nhau cho các loại hình dịch vụ khác nhau trong cùng một doanh nghiệp.

### Chiết khấu thương mại và giảm giá trên hóa đơn

Việc thể hiện chiết khấu trên hóa đơn chính thức phức tạp hơn nhiều so với việc trừ tiền thông thường. Có hai trường hợp phổ biến: chiết khấu trực tiếp trên từng dòng sản phẩm hoặc chiết khấu tổng đơn hàng sau thuế. Cách thức thể hiện này ảnh hưởng trực tiếp đến việc tính toán tổng tiền thuế cuối cùng. Hệ thống cần ghi nhận rõ khoản giảm giá này là trước thuế hay sau thuế để đảm bảo các con số cộng lại trên hóa đơn khớp chính xác đến từng đơn vị đồng lẻ theo đúng quy định kế toán.

### Lưu trữ và phục hồi định dạng file hóa đơn gốc

Hóa đơn điện tử chính thức thường tồn tại dưới dạng file XML có cấu trúc chặt chẽ để máy tính đọc và file PDF để người dùng đọc. Bài toán thực tế là làm thế nào để quản lý việc lưu trữ các tệp tin này một cách an toàn, có khả năng truy xuất nhanh chóng khi khách hàng cần tải về, đồng thời đảm bảo rằng tệp PDF được sinh ra luôn đồng nhất với dữ liệu thô trong cơ sở dữ liệu và dữ liệu XML đã gửi cho cơ quan thuế.

### Đối soát thanh toán và gạch nợ hóa đơn

Một hóa đơn có thể được thanh toán bằng nhiều phương thức khác nhau như tiền mặt, chuyển khoản ngân hàng hoặc cấn trừ công nợ. Bài toán thực tế yêu cầu hệ thống phải liên kết được hóa đơn với các chứng từ thanh toán tương ứng. Một hóa đơn có thể được thanh toán làm nhiều lần, hoặc một lần thanh toán có thể chi trả cho nhiều hóa đơn khác nhau. Việc thiết kế hệ thống phải cho phép theo dõi trạng thái thanh toán của hóa đơn để hỗ trợ bộ phận kế toán trong việc thu hồi công nợ.
