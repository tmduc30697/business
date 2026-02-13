# Business Analytics

## Identity & Access

1. **[Register account](01-identity-and-access/01-register-account.md)**: Cho phép người dùng tạo tài khoản mới bằng cách cung cấp thông tin cơ bản (email, mật khẩu, số điện thoại…). Hệ thống tạo user record và gán role mặc định.
1. **[Login email/password](01-identity-and-access/02-login-email-password.md)**: Xác thực người dùng bằng email và mật khẩu đã đăng ký. Nếu hợp lệ, hệ thống tạo session/token để truy cập hệ thống.
1. **[OAuth login](01-identity-and-access/03-oauth-login.md)**: Cho phép đăng nhập qua bên thứ ba (Google, Facebook…). Hệ thống nhận token từ provider và map với tài khoản nội bộ.
1. **[Two-factor authentication](01-identity-and-access/04-two-factor-authentication.md)**: Tăng cường bảo mật bằng cách yêu cầu thêm một bước xác minh (OTP SMS, email, authenticator app) sau khi nhập mật khẩu.
1. **[Email verification](01-identity-and-access/05-email-verification.md)**: Gửi email chứa link hoặc mã xác nhận để đảm bảo email người dùng là hợp lệ trước khi kích hoạt đầy đủ tài khoản.
1. **[Forgot password](01-identity-and-access/06-forgot-password.md)**: Cho phép người dùng yêu cầu đặt lại mật khẩu khi quên, thường bằng cách nhập email để nhận link reset.
1. **[Reset password](01-identity-and-access/07-reset-password.md)**: Cho phép người dùng tạo mật khẩu mới sau khi xác minh qua link hoặc OTP hợp lệ.
1. **[Session management](01-identity-and-access/08-session-management.md)**: Quản lý các phiên đăng nhập (session/token), bao gồm tạo mới, gia hạn, hủy khi logout hoặc hết hạn.
1. **[Device management](01-identity-and-access/09-device-management.md)**: Hiển thị và quản lý các thiết bị đã đăng nhập; cho phép người dùng logout khỏi thiết bị cụ thể.
1. **[Login history](01-identity-and-access/10-login-history.md)**: Lưu lại lịch sử đăng nhập gồm thời gian, IP, thiết bị, vị trí để người dùng và hệ thống kiểm tra bất thường.
1. **[Account lock](01-identity-and-access/11-account-lock.md)**: Tự động hoặc thủ công khóa tài khoản khi phát hiện hành vi bất thường (ví dụ: nhập sai mật khẩu nhiều lần).
1. **[Role management](01-identity-and-access/12-role-management.md)**: Định nghĩa các vai trò (Customer, Seller, Admin…) và gán role cho user để phân quyền truy cập.
1. **[Permission management](01-identity-and-access/13-permission-management.md)**: Quản lý quyền chi tiết theo chức năng (view, create, edit, delete…), thường dùng mô hình RBAC hoặc ACL.
1. **[Seller KYC](01-identity-and-access/14-seller-kyc.md)**: Yêu cầu người bán cung cấp giấy tờ xác minh danh tính/doanh nghiệp trước khi được phép bán hàng.
1. **[Account suspension](01-identity-and-access/15-account-suspension.md)**: Tạm ngưng tài khoản trong một khoảng thời gian do vi phạm chính sách hoặc nghi ngờ gian lận.
1. **[Account deletion](01-identity-and-access/16-account-deletion.md)**: Cho phép người dùng yêu cầu xóa tài khoản; hệ thống xử lý theo chính sách lưu trữ dữ liệu và pháp lý.
1. **[GDPR data export](01-identity-and-access/17-gdpr-data-export.md)**: Cho phép người dùng tải xuống toàn bộ dữ liệu cá nhân mà hệ thống đang lưu trữ theo yêu cầu bảo vệ dữ liệu.
1. **[Admin impersonate user](01-identity-and-access/18-admin-impersonate-user.md)**: Cho phép admin đăng nhập vào tài khoản người dùng (dưới quyền kiểm soát và audit log) để hỗ trợ hoặc xử lý sự cố.

## Product Catalog

