# Lost package claim

### Quản lý vòng đời trạng thái của phiếu khiếu nại

Khi một khách hàng báo cáo kiện hàng bị mất, hệ thống cần ghi nhận và theo dõi phiếu khiếu nại qua nhiều giai đoạn khác nhau. Các trạng thái có thể bao gồm từ lúc tiếp nhận đơn, đang xác minh với kho hàng, đang kiểm tra với đơn vị vận chuyển, cho đến khi đưa ra quyết định cuối cùng là bồi thường hoặc từ chối. Bài toán này đòi hỏi việc thiết kế một cơ chế lưu trữ lịch sử thay đổi trạng thái chặt chẽ để phục vụ mục đích kiểm toán và giúp nhân viên hỗ trợ biết được chính xác bước tiếp theo cần thực hiện là gì.

### Phân cấp quyền hạn và luồng phê duyệt bồi thường

Tùy vào giá trị của đơn hàng bị thất lạc mà quy trình phê duyệt khoản tiền bồi thường sẽ khác nhau. Những đơn hàng có giá trị nhỏ có thể được hệ thống tự động duyệt hoặc nhân viên sơ cấp xử lý ngay lập tức. Tuy nhiên, với những đơn hàng giá trị cao hoặc các mặt hàng dễ vỡ, quy trình cần phải đi qua nhiều cấp lãnh đạo khác nhau để phê duyệt. Việc thiết kế hệ thống cần đảm bảo phân định rõ vai trò của từng cấp bậc nhân viên và lưu lại dấu vết phê duyệt của từng người trong hồ sơ khiếu nại.

### Đối soát bằng chứng hình ảnh và dữ liệu vận chuyển

Một trong những bước quan trọng nhất khi giải quyết khiếu nại là thu thập bằng chứng từ các bên. Phía khách hàng có thể cung cấp ảnh chụp vị trí giao hàng trống không, trong khi phía shipper cung cấp ảnh chụp đã giao hàng thành công. Hệ thống cần có khả năng lưu trữ và liên kết các tệp tin đa phương tiện này với mã vận đơn và mã khiếu nại tương ứng. Bài toán này giúp bạn thực hành cách quản lý dữ liệu không cấu trúc và liên kết chúng với các bảng dữ liệu nghiệp vụ trong cơ sở dữ liệu.

### Tính toán giá trị bồi thường theo chính sách bảo hiểm

Giá trị bồi thường không phải lúc nào cũng bằng 100% giá trị hóa đơn. Nó phụ thuộc vào việc khách hàng có mua bảo hiểm hàng hóa hay không, loại hình dịch vụ vận chuyển đã chọn và các điều khoản giới hạn trách nhiệm của đơn vị vận chuyển. Hệ thống cần lưu trữ các quy tắc nghiệp vụ phức tạp về mức trần bồi thường và các công thức tính toán khấu hao dựa trên loại mặt hàng. Đây là bài toán tốt để thiết kế các logic xử lý về tài chính và thanh toán trong API.

### Quản lý giao tiếp đa kênh giữa các bên liên quan

Trong quá trình xử lý thất lạc, nhân viên hỗ trợ khách hàng thường phải trao đổi liên tục với cả người gửi, người nhận và bộ phận điều phối vận chuyển. Mỗi lần có thông tin mới hoặc yêu cầu bổ sung giấy tờ, hệ thống cần gửi thông báo qua email, tin nhắn hoặc ứng dụng di động. Việc thiết kế database cho phần này cần chú ý đến việc lưu trữ các cuộc hội thoại theo luồng và đảm bảo tất cả các bên đều nhận được thông tin cập nhật đồng bộ theo thời gian thực.

### Tự động hóa việc truy vấn vị trí cuối cùng của kiện hàng

Trước khi kết luận một đơn hàng bị mất, hệ thống cần thực hiện một lệnh quét toàn diện trên các trạm trung chuyển mà đơn hàng đã đi qua. Bài toán này yêu cầu hệ thống phải tích hợp với API của các đối tác vận chuyển bên thứ ba để lấy dữ liệu log chi tiết về vị trí và thời gian cuối cùng kiện hàng được quét mã. Dữ liệu này sau đó được đối chiếu với lịch trình dự kiến để khoanh vùng khu vực có khả năng xảy ra sự cố cao nhất, giúp thu hẹp phạm vi tìm kiếm.

### Phân tích và dự báo rủi ro thất lạc theo tuyến đường

Dựa trên dữ liệu các vụ khiếu nại đã đóng, doanh nghiệp muốn xây dựng một hệ thống báo cáo để nhận diện các điểm nóng thường xuyên xảy ra mất mát hàng hóa. Bài toán yêu cầu lưu trữ dữ liệu sao cho có thể truy vấn theo vùng địa lý, theo đơn vị vận chuyển cụ thể hoặc theo ca làm việc của nhân viên kho. Điều này giúp bộ phận vận hành đưa ra các cảnh báo sớm hoặc điều chỉnh lại lộ trình vận chuyển để giảm thiểu rủi ro thất lạc trong tương lai.

### Quy trình hoàn tiền và xử lý tài chính sau khiếu nại

Sau khi một khiếu nại thất lạc được chấp nhận, hệ thống cần thực hiện quy trình hoàn tiền vào ví điện tử của khách hàng hoặc tài khoản ngân hàng. Đồng thời, hệ thống cũng phải tạo ra các yêu cầu thu hồi số tiền bồi thường đó từ phía đơn vị bảo hiểm hoặc từ tiền lương của nhân viên vận chuyển nếu lỗi thuộc về cá nhân. Việc thiết kế database cho phần này cần đảm bảo tính toàn vẹn dữ liệu cực cao để tránh việc hoàn tiền trùng lặp hoặc sai sót trong sổ sách kế toán.
