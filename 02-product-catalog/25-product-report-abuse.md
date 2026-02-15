# Product report abuse

### Quản lý danh mục vi phạm đa cấp và trọng số độc hại

Hệ thống cần cho phép quản trị viên định nghĩa các loại vi phạm khác nhau như hàng giả, vũ khí, nội dung khiêu dâm hoặc lừa đảo. Mỗi loại vi phạm sẽ thuộc một nhóm cha nhất định và đi kèm với một mức độ nghiêm trọng riêng biệt. Việc thiết kế cần đảm bảo khi người dùng báo cáo, họ có thể chọn từ các danh mục gợi ý này, và hệ thống sẽ dựa vào trọng số của danh mục đó để ưu tiên hiển thị các báo cáo nguy hiểm lên đầu hàng đợi kiểm duyệt.

### Thu thập bằng chứng đa phương tiện và thông tin ngữ cảnh

Khi người dùng thực hiện báo cáo một sản phẩm, họ không chỉ gửi lý do văn bản mà còn phải cung cấp bằng chứng cụ thể. Bài toán yêu cầu lưu trữ các tệp hình ảnh, video hoặc ảnh chụp màn hình chứng minh vi phạm. Ngoài ra, hệ thống phải ghi lại trạng thái của sản phẩm tại thời điểm báo cáo gồm giá cả, mô tả sản phẩm và thông tin người bán để tránh trường hợp người bán thay đổi nội dung sản phẩm nhằm xóa dấu vết sau khi bị báo cáo.

### Quy trình xử lý báo cáo theo luồng công việc của kiểm duyệt viên

Sau khi nhận báo cáo, hệ thống cần điều phối các yêu cầu này đến đội ngũ kiểm duyệt viên. Bài toán này tập trung vào trạng thái của báo cáo từ lúc mới tiếp nhận, đang xử lý, yêu cầu bổ sung thông tin, cho đến khi đóng báo cáo. Cần thiết kế sao cho một báo cáo có thể được chuyển qua lại giữa các phòng ban chuyên trách khác nhau và lưu lại lịch sử thay đổi trạng thái kèm theo ghi chú của người xử lý để phục vụ mục đích đối soát.

### Cơ chế gom nhóm các báo cáo trùng lặp trên cùng một sản phẩm

Trong thực tế, một sản phẩm vi phạm có thể bị hàng nghìn người báo cáo cùng lúc. Nếu mỗi báo cáo được xử lý riêng lẻ sẽ gây lãng phí nguồn lực. Hệ thống cần có cơ chế tự động gom nhóm các báo cáo về cùng một mã sản phẩm và cùng một loại vi phạm vào một vụ việc duy nhất. Điều này giúp kiểm duyệt viên chỉ cần đưa ra một quyết định xử lý nhưng áp dụng được cho tất cả các báo cáo liên quan và phản hồi đồng loạt cho những người dùng đã gửi báo cáo đó.

### Hệ thống điểm uy tín của người báo cáo và người bán

Để giảm thiểu các báo cáo rác hoặc báo cáo phá hoại từ đối thủ cạnh tranh, hệ thống cần quản lý điểm tin cậy của người gửi báo cáo. Nếu một người thường xuyên báo cáo đúng, yêu cầu của họ sẽ được ưu tiên. Ngược lại, nếu báo cáo sai nhiều lần, tài khoản đó sẽ bị hạn chế tính năng. Đồng thời, hệ thống cũng cần theo dõi lịch sử vi phạm của người bán để tự động khóa tài khoản hoặc gỡ sản phẩm nếu số lượng báo cáo vi phạm vượt quá một ngưỡng nhất định trong khoảng thời gian ngắn.

### Kháng cáo và xử lý tranh chấp sau kiểm duyệt

Khi một sản phẩm bị gỡ bỏ hoặc người bán bị xử phạt, hệ thống phải cung cấp quy trình cho phép người bán gửi đơn khiếu nại nếu họ cho rằng quyết định của kiểm duyệt viên là sai lầm. Bài toán này yêu cầu thiết kế các thực thể liên kết giữa quyết định xử phạt ban đầu và đơn kháng cáo, cho phép kiểm duyệt viên cấp cao hơn xem xét lại hồ sơ, bằng chứng cũ và bằng chứng mới để đưa ra quyết định cuối cùng là giữ nguyên hay hủy bỏ lệnh phạt.

### Tự động hóa kiểm duyệt bằng trí tuệ nhân tạo và quy tắc cứng

Trước khi đưa đến tay con người, các báo cáo cần đi qua một lớp xử lý tự động. Hệ thống sẽ quét qua nội dung sản phẩm và hình ảnh bằng các mô hình học máy hoặc bộ lọc từ khóa cấm. Nếu độ tin cậy của vi phạm vượt ngưỡng quy định, hệ thống có thể tự động ẩn sản phẩm ngay lập tức để ngăn chặn rủi ro phát tán, sau đó mới đẩy hồ sơ cho con người xác nhận lại. Điều này đòi hỏi thiết kế hệ thống có khả năng tích hợp các dịch vụ bên thứ ba và xử lý bất đồng bộ.

### Hệ thống thông báo và phản hồi kết quả báo cáo

Một phần quan trọng của trải nghiệm người dùng là việc thông báo kết quả. Hệ thống cần theo dõi và gửi thông báo cho người báo cáo khi yêu cầu của họ được tiếp nhận và sau khi có kết quả xử lý cuối cùng. Đối với người bán, thông báo phải nêu rõ lý do vi phạm, điều khoản chính sách bị vi phạm và các bước tiếp theo họ có thể thực hiện. Việc thiết kế cần đảm bảo tính thời gian thực và khả năng lưu trữ lịch sử thông báo đồ sộ.