1. **[Create product](02-product-catalog/01-create-product.md)**: Cho phép seller tạo sản phẩm mới với đầy đủ thông tin cơ bản như tên, mô tả, giá, danh mục, hình ảnh và tồn kho.
1. **[Edit product](02-product-catalog/02-edit-product.md)**: Cho phép seller cập nhật thông tin sản phẩm đã tạo (giá, mô tả, hình ảnh, tồn kho…).
1. **[Delete product](02-product-catalog/03-delete-product.md)**: Xóa hoàn toàn sản phẩm khỏi hệ thống, thường chỉ dùng khi chưa có giao dịch liên quan.
1. **[Soft delete product](02-product-catalog/04-soft-delete-product.md)**: Ẩn sản phẩm khỏi người dùng nhưng vẫn giữ dữ liệu trong hệ thống để phục vụ audit hoặc khôi phục.
1. **[SKU management](02-product-catalog/05-sku-management.md)**: Quản lý mã SKU (Stock Keeping Unit) duy nhất cho từng sản phẩm hoặc từng biến thể để theo dõi tồn kho và giao dịch.
1. **[Category assignment](02-product-catalog/06-category-assignment.md)**: Gán sản phẩm vào một hoặc nhiều danh mục để phục vụ điều hướng và tìm kiếm.
1. **[Tag management](02-product-catalog/07-tag-management.md)**: Thêm và quản lý tag (nhãn) cho sản phẩm nhằm hỗ trợ tìm kiếm và phân loại linh hoạt.
1. **[Attribute definition](02-product-catalog/08-attribute-definition.md)**: Định nghĩa các thuộc tính của sản phẩm như màu sắc, kích thước, chất liệu… làm nền tảng cho biến thể.
1. **[Variant creation](02-product-catalog/09-variant-creation.md)**: Tạo các biến thể từ thuộc tính (ví dụ: áo màu đỏ size M, áo màu xanh size L).
1. **[Variant pricing](02-product-catalog/10-variant-pricing.md)**: Thiết lập giá riêng cho từng biến thể nếu khác với giá mặc định của sản phẩm.
1. **[Variant stock](02-product-catalog/11-variant-stock.md)**: Quản lý tồn kho riêng cho từng biến thể thay vì chỉ ở cấp sản phẩm cha.
1. **[Bulk upload product](02-product-catalog/12-bulk-upload-product.md)**: Cho phép upload nhiều sản phẩm cùng lúc qua file (CSV/Excel) hoặc API.
1. **[Bulk update product](02-product-catalog/13-bulk-update-product.md)**: Cập nhật hàng loạt thông tin sản phẩm (giá, tồn kho, danh mục…) trong một thao tác.
1. **[Product image upload](02-product-catalog/14-product-image-upload.md)**: Upload và quản lý nhiều hình ảnh cho sản phẩm, bao gồm ảnh chính và ảnh phụ.
1. **[Product video upload](02-product-catalog/15-product-video-upload.md)**: Cho phép thêm video giới thiệu sản phẩm để tăng khả năng chuyển đổi.
1. **[SEO metadata](02-product-catalog/16-seo-metadata.md)**: Cấu hình tiêu đề SEO, meta description, slug URL để tối ưu hiển thị trên công cụ tìm kiếm.
1. **[Product publish/unpublish](02-product-catalog/17-product-publish-unpublish.md)**: Bật/tắt trạng thái hiển thị sản phẩm trên marketplace.
1. **[Schedule publish time](02-product-catalog/18-schedule-publish-time.md)**: Đặt lịch tự động publish hoặc unpublish sản phẩm vào thời điểm xác định.
1. **[Flash sale enrollment](02-product-catalog/19-flash-sale-enrollment.md)**: Đăng ký sản phẩm tham gia chương trình flash sale với giá và thời gian giới hạn.
1. **[Product approval workflow](02-product-catalog/20-product-approval-workflow.md)**: Quy trình duyệt sản phẩm bởi admin trước khi được hiển thị công khai.
1. **[Cross-sell setup](02-product-catalog/21-cross-sell-setup.md)**: Thiết lập gợi ý sản phẩm bổ sung liên quan để bán kèm (ví dụ: mua điện thoại gợi ý ốp lưng).
1. **[Upsell setup](02-product-catalog/22-upsell-setup.md)**: Thiết lập gợi ý phiên bản cao cấp hoặc giá trị cao hơn của cùng sản phẩm.
1. **[Related product](02-product-catalog/23-related-product.md)**: Liên kết sản phẩm tương tự để hiển thị trong phần “Sản phẩm liên quan”.
1. **[Digital product support](02-product-catalog/24-digital-product-support.md)**: Hỗ trợ sản phẩm số (file tải về, license key…), bao gồm cơ chế phân phối và kiểm soát truy cập.
1. **[Product report abuse](02-product-catalog/25-product-report-abuse.md)**: Cho phép người dùng báo cáo sản phẩm vi phạm chính sách (hàng giả, nội dung cấm…), kích hoạt quy trình kiểm duyệt.

## Inventory

1. **[Stock quantity update](03-inventory/01-stock-quantity-update.md)**: Cho phép seller hoặc hệ thống cập nhật số lượng tồn kho của sản phẩm hoặc từng biến thể.
1. **[Stock reservation](03-inventory/02-stock-reservation.md)**: Tạm giữ một số lượng hàng khi khách thêm vào cart hoặc tạo order để tránh bị mua trùng.
1. **[Auto deduct stock](03-inventory/03-auto-deduct-stock.md)**: Tự động trừ tồn kho khi đơn hàng được xác nhận hoặc thanh toán thành công theo rule định nghĩa.
1. **[Release reserved stock](03-inventory/04-release-reserved-stock.md)**: Hoàn lại số lượng đã giữ khi đơn bị hủy, thanh toán thất bại hoặc hết thời gian giữ chỗ.
1. **[Low stock alert](03-inventory/05-low-stock-alert.md)**: Gửi cảnh báo cho seller khi tồn kho xuống dưới ngưỡng tối thiểu đã cấu hình.
1. **[Oversell prevention](03-inventory/06-oversell-prevention.md)**: Ngăn chặn việc bán vượt quá số lượng thực tế bằng cách kiểm tra tồn kho real-time trước khi xác nhận đơn.
1. **[Warehouse management](03-inventory/07-warehouse-management.md)**: Quản lý thông tin kho hàng như địa chỉ, sức chứa, người phụ trách và trạng thái hoạt động.
1. **[Multi-warehouse](03-inventory/08-multi-warehouse.md)**: Hỗ trợ nhiều kho cho một seller hoặc hệ thống; cho phép phân bổ tồn kho theo từng kho.
1. **[Stock movement log](03-inventory/09-stock-movement-log.md)**: Ghi lại lịch sử thay đổi tồn kho (nhập kho, xuất kho, hoàn trả, điều chỉnh thủ công…) để audit.
1. **[Inventory audit](03-inventory/10-inventory-audit.md)**: Quy trình đối chiếu tồn kho thực tế với hệ thống để phát hiện sai lệch và điều chỉnh.
1. **[Backorder support](03-inventory/11-backorder-support.md)**: Cho phép nhận đơn hàng dù hết tồn kho, với trạng thái chờ nhập hàng bổ sung trước khi giao.

## Search & Discovery

1. **[Keyword search](04-search-and-discovery/01-keyword-search.md)**: Cho phép người dùng tìm sản phẩm bằng cách nhập từ khóa; hệ thống trả về danh sách kết quả phù hợp dựa trên chỉ mục tìm kiếm.
1. **[Autocomplete](04-search-and-discovery/02-autocomplete.md)**: Hiển thị gợi ý từ khóa hoặc sản phẩm khi người dùng đang nhập để tăng tốc độ tìm kiếm và giảm lỗi chính tả.
1. **[Search history](04-search-and-discovery/03-search-history.md)**: Lưu lại các từ khóa đã tìm trước đó để người dùng có thể truy cập lại nhanh chóng.
1. **[Filter by price](04-search-and-discovery/04-filter-by-price.md)**: Cho phép lọc sản phẩm theo khoảng giá xác định.
1. **[Filter by rating](04-search-and-discovery/05-filter-by-rating.md)**: Lọc sản phẩm dựa trên số sao đánh giá trung bình.
1. **[Filter by category](04-search-and-discovery/06-filter-by-category.md)**: Giới hạn kết quả tìm kiếm theo danh mục sản phẩm cụ thể.
1. **[Filter by location](04-search-and-discovery/07-filter-by-location.md)**: Lọc sản phẩm theo vị trí người bán hoặc khu vực giao hàng.
1. **[Sort by price](04-search-and-discovery/08-sort-by-price.md)**: Sắp xếp kết quả theo giá tăng dần hoặc giảm dần.
1. **[Sort by popularity](04-search-and-discovery/09-sort-by-popularity.md)**: Sắp xếp dựa trên số lượng bán, lượt xem hoặc tương tác.
1. **[Sort by newest](04-search-and-discovery/10-sort-by-newest.md)**: Hiển thị sản phẩm mới đăng trước.
1. **[Trending products](04-search-and-discovery/11-trending-products.md)**: Hiển thị các sản phẩm đang có lượng tìm kiếm hoặc mua cao trong một khoảng thời gian nhất định.
1. **[Recently viewed](04-search-and-discovery/12-recently-viewed.md)**: Hiển thị danh sách sản phẩm người dùng đã xem gần đây để dễ quay lại.
1. **[Personalized recommendation](04-search-and-discovery/13-personalized-recommendation.md)**: Đề xuất sản phẩm dựa trên hành vi, lịch sử tìm kiếm và mua hàng của từng người dùng.
1. **[Sponsored product listing](04-search-and-discovery/14-sponsored-product-listing.md)**: Cho phép sản phẩm được ưu tiên hiển thị trong kết quả tìm kiếm hoặc trang danh mục thông qua hình thức quảng cáo trả phí.

## Cart

1. **[Add to cart](05-cart/01-add-to-cart.md)**: Cho phép người dùng thêm sản phẩm hoặc biến thể vào giỏ hàng, hệ thống ghi nhận số lượng và thông tin giá tại thời điểm thêm.
1. **[Update cart quantity](05-cart/02-update-cart-quantity.md)**: Cho phép thay đổi số lượng sản phẩm trong giỏ; hệ thống kiểm tra lại tồn kho và cập nhật tổng tiền.
1. **[Remove from cart](05-cart/03-remove-from-cart.md)**: Xóa sản phẩm khỏi giỏ hàng và cập nhật lại giá trị đơn tạm tính.
1. **[Save for later](05-cart/04-save-for-later.md)**: Di chuyển sản phẩm ra khỏi giỏ chính sang danh sách lưu lại để mua sau mà không mất thông tin.
1. **[Multi-seller cart](05-cart/05-multi-seller-cart.md)**: Hỗ trợ giỏ hàng chứa sản phẩm từ nhiều seller khác nhau; hệ thống tự động tách đơn theo từng seller khi checkout.
1. **[Price revalidation](05-cart/06-price-revalidation.md)**: Kiểm tra lại giá sản phẩm trước khi thanh toán để đảm bảo không có thay đổi so với lúc thêm vào giỏ.
1. **[Stock validation](05-cart/07-stock-validation.md)**: Xác minh tồn kho thực tế trước khi cho phép tiếp tục thanh toán để tránh hết hàng.
1. **[Voucher apply](05-cart/08-voucher-apply.md)**: Cho phép nhập và áp dụng mã giảm giá; hệ thống kiểm tra điều kiện hợp lệ và tính lại tổng tiền.
1. **[Coin apply](05-cart/09-coin-apply.md)**: Cho phép sử dụng điểm thưởng hoặc coin nội bộ để giảm giá trị đơn hàng theo quy tắc định sẵn.
1. **[Auto merge guest cart](05-cart/10-auto-merge-guest-cart.md)**: Khi người dùng đăng nhập, hệ thống tự động hợp nhất giỏ hàng của khách (local/session) với giỏ hàng tài khoản đã lưu trước đó.

## Checkout & Order

1. **[Address management](06-checkout-and-order/01-address-management.md)**: Cho phép người dùng thêm, chỉnh sửa, xóa và chọn địa chỉ giao hàng hoặc xuất hóa đơn.
1. **[Shipping method selection](06-checkout-and-order/02-shipping-method-selection.md)**: Cho phép chọn phương thức vận chuyển (nhanh, tiết kiệm, hỏa tốc…) tùy theo khu vực và chính sách seller.
1. **[Shipping fee calculation](06-checkout-and-order/03-shipping-fee-calculation.md)**: Tự động tính phí vận chuyển dựa trên trọng lượng, khoảng cách, kho hàng và đơn vị vận chuyển.
1. **[Tax calculation](06-checkout-and-order/04-tax-calculation.md)**: Tính thuế (VAT, sales tax…) dựa trên địa điểm giao hàng, loại sản phẩm và quy định pháp lý.
1. **[Voucher stacking rule](06-checkout-and-order/05-voucher-stacking-rule.md)**: Xác định quy tắc cho phép hoặc không cho phép áp dụng nhiều voucher cùng lúc.
1. **[Loyalty point redemption](06-checkout-and-order/06-loyalty-point-redemption.md)**: Cho phép dùng điểm thưởng để giảm giá đơn hàng theo tỷ lệ hoặc giới hạn quy định.
1. **[Payment method selection](06-checkout-and-order/07-payment-method-selection.md)**: Cho phép chọn phương thức thanh toán như COD, thẻ tín dụng, ví điện tử, chuyển khoản…
1. **[Payment timeout](06-checkout-and-order/08-payment-timeout.md)**: Đặt thời gian giới hạn thanh toán; nếu quá thời gian mà chưa hoàn tất, đơn sẽ tự động hủy hoặc chuyển trạng thái.
1. **[Payment retry](06-checkout-and-order/09-payment-retry.md)**: Cho phép người dùng thử thanh toán lại nếu giao dịch trước đó thất bại.
1. **[Fraud scoring](06-checkout-and-order/10-fraud-scoring.md)**: Chấm điểm rủi ro giao dịch dựa trên hành vi, lịch sử, IP, thiết bị… để quyết định duyệt, giữ hoặc từ chối đơn.
1. **[Order creation](06-checkout-and-order/11-order-creation.md)**: Tạo bản ghi đơn hàng sau khi thanh toán hợp lệ, lưu toàn bộ thông tin sản phẩm, giá và người mua.
1. **[Order split by seller](06-checkout-and-order/12-order-split-by-seller.md)**: Tự động tách một giỏ hàng thành nhiều đơn con theo từng seller để xử lý độc lập.
1. **[Order state machine](06-checkout-and-order/13-order-state-machine.md)**: Quản lý vòng đời đơn hàng theo các trạng thái (Pending, Paid, Shipping, Delivered, Completed, Cancelled, Refunded…).
1. **[Order cancellation](06-checkout-and-order/14-order-cancellation.md)**: Cho phép hủy toàn bộ đơn hàng theo điều kiện và thời điểm cho phép.
1. **[Partial cancellation](06-checkout-and-order/15-partial-cancellation.md)**: Cho phép hủy một phần sản phẩm trong đơn thay vì toàn bộ.
1. **[Order confirmation](06-checkout-and-order/16-order-confirmation.md)**: Gửi xác nhận đơn hàng qua email, SMS hoặc thông báo in-app sau khi tạo thành công.
1. **[Invoice generation](06-checkout-and-order/17-invoice-generation.md)**: Tạo hóa đơn chính thức (có thông tin thuế, pháp lý) cho đơn hàng.
1. **[Receipt generation](06-checkout-and-order/18-receipt-generation.md)**: Tạo biên nhận thanh toán đơn giản xác nhận giao dịch đã hoàn tất.
1. **[Order history](06-checkout-and-order/19-order-history.md)**: Hiển thị danh sách các đơn hàng trước đây của người dùng.
1. **[Order detail view](06-checkout-and-order/20-order-detail-view.md)**: Cho phép xem chi tiết từng đơn bao gồm sản phẩm, trạng thái, thanh toán, vận chuyển và lịch sử cập nhật.

## Payment & Wallet

1. **[Wallet creation](07-payment-and-wallet/01-wallet-creation.md)**: Tự động tạo ví nội bộ cho người dùng hoặc seller để lưu trữ số dư và giao dịch trong hệ thống.
1. **[Wallet balance](07-payment-and-wallet/02-wallet-balance.md)**: Hiển thị số dư hiện tại, bao gồm số tiền khả dụng và số tiền đang bị giữ (frozen/escrow).
1. **[Wallet top-up](07-payment-and-wallet/03-wallet-top-up.md)**: Cho phép người dùng nạp tiền vào ví thông qua các phương thức thanh toán được hỗ trợ.
1. **[Wallet withdraw](07-payment-and-wallet/04-wallet-withdraw.md)**: Cho phép rút tiền từ ví về tài khoản ngân hàng hoặc phương thức thanh toán đã liên kết.
1. **[Escrow holding](07-payment-and-wallet/05-escrow-holding.md)**: Giữ tiền giao dịch tạm thời trong hệ thống cho đến khi đơn hàng hoàn tất hoặc hết thời gian khiếu nại.
1. **[Commission deduction](07-payment-and-wallet/06-commission-deduction.md)**: Tự động trừ phần trăm hoa hồng của nền tảng từ số tiền seller nhận được.
1. **[Cashback credit](07-payment-and-wallet/07-cashback-credit.md)**: Hoàn lại một phần tiền vào ví người dùng sau giao dịch theo chương trình khuyến mãi.
1. **[Transaction log](07-payment-and-wallet/08-transaction-log.md)**: Ghi lại toàn bộ lịch sử giao dịch ví gồm nạp, rút, thanh toán, hoàn tiền, hoa hồng.
1. **[Settlement cycle](07-payment-and-wallet/09-settlement-cycle.md)**: Thiết lập chu kỳ đối soát và chuyển tiền cho seller (ví dụ: T+7, T+14).
1. **[Refund to wallet](07-payment-and-wallet/10-refund-to-wallet.md)**: Hoàn tiền trực tiếp vào ví nội bộ thay vì về phương thức thanh toán ban đầu.
1. **[Refund to bank](07-payment-and-wallet/11-refund-to-bank.md)**: Hoàn tiền về tài khoản ngân hàng hoặc thẻ thanh toán của người dùng.
1. **[Chargeback handling](07-payment-and-wallet/12-chargeback-handling.md)**: Xử lý các trường hợp ngân hàng hoàn tiền cưỡng bức do người mua khiếu nại giao dịch.
1. **[Payment reconciliation](07-payment-and-wallet/13-payment-reconciliation.md)**: Đối soát dữ liệu giữa hệ thống nội bộ và cổng thanh toán để đảm bảo số liệu khớp.
1. **[Payout request](07-payment-and-wallet/14-payout-request.md)**: Cho phép seller gửi yêu cầu rút tiền từ số dư khả dụng.
1. **[Payout approval](07-payment-and-wallet/15-payout-approval.md)**: Quy trình hệ thống hoặc admin duyệt yêu cầu rút tiền trước khi thực hiện chuyển khoản.
1. **[Payout rejection](07-payment-and-wallet/16-payout-rejection.md)**: Từ chối yêu cầu rút tiền khi không đáp ứng điều kiện (ví dụ: nghi ngờ gian lận, thiếu thông tin ngân hàng).

## Shipping & Logistics

1. **[Shipping label generation](08-shipping-and-logistics/01-shipping-label-generation.md)**: Tự động tạo nhãn vận chuyển chứa thông tin người gửi, người nhận, mã đơn và mã vạch để in và dán lên kiện hàng.
1. **[Tracking code upload](08-shipping-and-logistics/02-tracking-code-upload.md)**: Cho phép seller hoặc hệ thống cập nhật mã vận đơn do đơn vị vận chuyển cung cấp.
1. **[Real-time tracking](08-shipping-and-logistics/03-real-time-tracking.md)**: Hiển thị trạng thái vận chuyển theo thời gian thực dựa trên dữ liệu từ đối tác logistics.
1. **[Delivery attempt tracking](08-shipping-and-logistics/04-delivery-attempt-tracking.md)**: Ghi nhận số lần giao hàng thất bại và lý do (không liên lạc được, người nhận vắng mặt…).
1. **[Delivery confirmation](08-shipping-and-logistics/05-delivery-confirmation.md)**: Xác nhận đơn đã giao thành công thông qua cập nhật từ hãng vận chuyển hoặc xác nhận từ người mua.
1. **[Failed delivery handling](08-shipping-and-logistics/06-failed-delivery-handling.md)**: Xử lý các trường hợp giao không thành công, bao gồm lên lịch giao lại hoặc chuyển hoàn.
1. **[Return to sender](08-shipping-and-logistics/07-return-to-sender.md)**: Quy trình hoàn hàng về người bán khi giao thất bại hoặc người mua từ chối nhận.
1. **[Shipping SLA tracking](08-shipping-and-logistics/08-shipping-sla-tracking.md)**: Theo dõi thời gian giao hàng so với cam kết (Service Level Agreement) để đánh giá hiệu suất.
1. **[Shipping fee subsidy](08-shipping-and-logistics/09-shipping-fee-subsidy.md)**: Hỗ trợ một phần hoặc toàn bộ phí vận chuyển theo chương trình khuyến mãi hoặc chính sách nền tảng.
1. **[Lost package claim](08-shipping-and-logistics/10-lost-package-claim.md)**: Xử lý khiếu nại khi kiện hàng bị thất lạc trong quá trình vận chuyển.
1. **[Insurance claim](08-shipping-and-logistics/11-insurance-claim.md)**: Quy trình yêu cầu bồi thường bảo hiểm khi hàng hóa bị mất, hư hỏng hoặc thất lạc.

## Review & Rating

1. **[Star rating](09-review-and-rating/01-star-rating.md)**: Cho phép người mua chấm điểm sản phẩm hoặc seller theo thang sao (ví dụ 1–5 sao), ảnh hưởng đến điểm đánh giá trung bình.
1. **[Text review](09-review-and-rating/02-text-review.md)**: Cho phép người mua viết nhận xét chi tiết về trải nghiệm sản phẩm hoặc dịch vụ.
1. **[Image review](09-review-and-rating/03-image-review.md)**: Cho phép đính kèm hình ảnh thực tế vào đánh giá để tăng độ tin cậy.
1. **[Video review](09-review-and-rating/04-video-review.md)**: Cho phép tải lên video đánh giá sản phẩm nhằm cung cấp trải nghiệm trực quan hơn.
1. **[Seller reply](09-review-and-rating/05-seller-reply.md)**: Cho phép người bán phản hồi công khai dưới phần đánh giá của khách hàng.
1. **[Review edit](09-review-and-rating/06-review-edit.md)**: Cho phép người mua chỉnh sửa nội dung đánh giá trong một khoảng thời gian nhất định.
1. **[Review delete](09-review-and-rating/07-review-delete.md)**: Cho phép người mua xóa đánh giá của mình hoặc admin xóa nếu vi phạm chính sách.
1. **[Review report abuse](09-review-and-rating/08-review-report-abuse.md)**: Cho phép người dùng báo cáo đánh giá có nội dung sai lệch, spam, xúc phạm hoặc vi phạm quy định.
1. **[Review moderation](09-review-and-rating/09-review-moderation.md)**: Hệ thống hoặc admin kiểm duyệt đánh giá trước hoặc sau khi hiển thị để đảm bảo tuân thủ chính sách.
1. **[Verified purchase badge](09-review-and-rating/10-verified-purchase-badge.md)**: Gắn nhãn xác nhận người đánh giá đã thực sự mua sản phẩm thông qua hệ thống.

## Dispute & Refund

1. **[Open dispute](10-dispute-and-refund/01-open-dispute.md)**: Cho phép người mua mở khiếu nại đối với đơn hàng khi có vấn đề như hàng lỗi, sai mô tả hoặc chưa nhận được hàng.
1. **[Upload evidence](10-dispute-and-refund/02-upload-evidence.md)**: Cho phép các bên (buyer/seller) tải lên hình ảnh, video hoặc tài liệu để chứng minh lập luận của mình.
1. **[Seller response](10-dispute-and-refund/03-seller-response.md)**: Cho phép người bán phản hồi khiếu nại trong thời gian quy định, đề xuất giải pháp như đổi hàng hoặc hoàn tiền.
1. **[Admin arbitration](10-dispute-and-refund/04-admin-arbitration.md)**: Cho phép admin can thiệp và đưa ra quyết định cuối cùng khi hai bên không đạt được thỏa thuận.
1. **[Partial refund](10-dispute-and-refund/05-partial-refund.md)**: Hoàn lại một phần giá trị đơn hàng mà không yêu cầu trả lại toàn bộ sản phẩm.
1. **[Full refund](10-dispute-and-refund/06-full-refund.md)**: Hoàn lại toàn bộ số tiền đơn hàng theo quyết định xử lý.
1. **[Return request](10-dispute-and-refund/07-return-request.md)**: Cho phép người mua yêu cầu trả lại hàng trước khi được hoàn tiền.
1. **[Return approval](10-dispute-and-refund/08-return-approval.md)**: Người bán hoặc hệ thống chấp nhận yêu cầu trả hàng và cung cấp hướng dẫn gửi trả.
1. **[Return rejection](10-dispute-and-refund/09-return-rejection.md)**: Từ chối yêu cầu trả hàng nếu không đáp ứng điều kiện chính sách.
1. **[Refund status tracking](10-dispute-and-refund/10-refund-status-tracking.md)**: Cho phép theo dõi tiến trình hoàn tiền từ lúc yêu cầu đến khi hoàn tất.
1. **[Escalation](10-dispute-and-refund/11-escalation.md)**: Chuyển vụ việc lên cấp xử lý cao hơn (admin hoặc bộ phận chuyên trách) khi không đạt được thỏa thuận.
1. **[Auto refund rule](10-dispute-and-refund/12-auto-refund-rule.md)**: Tự động kích hoạt hoàn tiền theo quy tắc định sẵn, ví dụ khi seller không phản hồi trong thời gian SLA.

## Communication

1. **[Buyer-seller chat](11-communication/01-buyer-seller-chat.md)**: Cho phép người mua và người bán trao đổi trực tiếp trong hệ thống về sản phẩm, đơn hàng hoặc khiếu nại.
1. **[File sharing](11-communication/02-file-sharing.md)**: Cho phép gửi và nhận tệp đính kèm (ví dụ: hóa đơn, tài liệu hướng dẫn) trong cuộc trò chuyện.
1. **[Image sharing](11-communication/03-image-sharing.md)**: Cho phép gửi hình ảnh trong chat để minh họa tình trạng sản phẩm hoặc xác nhận thông tin.
1. **[Auto reply](11-communication/04-auto-reply.md)**: Cho phép thiết lập phản hồi tự động từ phía seller khi ngoài giờ làm việc hoặc khi nhận tin nhắn mới.
1. **[Chat history](11-communication/05-chat-history.md)**: Lưu trữ toàn bộ lịch sử trò chuyện để người dùng có thể xem lại và phục vụ đối soát khi cần.
1. **[Chat moderation](11-communication/06-chat-moderation.md)**: Hệ thống hoặc admin giám sát nội dung chat nhằm phát hiện vi phạm chính sách như spam, lừa đảo hoặc trao đổi ngoài nền tảng.
1. **[User block](11-communication/07-user-block.md)**: Cho phép người dùng chặn người khác để ngăn gửi tin nhắn hoặc liên hệ tiếp.
1. **[AI chatbot](11-communication/08-ai-chatbot.md)**: Bot tự động trả lời câu hỏi phổ biến, hướng dẫn sử dụng hoặc hỗ trợ cơ bản trước khi chuyển sang người thật.
1. **[System announcement](11-communication/09-system-announcement.md)**: Gửi thông báo chung từ hệ thống đến người dùng về bảo trì, khuyến mãi hoặc thay đổi chính sách.

## Promotion & Marketing

1. **[Global voucher](12-promotion-and-marketing/01-global-voucher.md)**: Mã giảm giá áp dụng cho toàn bộ nền tảng theo điều kiện xác định (giá trị đơn tối thiểu, danh mục, thời gian).
1. **[Shop voucher](12-promotion-and-marketing/02-shop-voucher.md)**: Mã giảm giá do từng seller tạo và chỉ áp dụng cho sản phẩm trong shop đó.
1. **[Flash sale](12-promotion-and-marketing/03-flash-sale.md)**: Chương trình giảm giá mạnh trong thời gian giới hạn với số lượng sản phẩm giới hạn.
1. **[Bundle deal](12-promotion-and-marketing/04-bundle-deal.md)**: Bán nhiều sản phẩm theo gói với mức giá ưu đãi hơn so với mua lẻ.
1. **[Buy X get Y](12-promotion-and-marketing/05-buy-x-get-y.md)**: Chương trình khuyến mãi tặng thêm sản phẩm hoặc giảm giá khi mua đủ số lượng quy định.
1. **[Referral program](12-promotion-and-marketing/06-referral-program.md)**: Chương trình giới thiệu người dùng mới, thưởng cho người giới thiệu khi người được mời hoàn tất hành động nhất định.
1. **[Affiliate tracking](12-promotion-and-marketing/07-affiliate-tracking.md)**: Theo dõi và ghi nhận đơn hàng phát sinh từ link giới thiệu của đối tác để tính hoa hồng.
1. **[Campaign creation](12-promotion-and-marketing/08-campaign-creation.md)**: Cho phép marketing team tạo và quản lý các chiến dịch khuyến mãi theo thời gian, nhóm khách hàng hoặc mục tiêu cụ thể.
1. **[Discount rule engine](12-promotion-and-marketing/09-discount-rule-engine.md)**: Hệ thống định nghĩa và thực thi các quy tắc giảm giá phức tạp dựa trên điều kiện (giá trị giỏ hàng, danh mục, vai trò người dùng…).
1. **[Loyalty program](12-promotion-and-marketing/10-loyalty-program.md)**: Chương trình tích điểm hoặc xếp hạng thành viên dựa trên hành vi mua sắm để đổi ưu đãi.
1. **[Coupon usage limit](12-promotion-and-marketing/11-coupon-usage-limit.md)**: Thiết lập giới hạn sử dụng mã giảm giá theo người dùng, theo lượt hoặc tổng số lượng toàn hệ thống.
1. **[Marketing banner CMS](12-promotion-and-marketing/12-marketing-banner-cms.md)**: Công cụ quản lý nội dung banner quảng bá trên trang chủ hoặc trang danh mục.
1. **[Push campaign](12-promotion-and-marketing/13-push-campaign.md)**: Gửi thông báo đẩy đến người dùng trên web/app theo nhóm mục tiêu hoặc hành vi.
1. **[Email campaign](12-promotion-and-marketing/14-email-campaign.md)**: Gửi email marketing hàng loạt hoặc tự động theo kịch bản (abandoned cart, khuyến mãi…).
1. **[A/B testing](12-promotion-and-marketing/15-a-b-testing.md)**: Thử nghiệm nhiều phiên bản nội dung hoặc giao diện để đo lường hiệu quả và tối ưu chuyển đổi.

## Analytics & Reporting

1. **[GMV tracking](13-analytics-and-reporting/01-gmv-tracking.md)**: Theo dõi tổng giá trị giao dịch (Gross Merchandise Value) phát sinh trên nền tảng trong một khoảng thời gian.
1. **[Revenue tracking](13-analytics-and-reporting/02-revenue-tracking.md)**: Theo dõi doanh thu thực tế của nền tảng sau khi trừ chiết khấu, hoàn tiền hoặc các khoản điều chỉnh.
1. **[Conversion rate](13-analytics-and-reporting/03-conversion-rate.md)**: Đo tỷ lệ người dùng thực hiện hành động mong muốn (ví dụ: mua hàng) trên tổng số người truy cập.
1. **[Cart abandonment](13-analytics-and-reporting/04-cart-abandonment.md)**: Theo dõi tỷ lệ người dùng thêm sản phẩm vào giỏ nhưng không hoàn tất thanh toán.
1. **[Seller performance score](13-analytics-and-reporting/05-seller-performance-score.md)**: Tính điểm đánh giá hiệu suất seller dựa trên doanh số, tỷ lệ hủy đơn, phản hồi khách hàng và SLA giao hàng.
1. **[Customer LTV](13-analytics-and-reporting/06-customer-ltv.md)**: Ước tính giá trị vòng đời khách hàng (Lifetime Value) dựa trên tổng chi tiêu và tần suất mua hàng.
1. **[CAC tracking](13-analytics-and-reporting/07-cac-tracking.md)**: Theo dõi chi phí để có được một khách hàng mới (Customer Acquisition Cost) từ các kênh marketing.
1. **[Funnel tracking](13-analytics-and-reporting/08-funnel-tracking.md)**: Phân tích từng bước trong hành trình người dùng (view → add to cart → checkout → payment) để xác định điểm rơi.
1. **[Cohort analysis](13-analytics-and-reporting/09-cohort-analysis.md)**: Phân tích nhóm người dùng theo cùng thời điểm đăng ký hoặc hành vi để đánh giá retention và xu hướng mua.
1. **[Fraud analytics](13-analytics-and-reporting/10-fraud-analytics.md)**: Phân tích dữ liệu để phát hiện mô hình gian lận như tài khoản ảo, lạm dụng voucher hoặc chargeback bất thường.
1. **[Refund rate tracking](13-analytics-and-reporting/11-refund-rate-tracking.md)**: Theo dõi tỷ lệ hoàn tiền theo sản phẩm, seller hoặc danh mục để đánh giá chất lượng và rủi ro.
1. **[Inventory turnover](13-analytics-and-reporting/12-inventory-turnover.md)**: Đo tốc độ luân chuyển hàng tồn kho, cho biết thời gian trung bình để bán hết hàng.
1. **[Heatmap tracking](13-analytics-and-reporting/13-heatmap-tracking.md)**: Theo dõi hành vi tương tác trên giao diện (click, scroll, hover) để tối ưu UX và bố cục trang.

## Admin & Moderation

1. **[User management](14-admin-and-moderation/01-user-management.md)**: Cho phép admin xem, tìm kiếm, chỉnh sửa và quản lý thông tin tài khoản người dùng trong hệ thống.
1. **[Seller approval](14-admin-and-moderation/02-seller-approval.md)**: Quy trình xét duyệt hồ sơ đăng ký bán hàng trước khi cho phép seller hoạt động chính thức.
1. **[Product moderation](14-admin-and-moderation/03-product-moderation.md)**: Kiểm duyệt sản phẩm trước hoặc sau khi publish để đảm bảo tuân thủ chính sách và pháp luật.
1. **[Category management](14-admin-and-moderation/04-category-management.md)**: Tạo, chỉnh sửa, sắp xếp và phân cấp danh mục sản phẩm để phục vụ tìm kiếm và điều hướng.
1. **[Commission configuration](14-admin-and-moderation/05-commission-configuration.md)**: Thiết lập mức hoa hồng nền tảng theo danh mục, seller hoặc chương trình cụ thể.
1. **[Tax configuration](14-admin-and-moderation/06-tax-configuration.md)**: Cấu hình quy tắc tính thuế theo khu vực, loại sản phẩm hoặc mô hình kinh doanh.
1. **[Feature toggle](14-admin-and-moderation/07-feature-toggle.md)**: Bật/tắt các tính năng hệ thống theo môi trường, nhóm người dùng hoặc mục đích thử nghiệm.
1. **[Content moderation](14-admin-and-moderation/08-content-moderation.md)**: Kiểm duyệt nội dung do người dùng tạo ra như review, chat, mô tả sản phẩm, banner.
1. **[Ban account](14-admin-and-moderation/09-ban-account.md)**: Khóa hoặc vô hiệu hóa tài khoản khi phát hiện vi phạm chính sách.
1. **[System audit log](14-admin-and-moderation/10-system-audit-log.md)**: Ghi lại toàn bộ hành động quan trọng trong hệ thống (admin, user, system event) để phục vụ kiểm tra và truy vết.
1. **[Manual refund override](14-admin-and-moderation/11-manual-refund-override.md)**: Cho phép admin can thiệp và thực hiện hoàn tiền thủ công ngoài quy trình tự động.
1. **[Risk dashboard](14-admin-and-moderation/12-risk-dashboard.md)**: Hiển thị các chỉ số rủi ro như gian lận, chargeback, hành vi bất thường để admin theo dõi và xử lý.
1. **[SLA monitoring](14-admin-and-moderation/13-sla-monitoring.md)**: Theo dõi mức độ tuân thủ cam kết dịch vụ (thời gian xử lý đơn, phản hồi khiếu nại…).
1. **[Access log](14-admin-and-moderation/14-access-log.md)**: Lưu trữ lịch sử truy cập hệ thống bao gồm IP, thiết bị, thời gian và hành động thực hiện.

## Platform Infrastructure

1. **[Multi-language](15-platform-infrastructure/01-multi-language.md)**: Hệ thống hỗ trợ nhiều ngôn ngữ, cho phép người dùng chuyển đổi giao diện, nội dung sản phẩm, email, thông báo… sang các ngôn ngữ khác nhau. Thường dùng i18n framework và quản lý translation key.
1. **[Multi-currency](15-platform-infrastructure/02-multi-currency.md)**: Cho phép hiển thị và thanh toán bằng nhiều loại tiền tệ khác nhau, tự động quy đổi theo tỷ giá. Quan trọng với marketplace hoặc sản phẩm bán quốc tế.
1. **[Localization](15-platform-infrastructure/03-localization.md)**: Điều chỉnh nội dung theo khu vực (locale) như định dạng ngày tháng, số, tiền tệ, múi giờ, văn hóa hiển thị… Không chỉ dịch ngôn ngữ mà còn “bản địa hóa” trải nghiệm.
1. **[Timezone handling](15-platform-infrastructure/04-timezone-handling.md)**: Xử lý múi giờ khác nhau giữa user, server và database. Đảm bảo các mốc thời gian (đơn hàng, chat, log, báo cáo) chính xác theo vùng của người dùng.
1. **[CDN integration](15-platform-infrastructure/05-cdn-integration.md)**: Tích hợp Content Delivery Network để phân phối ảnh, video, file tĩnh qua nhiều server toàn cầu, giúp tăng tốc tải trang và giảm tải server gốc.
1. **[Caching](15-platform-infrastructure/06-caching.md)**: Lưu tạm dữ liệu (Redis, memory cache…) để giảm số lần truy vấn database hoặc gọi API, từ đó tăng tốc độ phản hồi và giảm chi phí hạ tầng.
1. **[Rate limiting](15-platform-infrastructure/07-rate-limiting.md)**: Giới hạn số lượng request trong một khoảng thời gian nhằm chống spam, DDoS hoặc lạm dụng API. Thường áp dụng cho login, OTP, public API.
1. **[API gateway](15-platform-infrastructure/08-api-gateway.md)**: Lớp trung gian quản lý tất cả API request: routing, authentication, logging, rate limit… Rất quan trọng trong kiến trúc microservices.
1. **[Webhook system](15-platform-infrastructure/09-webhook-system.md)**: Cơ chế gửi thông báo tự động đến hệ thống khác khi có sự kiện xảy ra (vd: thanh toán thành công, đơn hàng tạo mới). Thường dùng để tích hợp bên thứ ba.
1. **[Background job queue](15-platform-infrastructure/10-background-job-queue.md)**: Hệ thống xử lý tác vụ nền (gửi email, xử lý ảnh, sync dữ liệu…) thay vì xử lý trực tiếp trong request để tránh làm chậm response.
1. **[Backup system](15-platform-infrastructure/11-backup-system.md)**: Cơ chế sao lưu database và file định kỳ để đảm bảo có thể phục hồi dữ liệu khi gặp sự cố.
1. **[Disaster recovery](15-platform-infrastructure/12-disaster-recovery.md)**: Kế hoạch và kiến trúc dự phòng khi hệ thống gặp sự cố nghiêm trọng (server chết, mất vùng cloud…), bao gồm failover và restore nhanh.
1. **[Data encryption](15-platform-infrastructure/13-data-encryption.md)**: Mã hóa dữ liệu nhạy cảm khi lưu trữ (at rest) và khi truyền tải (in transit – HTTPS, TLS), nhằm bảo vệ thông tin người dùng.
1. **[GDPR compliance](15-platform-infrastructure/14-gdpr-compliance.md)**: Đảm bảo hệ thống tuân thủ quy định bảo vệ dữ liệu cá nhân (ví dụ: cho phép user yêu cầu xóa dữ liệu, export dữ liệu, quản lý consent).
1. **[Monitoring & alerting](15-platform-infrastructure/15-monitoring-alerting.md)**: Theo dõi tình trạng hệ thống (CPU, memory, error rate, latency…) và gửi cảnh báo khi có sự cố để đội kỹ thuật xử lý kịp thời.
1. **[High availability setup](15-platform-infrastructure/16-high-availability-setup.md)**: Thiết lập hệ thống có khả năng hoạt động liên tục (99.9%+ uptime) bằng cách dùng load balancing, replication, nhiều server dự phòng.
