# I. THÔNG TIN CƠ BẢN
- Nhóm sinh viên: tối đa 6 bạn
- Chọn đồ án theo gợi ý bên dưới, các em có thể chọn đề tài khác theo ý định
- Các đồ án nên xuyên suốt qua nhiều môn học để làm tăng chất lượng đề tài

## II. DANH SÁCH ĐỀ TÀI VÀ GỢI Ý TRIỂN KHAI (BPMN \+ RPA \+ CAMUNDA)

| DANH SÁCH ĐỀ TÀI VÀ GỢI Ý TRIỂN KHAI (BPMN \+ RPA \+ CAMUNDA) |
| :---- |
| **1\. Mô hình Dropshipping (Hàng từ AliExpress/1688 bán sang Mỹ) Bối cảnh:** Kinh doanh bán lẻ xuyên biên giới, người bán không giữ hàng mà chuyển đơn cho nhà cung cấp. **Quy trình nghiệp vụ:** Nhận đơn hàng từ web bán lẻ (Shopify/WooCommerce) → Hệ thống/Tool xử lý đơn hàng → Tự động đặt hàng (Place Order) bên nhà cung cấp Trung Quốc (AliExpress) → Nhà cung cấp đóng gói và ship thẳng cho khách hàng cuối → Cập nhật mã vận đơn (Tracking Number) ngược lại cho khách để theo dõi. **Ứng dụng RPA:** Đây là đất diễn chính cho RPA. Viết Bot tự động truy cập trang AliExpress, đăng nhập, điền form đặt hàng (tên, địa chỉ khách từ đơn Shopify), chọn đúng thuộc tính sản phẩm và bấm thanh toán. Bot giúp tránh sai sót nhập liệu tay hàng nghìn đơn. **Phù hợp:** Nhóm mạnh về Code/Kỹ thuật. |
| **2\. Mô hình "Box Subscription" (Hộp quà định kỳ \- VD: Mỹ phẩm/Snack) Bối cảnh:** Khách hàng trả tiền theo tháng để nhận một hộp quà bất ngờ định kỳ. **Quy trình nghiệp vụ:** Quản lý thành viên đăng ký → Lên thực đơn/bộ sưu tập sản phẩm cho tháng này → Trừ tiền thẻ tín dụng định kỳ (Recurring Payment) → Đóng gói hàng loạt → Giao hàng → Xử lý gia hạn hoặc hủy gói. **Ứng dụng Camunda:** Quản lý vòng đời gói đăng ký (Subscription Cycle). Sử dụng Timer Event: "Cứ đến ngày 25 hàng tháng, kích hoạt quy trình trừ tiền và tạo lệnh xuất kho". Xử lý ngoại lệ: Nếu trừ tiền thất bại 3 lần → Gửi email nhắc → Hủy gói. **Phù hợp:** Nhóm thiên về Business/Quản trị. |
| **3\. Kinh doanh Hàng hiệu đã qua sử dụng (Second-hand Luxury Consignment) Bối cảnh:** Sàn trung gian nhận ký gửi túi xách, đồng hồ xa xỉ. **Quy trình nghiệp vụ:** Khách gửi yêu cầu ký gửi → Gửi hàng về kho → Chuyên gia thẩm định thật/giả (Authentication) → Định giá sản phẩm → Chụp ảnh/Spa sản phẩm → Đăng bán → Khi bán được thì thanh toán cho người ký gửi (trừ hoa hồng). **Điểm nhấn BPMN:** Quy trình thẩm định rất kỹ lưỡng, có nhiều cổng rẽ nhánh (Gateway): Hàng giả → Trả lại/Tiêu hủy; Hàng thật nhưng cũ quá → Từ chối; Hàng thật đẹp → Duyệt bán. **Phù hợp:** Nhóm thiên về Business. |
| **4\. Sàn giao dịch Vé sự kiện (Ticket Reselling Platform) Bối cảnh:** Nơi mua đi bán lại vé concert, bóng đá (tránh vé giả/lừa đảo). **Quy trình nghiệp vụ:** Người bán đăng tải thông tin vé → Sàn xác thực vé → Người mua thanh toán (Sàn giữ tiền treo) → Người bán chuyển vé → Người mua đi sự kiện check-in thành công → Sàn mới nhả tiền cho người bán (Release Payment). **Ứng dụng RPA:** Bot tự động quét mã QR code hoặc Barcode trên vé người bán upload lên, đối chiếu với API của đơn vị phát hành vé gốc (Ticketbox/Ticketmaster giả lập) để verify tính hợp lệ ngay lập tức. **Phù hợp:** Nhóm Kỹ thuật. |
| **5\. Siêu thị trực tuyến (Online Grocery \- Mô hình Instacart) Bối cảnh:** Đi chợ hộ, giao hàng trong 1-2 giờ. **Quy trình nghiệp vụ:** Khách đặt đơn thực phẩm → Hệ thống điều phối cho nhân viên đi nhặt đồ (Picker) tại siêu thị gần nhất → Picker quét mã vạch sản phẩm → Nếu hết hàng: Chat với khách để đổi món tương đương hoặc hoàn tiền món đó → Thanh toán tại quầy → Giao hàng. **Ứng dụng Camunda:** Xử lý tình huống ngoại lệ phức tạp: "Hết hàng nhưng gọi khách không nghe máy". Camunda sẽ đếm ngược 5 phút, nếu không phản hồi → Tự động chọn phương án mặc định (Hoàn tiền) để Picker đi tiếp, đảm bảo KPI thời gian. **Phù hợp:** Nhóm Business. |
| **6\. Công ty "Săn đầu người" (Headhunter/Recruitment Agency) Bối cảnh:** Công ty dịch vụ tuyển dụng nhân sự cấp cao. **Quy trình nghiệp vụ:** Nhận bản mô tả công việc (JD) từ khách hàng doanh nghiệp → Tìm kiếm nguồn ứng viên (Sourcing) → Sàng lọc hồ sơ → Phỏng vấn sơ bộ → Gửi hồ sơ sang khách hàng (Shortlist) → Sắp xếp lịch phỏng vấn với khách → Đàm phán lương/Offer → Ứng viên đi làm → Bảo hành (nếu ứng viên nghỉ sớm). **Ứng dụng RPA:** Bot tự động lên LinkedIn, nhập từ khóa trong JD, quét (crawl) hàng loạt Profile ứng viên phù hợp, lưu vào Excel/Database để nhân viên lọc lại. **Phù hợp:** Nhóm Business. |
| **7\. Công ty Dịch vụ Kế toán/Thuế (Accounting Service Firm) Bối cảnh:** Làm thuê kế toán cho các doanh nghiệp nhỏ. **Quy trình nghiệp vụ:** Định kỳ hàng tháng nhận hóa đơn/chứng từ từ khách hàng (qua Email/Drive) → Phân loại hóa đơn → Nhập liệu vào phần mềm kế toán → Lên tờ khai thuế → Gửi báo cáo cho khách duyệt → Nộp thuế. **Ứng dụng RPA:** Sử dụng công nghệ OCR (Nhận diện ký tự quang học) kết hợp RPA. Bot tự động mở Email, tải file đính kèm, đọc nội dung ảnh hóa đơn, trích xuất: Ngày, Số tiền, Mã số thuế, Mặt hàng và tự điền vào Excel hoặc phần mềm MISA. **Phù hợp:** Nhóm Kỹ thuật & Business. |
| **8\. Trung tâm Dịch thuật & Bản địa hóa (Translation Agency) Bối cảnh:** Dịch thuật tài liệu đa ngôn ngữ chuyên nghiệp. **Quy trình nghiệp vụ:** Tiếp nhận tài liệu gốc → Phân tích (đếm từ, xác định chuyên ngành) → Báo giá → Gửi cho Biên dịch viên (Freelancer) → Gửi cho người Hiệu đính (Reviewer) → Kiểm tra format (DTP) → Bàn giao. **Ứng dụng Camunda:** Quản lý Deadline chặt chẽ. Nếu Biên dịch viên A không nộp bài trước giờ G → Hệ thống tự động gửi email cảnh báo hoặc re-assign (gán lại) việc cho người khác để kịp tiến độ. **Phù hợp:** Nhóm Business. |
| **9\. Công ty Quản lý Tòa nhà/Chung cư (Building Management) Bối cảnh:** Vận hành khu dân cư, xử lý sự cố điện nước. **Quy trình nghiệp vụ:** Cư dân gửi yêu cầu (vd: vỡ ống nước) qua App → Ban quản lý tiếp nhận → Điều kỹ thuật viên đi kiểm tra → Báo giá sửa chữa (nếu hỏng thiết bị riêng) → Tiến hành sửa → Cư dân nghiệm thu → Thu tiền (cộng vào phí quản lý tháng). **Ứng dụng RPA:** Bot tự động gửi thông báo qua Zalo/SMS cho cư dân khi có lịch cắt nước, hoặc gửi thông báo phí quản lý hàng tháng, nhắc nợ tự động. **Phù hợp:** Nhóm Business. |
| **10\. Công ty Thẩm định giá (Valuation Agency) Bối cảnh:** Định giá bất động sản/động sản cho mục đích vay vốn, mua bán. **Quy trình nghiệp vụ:** Nhận yêu cầu định giá → Nhân viên đi khảo sát hiện trường (chụp ảnh, đo đạc) → Tra cứu cơ sở dữ liệu giá thị trường → Lập dự thảo báo cáo → Trình Kiểm soát viên → Trình Hội đồng thẩm định giá duyệt mức giá cuối cùng → Phát hành chứng thư. **Điểm nhấn BPMN:** Mô hình hóa quy trình phê duyệt tuần tự qua nhiều cấp bậc (Approval Workflow) rất điển hình trong doanh nghiệp. **Phù hợp:** Nhóm Business. |
| **11\. Mô hình Cho vay ngang hàng (P2P Lending) Bối cảnh:** Nền tảng kết nối người cần vay và nhà đầu tư (như Tima, Fiin). **Quy trình nghiệp vụ:** Người vay đăng ký hồ sơ Online → Hệ thống chấm điểm tín dụng (Credit Scoring) → Phân loại rủi ro (A, B, C, D) → Đẩy lên sàn gọi vốn (Crowdfunding) → Nhà đầu tư góp tiền → Giải ngân → Thu hồi nợ gốc lãi hàng tháng. **Ứng dụng Camunda DMN (Decision Model and Notation):** Xây dựng bảng quy tắc chấm điểm tự động. Ví dụ: "Nếu Thu nhập \> 10tr VÀ Không nợ xấu → Điểm A". "Nếu nợ xấu nhóm 2 → Từ chối". **Phù hợp:** Nhóm Kỹ thuật. |
| **12\. Bảo hiểm du lịch quốc tế (Travel Insurance) Bối cảnh:** Bảo hiểm tự động, đặc biệt là quy trình bồi thường (Claim). **Quy trình nghiệp vụ:** Khách mua online → Cấp đơn/Giấy chứng nhận điện tử. Quy trình bồi thường: Khách báo chuyến bay bị hủy/delay → Khách gửi ảnh vé máy bay/xác nhận từ hãng → Công ty bảo hiểm thẩm định → Duyệt chi trả → Chuyển khoản. **Ứng dụng RPA:** Bot tự động truy cập website của hãng hàng không hoặc trang FlightRadar24, nhập mã chuyến bay để kiểm tra xem chuyến bay đó có thực sự bị delay như khách khai báo hay không. **Phù hợp:** Nhóm Kỹ thuật. |
| **13\. Dịch vụ Cầm đồ công nghệ (Mô hình chuỗi \- F88/Camdonhanh) Bối cảnh:** Cầm cố tài sản (Laptop, Xe máy) với quy trình định giá online. **Quy trình nghiệp vụ:** Khách gửi thông tin tài sản qua Web/App → Hệ thống định giá sơ bộ → Khách mang đồ ra cửa hàng (hoặc nhân viên đến nhà) → Thẩm định thực tế → Chốt giá → Ký hợp đồng điện tử → Giải ngân (Tiền mặt/CK) → Quản lý đóng lãi → Thanh lý nếu quá hạn. **Điểm nhấn BPMN:** Quy trình nhắc nợ và xử lý tài sản thanh lý (khi khách bùng nợ) cần vẽ chi tiết. **Phù hợp:** Nhóm Business. |
| **14\. Mở thẻ tín dụng trực tuyến (Digital Credit Card Onboarding) Bối cảnh:** Ngân hàng số, cho phép mở thẻ không cần ra quầy. **Quy trình nghiệp vụ:** Khách chụp CMND/CCCD (eKYC) → Xác thực khuôn mặt (Face Matching) → Điền thông tin thu nhập → Hệ thống tra cứu lịch sử tín dụng (CIC) → Phê duyệt hạn mức thẻ tự động → Phát hành thẻ phi vật lý (Virtual Card) để dùng ngay → Gửi thẻ cứng sau. **Điểm nhấn BPMN:** Tích hợp nhiều API của bên thứ 3 (eKYC, CIC, Core Banking) trong các bước Service Task. **Phù hợp:** Nhóm Kỹ thuật. |
| **15\. Hệ thống Quản lý Học tập (LMS \- Selling Online Courses) Bối cảnh:** Bán khóa học Video (như Udemy/Kyna). **Quy trình nghiệp vụ:** Giảng viên sản xuất khóa học → Upload lên hệ thống → Admin duyệt nội dung/chất lượng → Xuất bản khóa học → Học viên mua và thanh toán → Hệ thống cấp quyền học → Học viên hoàn thành → Cấp chứng chỉ (Certificate). **Ứng dụng RPA:** Bot tự động lấy tên học viên, ngày hoàn thành, điểm số để điền vào phôi bằng (file mẫu PDF), xuất file và gửi email chúc mừng cho học viên. **Phù hợp:** Nhóm Business. |
| **16\. Trung tâm Tư vấn Du học Bối cảnh:** Dịch vụ tư vấn giáo dục quốc tế, quy trình kéo dài nhiều tháng. **Quy trình nghiệp vụ:** Tư vấn chọn trường/ngành → Ký hợp đồng dịch vụ → Hướng dẫn chuẩn bị hồ sơ (SOP, LOR, Bảng điểm) → Dịch thuật công chứng → Nộp hồ sơ (Submit Application) → Nhận Offer → Luyện phỏng vấn Visa → Hỗ trợ đặt vé/nhà ở. **Ứng dụng Camunda:** Theo dõi tiến độ (Timeline tracking). Do mỗi trường có hạn nộp (Deadline) khác nhau, Camunda sẽ gửi cảnh báo cho nhân viên tư vấn trước 3 ngày hết hạn nộp hồ sơ. **Phù hợp:** Nhóm Business. |
| **17\. Đại lý Vé máy bay cấp 1 (OTA \- Online Travel Agent) Bối cảnh:** Bán vé máy bay trực tuyến, xử lý nghiệp vụ sau bán hàng. **Quy trình nghiệp vụ:** Tìm chuyến bay → Giữ chỗ (Booking) → Xuất vé (Ticketing) sau khi nhận tiền → Gửi mặt vé. Quy trình sau bán (quan trọng): Xử lý hoàn vé, hủy vé, đổi ngày bay theo yêu cầu khách. **Ứng dụng RPA:** Khi khách yêu cầu hủy vé, nhân viên thường phải vào web hãng làm thủ công. RPA có thể tự động đăng nhập portal đại lý của hãng (Vietnam Airlines/Vietjet), tìm mã đặt chỗ và bấm nút hủy/void vé theo quy định. **Phù hợp:** Nhóm Kỹ thuật. |
| **18\. Dịch vụ Chuyển phát nhanh nội thành (Instant Delivery \- AhaMove/GrabExpress) Bối cảnh:** Giao hàng tức thời trong nội thành. **Quy trình nghiệp vụ:** Khách đặt đơn → Hệ thống tìm tài xế gần nhất (Matching) → Tài xế nhận đơn → Đến lấy hàng (Pick-up) → Chụp ảnh xác nhận → Đi giao (Drop-off) → Thu tiền hộ (COD) → Hoàn thành → Hệ thống trừ chiết khấu và cộng tiền vào ví tài xế. **Điểm nhấn BPMN:** Xử lý các luồng: Tài xế hủy chuyến, Khách không nghe máy, Hàng bị vỡ hỏng trong quá trình giao. **Phù hợp:** Nhóm Business. |
| **19\. Kinh doanh Homestay/Airbnb (Chuỗi căn hộ) Bối cảnh:** Quản lý nhiều căn hộ cho thuê ngắn hạn trên nhiều nền tảng. **Quy trình nghiệp vụ:** Khách đặt phòng (trên Airbnb/Agoda/Booking) → Hệ thống ghi nhận lịch → Gửi hướng dẫn Check-in (Mã khóa cửa thông minh) → Khách ở → Khách Check-out → Điều phối nhân viên dọn phòng (Housekeeping) → Kiểm tra phòng → Review khách hàng. **Ứng dụng RPA:** Bot tự động đồng bộ lịch trống (Calendar Sync). Khi có khách đặt trên Airbnb, Bot lập tức vào Agoda/Booking khóa ngày đó lại để tránh bị trùng lịch (Overbooking). **Phù hợp:** Nhóm Kỹ thuật. |
| **20\. Dịch vụ Order hàng Nhật/Mỹ/Hàn (Buy-for-me Service) Bối cảnh:** Mua hộ hàng hóa quốc tế về Việt Nam. **Quy trình nghiệp vụ:** Khách gửi link sản phẩm → Nhân viên báo giá (Giá Web \+ Tax \+ Phí ship \+ Công) → Khách cọc tiền → Nhân viên mua hàng → Hàng về kho nước ngoài → Gom hàng (Consolidation) đóng chung kiện → Ship về VN → Thông quan → Giao khách và thu tiền còn lại. **Điểm nhấn BPMN:** Quy trình gom hàng (Consolidation) là phức tạp nhất: Chờ đủ hàng của nhiều khách mới đóng vào 1 thùng to để tiết kiệm cước vận chuyển. **Phù hợp:** Nhóm Business. |
| **21\. Quy trình Booking & Quản lý chiến dịch KOC/KOL (Influencer Marketing) Bối cảnh:** Agency quản lý chiến dịch quảng cáo sử dụng người có ảnh hưởng. **Quy trình nghiệp vụ:** Nhận Brief từ nhãn hàng → Tìm kiếm KOC phù hợp → Gửi mời hợp tác (Booking) → KOC lên kịch bản/quay video → Agency và Nhãn hàng duyệt Content → KOC đăng bài → Theo dõi hiệu quả (Tracking) → Nghiệm thu và thanh toán. **Ứng dụng RPA:** Bot tự động truy cập vào link bài viết (TikTok/Facebook/Youtube) của KOC hàng ngày để "cào" số liệu: Lượt xem, Lượt thả tim, Số bình luận... và cập nhật vào báo cáo Excel gửi khách hàng. **Phù hợp:** Nhóm Sáng tạo. |
| **22\. Hệ thống Quản lý Bản quyền nhạc số (Digital Rights Management) Bối cảnh:** Công ty phân phối nhạc lên Spotify/Apple Music/Youtube. **Quy trình nghiệp vụ:** Nghệ sĩ gửi file nhạc demo → Đăng ký bản quyền (Content ID) → Phân phối lên các nền tảng nghe nhạc → Thu thập dữ liệu lượt nghe định kỳ → Tính toán doanh thu (Royalty Accounting) → Chi trả cho nghệ sĩ. **Ứng dụng Camunda:** Xử lý logic chia tiền phức tạp (Revenue Sharing Rules). Ví dụ: Bài hát A có 2 ca sĩ, 1 nhạc sĩ, 1 hòa âm. Camunda DMN sẽ tính toán: Ca sĩ A hưởng 30%, Ca sĩ B 20%, Nhạc sĩ 40%... dựa trên hợp đồng. **Phù hợp:** Nhóm Business/Tech. |
| **23\. Dịch vụ Chỉnh sửa Video/Ảnh theo yêu cầu (Post-production Service) Bối cảnh:** Nền tảng kết nối Editor và Khách hàng (Uber for Editing). **Quy trình nghiệp vụ:** Khách upload file thô (Raw footage) → Hệ thống báo giá tự động theo độ dài/yêu cầu → Editor nhận việc (Claim task) → Gửi bản nháp có đóng dấu (Watermark) → Khách xem và feedback (Vòng lặp sửa lỗi) → Khách chốt → Thanh toán → Gửi file sạch (Final). **Ứng dụng RPA:** Bot tự động tải video Editor vừa làm xong, chèn Logo/Watermark "Bản Demo" vào giữa video trước khi gửi cho khách xem, giúp bảo vệ bản quyền khi chưa thanh toán. **Phù hợp:** Nhóm Sáng tạo. |
| **24\. Nền tảng Tự xuất bản sách điện tử (Self-Publishing Platform) Bối cảnh:** Tác giả tự đăng bán sách (như Amazon KDP). **Quy trình nghiệp vụ:** Tác giả upload file sách (Doc/Pdf) và bìa → Hệ thống kiểm tra lỗi định dạng tự động → Đội ngũ kiểm duyệt nội dung (tránh vi phạm bản quyền/luật pháp) → Cấp mã ISBN (nếu có) → Xuất bản lên Store → Khách mua → Ghi nhận doanh thu cho tác giả. **Điểm nhấn BPMN:** Quy trình kiểm duyệt nội dung (Content Moderation) kết hợp giữa AI check từ khóa cấm và Con người đọc lại. **Phù hợp:** Nhóm Business. |
| **25\. Hệ thống Helpdesk & Xử lý sự cố IT đa tầng (IT Incident Management) Bối cảnh:** Trung tâm hỗ trợ kỹ thuật của tập đoàn lớn. **Quy trình nghiệp vụ:** Người dùng báo lỗi (Ticket) → Bot phân loại sơ bộ → Chuyển Kỹ thuật viên cấp 1 (Tier 1 \- Lỗi cơ bản) → Nếu không sửa được → Chuyển chuyên gia cấp 2 (Tier 2 \- Lỗi sâu) → Chuyên gia cấp 3 (Tier 3 \- Lỗi hệ thống) → Đóng Ticket → Khảo sát hài lòng. **Ứng dụng Camunda:** Quản lý cam kết chất lượng dịch vụ (SLA). Nếu Tier 1 ngâm hồ sơ quá 2 tiếng không xử lý, Camunda tự động Leo thang (Escalate) chuyển thẳng lên sếp hoặc Tier 2\. **Phù hợp:** Nhóm Kỹ thuật. |
| **26\. Quy trình Tiếp thị liên kết (Affiliate Network Management) Bối cảnh:** Sàn trung gian kết nối Advertiser và Publisher (như Accesstrade). **Quy trình nghiệp vụ:** Publisher lấy link tiếp thị → Đi rải link → Khách hàng click và mua hàng → Hệ thống ghi nhận đơn hàng (Conversion) → Kiểm tra gian lận (Fraud Detection) → Đối soát với Advertiser → Thanh toán hoa hồng cho Publisher. **Ứng dụng RPA:** Bot chạy ngầm để quét các IP trùng lặp, hành vi click chuột bất thường (click farm) để gắn cờ gian lận (Flagged) trước khi thanh toán tiền. **Phù hợp:** Nhóm Kỹ thuật. |
| **27\. Dịch vụ Quản lý Chi tiêu doanh nghiệp (Corporate Expense Management) Bối cảnh:** Quản lý việc nhân viên đi công tác về thanh toán lại tiền. **Quy trình nghiệp vụ:** Nhân viên đi tiếp khách/taxi → Chụp ảnh hóa đơn, upload lên App → Sếp trực tiếp duyệt → Bộ phận Kế toán kiểm tra tính hợp lệ → Phê duyệt hoàn tiền (Reimbursement) → Tiền chuyển vào lương. **Ứng dụng RPA:** Bot tích hợp OCR tự động đọc ảnh hóa đơn taxi, bóc tách ngày giờ, số tiền để đối chiếu với quy định công tác phí (Ví dụ: Quy định chỉ được đi tối đa 200k/lần, nếu hóa đơn 300k → Cảnh báo). **Phù hợp:** Nhóm Kỹ thuật. |
| **28\. Dịch vụ Đăng ký & Gia hạn tên miền/Hosting (Domain Registrar) Bối cảnh:** Đại lý bán tên miền (như Mắt Bão, Tenten). **Quy trình nghiệp vụ:** Khách tra cứu tên miền → Đăng ký và thanh toán → Hệ thống đăng ký thông tin chủ sở hữu (Whois) lên tổ chức quốc tế → Kích hoạt DNS. Quy trình gia hạn: Nhắc phí → Khách đóng tiền → Gia hạn. Quy trình thu hồi: Khách không đóng → Khóa tạm thời → Thu hồi về kho. **Ứng dụng Camunda:** Quy trình vòng đời tên miền (Domain Lifecycle) với các mốc thời gian (Timer) cực kỳ quan trọng để tránh mất tên miền của khách. **Phù hợp:** Nhóm Kỹ thuật. |
| **29\. Dịch vụ Bác sĩ từ xa (Telemedicine Platform) Bối cảnh:** Khám bệnh qua Video Call. **Quy trình nghiệp vụ:** Bệnh nhân đặt lịch khám → Trợ lý ảo/Y tá sàng lọc triệu chứng ban đầu (Triage) → Kết nối Video Call với Bác sĩ đúng giờ → Bác sĩ chẩn đoán và kê đơn điện tử (E-Prescription) → Đơn thuốc chuyển sang nhà thuốc liên kết → Nhà thuốc giao thuốc tận nhà. **Ứng dụng Camunda:** Điều phối lịch làm việc (Scheduling). Tìm khung giờ trống chung giữa Bác sĩ và Bệnh nhân để gán lịch hẹn. **Phù hợp:** Nhóm Business. |
| **30\. Hệ thống Thi & Coi thi trực tuyến (Online Proctoring) Bối cảnh:** Tổ chức thi cử từ xa, chống gian lận. **Quy trình nghiệp vụ:** Giảng viên tạo đề thi → Thí sinh đăng nhập, xác thực khuôn mặt → Vào phòng thi ảo → Làm bài. Trong lúc làm bài: AI giám sát hành vi (quay ngang ngửa, mở tab khác). Nộp bài → Chấm điểm tự động (Trắc nghiệm) hoặc Giảng viên chấm (Tự luận) → Công bố điểm. **Ứng dụng RPA:** Bot tự động tổng hợp danh sách thí sinh bị AI đánh dấu "nghi vấn gian lận", cắt clip đoạn vi phạm gửi email cho Hội đồng thi xem xét. **Phù hợp:** Nhóm Kỹ thuật. |
| **31\. Dịch vụ Chăm sóc sức khỏe tại nhà (Home Care Booking) Bối cảnh:** Đặt lịch y tá/điều dưỡng đến nhà (lấy máu, thay băng). **Quy trình nghiệp vụ:** Khách đặt dịch vụ trên App → Hệ thống tìm Điều dưỡng viên gần nhất (tương tự Grab) → Điều dưỡng đến nhà thực hiện → Lấy mẫu xét nghiệm (nếu có) → Vận chuyển mẫu về Phòng Lab → Phòng Lab phân tích → Trả kết quả bản cứng hoặc qua App. **Điểm nhấn BPMN:** Quy trình Logistics vận chuyển mẫu xét nghiệm (bảo quản lạnh, thời gian di chuyển) là điểm trọng yếu cần vẽ kỹ. **Phù hợp:** Nhóm Business. |
| **32\. Nền tảng Cho thuê thiết bị công nghệ cao (Camera/Laptop Rental) Bối cảnh:** Cho thuê máy ảnh, lens, laptop đắt tiền. **Quy trình nghiệp vụ:** Khách chọn thiết bị → Hệ thống thẩm định uy tín khách (để quyết định có cần cọc 100% giá trị máy hay không) → Giao máy → Khách sử dụng → Trả máy → Nhân viên kỹ thuật kiểm tra hư hỏng/trầy xước → Hoàn cọc (trừ phí sửa chữa nếu có). **Điểm nhấn BPMN:** Quy trình xử lý tranh chấp (Dispute) khi máy bị hỏng: Lỗi do khách hay lỗi phần cứng tự phát sinh? **Phù hợp:** Nhóm Business. |
| **33\. Dịch vụ Giặt ủi công nghệ (E-Laundry) Bối cảnh:** Dịch vụ giặt ủi giao nhận tận nơi, quản lý từng món đồ. **Quy trình nghiệp vụ:** Shipper đến nhận đồ bẩn → Gắn Tag định danh cho từng túi/món → Mang về xưởng → Phân loại (Giặt khô/Giặt ướt/Tẩy) → Giặt & Sấy → Ủi & Gấp → Đóng gói → Bàn giao Shipper giao lại cho khách. **Điểm nhấn BPMN:** Quy trình theo dõi (Tracking) từng món đồ trong dây chuyền để đảm bảo không bị thất lạc tất/áo của khách. **Phù hợp:** Nhóm Business. |
| **34\. Ứng dụng Cứu hộ giao thông 24/7 (Roadside Assistance App) Bối cảnh:** Ứng dụng gọi xe cứu hộ/vá xe lưu động. **Quy trình nghiệp vụ:** Khách báo sự cố (Hỏng xe/Hết bình) kèm vị trí GPS → Hệ thống tìm Gara/Thợ sửa gần nhất → Gara báo giá → Khách đồng ý → Thợ đến sửa → Nghiệm thu & Thanh toán. **Ứng dụng Camunda:** Sử dụng Timer Event cho việc điều phối. Nếu Gara A được mời nhưng sau 3 phút không bấm "Nhận việc" → Hệ thống tự động chuyển yêu cầu sang Gara B xa hơn một chút. **Phù hợp:** Nhóm Business. |
| **35\. Nền tảng Quản lý trạm sạc xe điện (EV Charging Management) Bối cảnh:** Mạng lưới trạm sạc công cộng (như VinFast). **Quy trình nghiệp vụ:** Tài xế tìm trạm trên App → Đặt chỗ trước (Reservation) để giữ chỗ sạc trong 15p → Đến trạm, quét QR để mở khóa trụ sạc → Cắm sạc → Hệ thống đếm số điện tiêu thụ → Tự động trừ tiền trong Ví điện tử khi rút sạc → Xuất hóa đơn. **Điểm nhấn BPMN:** Luồng tương tác giữa Phần mềm (App) và Phần cứng (Trụ sạc IoT) thông qua API. **Phù hợp:** Nhóm Kỹ thuật. |
| **36\. Dịch vụ Công chứng trực tuyến (E-Notary) Bối cảnh:** Công chứng giấy tờ không cần ra văn phòng (áp dụng ở một số quốc gia/bối cảnh giả định). **Quy trình nghiệp vụ:** Khách upload tài liệu PDF → Đặt lịch hẹn → Video Call với Công chứng viên để xác thực danh tính (cầm CMND giơ lên cam) → Công chứng viên ký số (Digital Signature) → Hệ thống đóng dấu thời gian (Timestamp) → Khách nhận file đã công chứng. **Ứng dụng RPA:** Bot hỗ trợ tra cứu dữ liệu cư dân từ Cơ sở dữ liệu quốc gia (giả lập) để xác minh CMND khách đưa ra là thật hay giả. **Phù hợp:** Nhóm Business. |
| **37\. Bảo hiểm Rơi vỡ màn hình điện thoại (Screen Protection Plan) Bối cảnh:** Bảo hiểm ngách (Micro-insurance) bán kèm khi mua điện thoại. **Quy trình nghiệp vụ:** Khách tải App bảo hiểm → App yêu cầu khách đứng trước gương chụp ảnh màn hình điện thoại (để AI check xem màn hình có đang vỡ không) → Nếu màn hình tốt → Cho phép mua gói bảo hiểm → Kích hoạt. Khi vỡ màn hình: Khách báo claim → Mang ra tiệm liên kết sửa → Bảo hiểm thanh toán cho tiệm. **Phù hợp:** Nhóm Sáng tạo. |
| **38\. Dịch vụ Đòi bồi thường chuyến bay (Flight Compensation Service) Bối cảnh:** Công ty luật thay mặt khách hàng đòi tiền hãng bay khi bị delay (Châu Âu/Mỹ rất phổ biến). **Quy trình nghiệp vụ:** Khách nhập mã chuyến bay bị hủy/delay → Hệ thống tự động kiểm tra luật hàng không (có đủ điều kiện đòi tiền không) → Nếu được: Tự động tạo đơn khiếu nại (Claim Letter) gửi hãng bay → Theo dõi phản hồi → Nếu hãng trả tiền: Trừ phí dịch vụ (25%) rồi chuyển cho khách. **Ứng dụng RPA:** Bot đóng vai trò "người đòi nợ": Tự động gửi email nhắc nhở hãng bay mỗi ngày nếu hãng không trả lời, tự động kiểm tra tài khoản ngân hàng xem tiền về chưa. **Phù hợp:** Nhóm Kỹ thuật (Rất hay). |
| **39\. Quản lý Sự kiện ảo/Hội thảo Webinar (Virtual Event Platform) Bối cảnh:** Tổ chức hội thảo trực tuyến chuyên nghiệp. **Quy trình nghiệp vụ:** Tạo Landing page sự kiện → Bán vé/Đăng ký → Gửi email chứa link tham dự (Zoom/Meet) → Check-in người tham dự (bằng cách click link) → Trong sự kiện: Ghi nhận tương tác (Poll/Q\&A) → Kết thúc: Gửi tài liệu và cấp chứng nhận (Certificate) tham gia. **Ứng dụng RPA:** Tự động xuất danh sách người tham dự (kèm câu hỏi họ đã đặt) ra file Excel, phân loại "Khách hàng tiềm năng" (Warm Leads) để chuyển cho bộ phận Sales gọi điện chăm sóc. **Phù hợp:** Nhóm Sáng tạo. |
| **40\. Dịch vụ "Mystery Box" NFT (Kinh doanh vật phẩm số) Bối cảnh:** Game Fi hoặc Sưu tầm số. **Quy trình nghiệp vụ:** Mở bán đợt Hộp mù (Blind Box) → Người dùng nạp tiền (Crypto/Fiat) mua hộp → Hệ thống chạy thuật toán ngẫu nhiên (Random) để mở ra vật phẩm (Thẻ thường/Thẻ hiếm) → Vật phẩm được lưu vào Ví người dùng → Người dùng đăng bán trên Chợ (Marketplace) → Khớp lệnh mua bán → Trừ phí sàn. **Lưu ý:** Tập trung mô tả quy trình giao dịch và xử lý ví tiền (Wallet), không cần đi sâu vào code Blockchain phức tạp. **Phù hợp:** Nhóm Sáng tạo. |
| **41\. Hệ thống So sánh giá & Theo dõi giá TMĐT (Price Intelligence Platform) Bối cảnh:** Trang web giúp người mua tìm giá rẻ nhất giữa Shopee, Tiki, Lazada và kiếm tiền từ Affiliate. **Quy trình nghiệp vụ:** (1) Thu thập: Hệ thống định kỳ truy cập các sàn TMĐT lấy giá sản phẩm. (2) So khớp: Ghép nối sản phẩm giống nhau giữa các sàn. (3) Cảnh báo: Nếu giá giảm xuống mức khách mong muốn → Gửi Email/Noti. (4) Affiliate: Điều hướng khách mua qua link tiếp thị → Đối soát doanh thu hoa hồng. **Ứng dụng RPA & Camunda:** Đề tài **"Best Choice"** cho việc kết hợp. **RPA** dùng để cào dữ liệu (Crawl Data) từ các web bán hàng. **Camunda** đóng vai trò "Nhạc trưởng" điều phối: Lập lịch cho Bot chạy (ví dụ 12h đêm), xử lý lỗi khi Bot bị chặn IP, kích hoạt luồng gửi Email hàng loạt. **Phù hợp:** Mọi nhóm (Đặc biệt khuyến khích vì tính thực tế và hiện đại). |

---

## III. DÀN Ý CHI TIẾT CHO ĐỒ ÁN

### Tên Đề Tài (Ví dụ):

**PHÂN TÍCH VÀ THIẾT KẾ LẠI QUY TRÌNH [TÊN QUY TRÌNH] TẠI CÔNG TY [TÊN CÔNG TY]**
*(Ví dụ: Quy trình Xử lý Đổi trả hàng và Hoàn tiền tại Sàn TMĐT XYZ)*

---

### CHƯƠNG 1: TỔNG QUAN (INTRODUCTION)

*Mục đích: Giới thiệu "Sân khấu" nơi quy trình diễn ra.*

1. **Giới thiệu doanh nghiệp (Giả định):**
* Tên công ty, lĩnh vực hoạt động (VD: Sàn TMĐT mô hình C2C).
* Cơ cấu tổ chức sơ bộ (Sơ đồ tổ chức - Org Chart): Chỉ ra các phòng ban liên quan đến quy trình (Kho, CSKH, Kế toán, Vận chuyển...).


2. **Phạm vi quy trình (Process Scope):**
* Điểm bắt đầu (Start Event): Khi khách bấm nút "Yêu cầu trả hàng".
* Điểm kết thúc (End Event): Khi tiền về ví khách hoặc yêu cầu bị từ chối.


3. **Lý do chọn đề tài:** Tại sao quy trình này quan trọng? (VD: Ảnh hưởng trực tiếp đến uy tín sàn và trải nghiệm khách hàng).

### CHƯƠNG 2: MÔ HÌNH HÓA HIỆN TRẠNG (AS-IS PROCESS)

*Mục đích: Vẽ lại cách làm việc "cũ", thường là thủ công hoặc bán tự động.*

1. **Mô tả quy trình hiện tại (Narrative):**
* Kể lại câu chuyện quy trình bằng lời văn. Dựa trên dữ liệu khảo sát (đóng vai/tham khảo tài liệu Seller Uni như đã bàn).
* Ví dụ: "Hiện tại, nhân viên CSKH phải mở email kiểm tra ảnh bằng chứng thủ công, sau đó nhập liệu vào Excel..."


2. **Sơ đồ BPMN hiện trạng (AS-IS Diagram):**
* Vẽ sơ đồ quy trình chi tiết.
* **Lưu ý:** Thể hiện rõ các điểm yếu (bàn giao qua lại nhiều, chờ đợi lâu, dùng giấy tờ/Excel rời rạc).


3. **Ma trận trách nhiệm (RACI Matrix):**
* Kẻ bảng liệt kê ai làm gì (Responsible), ai chịu trách nhiệm chính (Accountable), ai cần được tư vấn (Consulted), ai cần được thông báo (Informed).
* *Phần này giúp nhóm 6 người có việc để làm chi tiết.*



### CHƯƠNG 3: PHÂN TÍCH VÀ ĐÁNH GIÁ (ANALYSIS & DIAGNOSIS)

*Mục đích: "Vạch lá tìm sâu" - Đây là chương quan trọng nhất để lấy điểm cao.*

1. **Các chỉ số đo lường hiệu quả (KPIs):**
* Thời gian chu kỳ (Cycle time): Mất bao lâu để xong 1 đơn?
* Tỷ lệ lỗi (Error rate): Bao nhiêu % đơn bị xử lý sai?
* Chi phí (Cost): Tốn bao nhiêu tiền nhân sự cho 1 đơn?


2. **Xác định các vấn đề (Pain Points/Bottlenecks):**
* **Nút thắt cổ chai:** Việc bị ùn ứ ở đâu? (VD: Tại bộ phận kiểm hàng do thiếu người).
* **Sự lãng phí:** Bước nào thừa? (VD: Phải in phiếu ra giấy rồi lại nhập vào máy).
* **Rủi ro:** Gian lận ở đâu?


3. **Nguyên nhân gốc rễ (Root Cause Analysis):**
* Sử dụng biểu đồ **Xương cá (Fishbone Diagram)** hoặc **5 Whys** để tìm nguyên nhân.
* Ví dụ: Chậm trễ -> Do phần mềm cũ + Do quy trình duyệt qua 3 cấp không cần thiết.



### CHƯƠNG 4: THIẾT KẾ QUY TRÌNH TƯƠNG LAI (TO-BE PROCESS)

*Mục đích: Đưa ra giải pháp cải tiến.*

1. **Các đề xuất cải tiến:**
* **Tự động hóa (Automation):** Thay người bằng hệ thống (VD: Hệ thống tự động duyệt hoàn tiền cho các đơn dưới 50k).
* **Loại bỏ (Elimination):** Bỏ bước phê duyệt trung gian.
* **Song song hóa (Parallelism):** Thực hiện 2 bước cùng lúc thay vì chờ nhau.


2. **Sơ đồ BPMN đề xuất (TO-BE Diagram):**
* Vẽ lại quy trình mới.
* Sử dụng các ký hiệu nâng cao (Service Task, Send/Receive Task) để thể hiện sự tự động hóa.


3. **Mô tả chi tiết các bước thay đổi:**
* Giải thích rõ tại sao bước này lại khác so với AS-IS.
* Mô tả luồng dữ liệu (Data Flow) trong các bước quan trọng.


### CHƯƠNG 5 - CÀI ĐẶT VÀ TRIỂN KHAI THỰC NGHIỆM

**5.1. Kiến trúc giải pháp (Solution Architecture)**

* **Orchestrator (Nhạc trưởng):** Camunda Run (hoặc Camunda Platform 7/8). Đóng vai trò điều phối luồng quy trình.
* **Human Task (Tác vụ người dùng):** Sử dụng Camunda Tasklist để nhân viên vào duyệt/nhập liệu.
* **Automated Task (Tác vụ tự động - RPA):** Robot (Bot) thực hiện các công việc lặp lại.
* **Giao tiếp:** Thông qua REST API hoặc External Task Pattern.

**5.2. Kịch bản Demo (Use Case Scenario)**

* Chọn 1 luồng nhỏ nhưng quan trọng để demo.
* *Ví dụ (Quy trình Trả hàng):* Khách yêu cầu trả hàng -> **Bot tự động vào web đơn vị vận chuyển tra cứu hành trình** -> Nếu đã giao thành công -> Chuyển nhân viên duyệt -> Nhân viên duyệt OK -> **Bot tự động cập nhật Google Sheet/Excel kế toán**.

**5.3. Cài đặt trên Camunda Modeler**

* Thiết kế lại BPMN trên Camunda Modeler (file `.bpmn`).
* Cấu hình các thuộc tính kỹ thuật (Executable, Assignee, Topic Name).
* Thiết kế Form nhập liệu (Camunda Forms) cho các bước của người dùng.

**5.4. Xây dựng Robot RPA**

* Giới thiệu công cụ: UiPath (kéo thả) hoặc Python Selenium (Code).
* Mô tả logic của Bot: Mở trình duyệt -> Login -> Cào dữ liệu -> Trả kết quả về Camunda.

**5.5. Kết quả chạy thử nghiệm (Demo Run)**

* Quay video màn hình hoặc demo trực tiếp tại lớp.


### CHƯƠNG 6: SO SÁNH VÀ KẾT LUẬN

*Mục đích: Chứng minh giải pháp của nhóm có hiệu quả.*

1. **So sánh AS-IS và TO-BE:**
* Kẻ bảng so sánh: Số lượng bước (giảm bao nhiêu?), Thời gian ước tính (giảm bao nhiêu?), Số người tham gia.


2. **Mô phỏng (Simulation - Nếu dùng Bizagi):**
* Chạy mô phỏng để ra biểu đồ chứng minh thời gian chờ giảm xuống. (Nếu không chạy được phần mềm thì lập bảng tính Excel ước lượng).


3. **Kết luận chung & Hướng phát triển.**

---

### IV. GỢI Ý: HƯỚNG DẪN KỸ THUẬT CHI TIẾT (HOW-TO)

Để nhóm 6 người làm được phần này, bạn cần chia việc rạch ròi giữa đội **Business** (Vẽ) và **Tech** (Code/Cấu hình).

#### Bước 1: Chuẩn hóa quy trình trên Camunda Modeler

* Tải **Camunda Modeler** (Desktop app).
* Vẽ quy trình TO-BE. Lưu ý quan trọng:
* Với bước người làm (User Task): Cần gán `Assignee` (ví dụ: `demo`).
* Với bước Bot làm (Service Task): Chọn `Implementation` là `External`, đặt `Topic` là tên nhiệm vụ (ví dụ: `check-shipping-status`).
* Tích vào ô `Executable` ở cấp độ Process.



#### Bước 2: Cài đặt Camunda Platform (Server)

* Tải **Camunda Run** (bản nhẹ nhất, chỉ cần giải nén và chạy file `start.bat` hoặc `start.sh`).
* Truy cập `localhost:8080` để vào Cockpit (Quản trị) và Tasklist (Cho người dùng làm việc).
* Deploy file `.bpmn` từ Modeler vào Server này.

#### Bước 3: Xây dựng RPA Bot (Kết nối Camunda)

Đây là phần "ăn tiền". Bạn có 2 cách tùy vào năng lực nhóm:

* **Cách 1: Dùng Python (Khuyên dùng cho dân IT/MIS)**
* Dùng thư viện `camunda-external-task-client-python`.
* Dùng thư viện `Selenium` để điều khiển trình duyệt (giả lập RPA).
* *Cơ chế:* Code Python sẽ "lắng nghe" Camunda. Khi quy trình chạy đến bước `check-shipping-status`, Python sẽ tự bật trình duyệt lên, tra cứu, rồi gửi kết quả lại cho Camunda.


* **Cách 2: Dùng UiPath (Khuyên dùng cho dân Kinh tế/Business)**
* Dùng UiPath Studio (Community Edition).
* Tải gói `Camunda.UiPath.Integration`.
* Dùng Activity `Poll External Task` để nhận lệnh từ Camunda và thực hiện thao tác trên màn hình.



#### Bước 4: Demo tích hợp (Kịch bản trình diễn)

Khi báo cáo, hãy sắp xếp màn hình để Giảng viên thấy sự tương tác:

1. **Màn hình 1 (Camunda Tasklist):** Sinh viên đóng vai khách hàng điền Form "Yêu cầu trả hàng". Bấm Submit.
2. **Màn hình 2 (RPA Visual):** Ngay lập tức, một trình duyệt web (hoặc Excel) **tự động bật lên** (không ai chạm vào chuột). Nó tự điền mã đơn hàng, lấy trạng thái, rồi tự tắt. -> *Đây là lúc cả lớp sẽ "Wow".*
3. **Màn hình 3 (Camunda Cockpit):** Quy trình tự động nhảy sang bước tiếp theo (Ví dụ: "Phê duyệt hoàn tiền") dựa trên kết quả Bot vừa lấy được.

---

### PHÂN CÔNG LẠI CÔNG VIỆC (QUAN TRỌNG)

Với khối lượng việc mới này, cần điều chỉnh nhân sự nhóm 6 người:

1. **Nhóm Business Analyst (2 người):**
* Vẫn phụ trách khảo sát, vẽ AS-IS, viết báo cáo chương 1-3.
* Viết kịch bản chi tiết cho Demo (Input là gì, Output mong muốn là gì).


2. **Nhóm Camunda Engineer (2 người):**
* Cài đặt Camunda Run.
* Vẽ lại quy trình trên Camunda Modeler (cấu hình kỹ thuật).
* Tạo các Form nhập liệu (HTML đơn giản hoặc Camunda Form JSON).


3. **Nhóm RPA Developer (2 người):**
* Code Python hoặc vẽ luồng UiPath.
* Đảm bảo Bot chạy được trên máy demo mà không lỗi.
* Kết nối Bot với Camunda (đảm bảo biến dữ liệu truyền đi truyền lại đúng).



### Mẹo nhỏ khi Demo

* **Đừng demo toàn bộ quy trình dài:** Chỉ demo một phân đoạn (Segment) có chứa đủ 3 yếu tố: *Người nhập -> Máy chạy -> Người duyệt*.
* **Chuẩn bị video dự phòng:** Demo trực tiếp (Live Demo) rất dễ lỗi (hiệu ứng Demo). Hãy quay màn hình lại quá trình chạy thành công ở nhà để phòng hờ trường hợp máy treo tại lớp.
* **Nhấn mạnh tính "Không chạm" (Touchless):** Khi Bot đang chạy, hãy giơ hai tay lên cao để giảng viên thấy là "Em không hề điều khiển chuột, Bot đang tự làm".

---

## V. GỢI Ý VỀ CÁCH KHẢO SÁT: Chiến lược khảo sát khi "Doanh nghiệp không cung cấp Data"
Hiểu được khó khăn về dữ liệu là một điểm cộng lớn. Giảng viên thường đánh giá cao sinh viên biết cách "Reverse Engineering" (Kỹ thuật đảo ngược) quy trình từ các nguồn công khai hơn là việc các bạn có số liệu nội bộ (vì điều đó thường bất khả thi với sinh viên).

Các bạn không cần lẻn vào kho Tiki hay Shopee để vẽ được quy trình. Hãy dùng các phương pháp sau để xây dựng dữ liệu **Giả định hợp lý (Logical Assumption)**:

#### Cách 1: Khai thác "Học viện Người bán" (Seller University/Academy) - *Cách hiệu quả nhất*

Các sàn TMĐT (Shopee, Lazada, TikTok, Amazon) đều có kho tài liệu khổng lồ dạy người bán cách vận hành. Đây chính là **quy trình chuẩn** được công khai.

* **Hành động:** Vào *Shopee Uni* hoặc *Lazada University*. Tìm đọc các bài hướng dẫn như: "Quy trình xử lý đơn hàng chuẩn", "Quy trình tham gia Flash Sale", "Quy trình khiếu nại".
* **Kết quả:** Bạn có sơ đồ luồng đi, thời gian quy định (SLA), và các bước bắt buộc mà không cần hỏi ai cả.

#### Cách 2: Phương pháp "Mystery Shopping" (Khách hàng bí mật)

Nhóm 6 người hãy tự đóng vai các mắt xích trong chuỗi.

* **Hành động:**
1. Cử 1 bạn mở một gian hàng ảo (bán đồ cũ, đồ handmade).
2. Cử 1 bạn đóng vai khách đặt mua.
3. Cử 1 bạn thử... yêu cầu trả hàng/hoàn tiền.
4. Cử 1 bạn thử... chat chửi shop để xem quy trình báo cáo/chặn.


* **Ghi chép:** Chụp màn hình từng thông báo (notification), email nhận được, thời gian chờ duyệt. Từ các giao diện (UI) này, các bạn suy ngược ra quy trình (Backend) phía sau.

#### Cách 3: Phỏng vấn "Vi mô" (Micro-Interview)

Đừng cố xin phỏng vấn Giám đốc Lazada. Hãy tìm những người dễ tiếp cận hơn:

* **Shipper:** Hỏi anh shipper hay giao hàng cho bạn: *"Anh nhận đơn trên app thế nào? Nếu em không nghe máy thì anh phải bấm nút nào trên app? Quy trình trả về kho ra sao?"*
* **Chủ shop online nhỏ:** Bạn bè, người quen bán hàng online. Hỏi họ cách họ in đơn, đóng gói và đối soát tiền với sàn.
* **Nhân viên kho/CSKH:** Tìm trên LinkedIn hoặc các Group Facebook ("Hội tâm sự Shipper", "Cộng đồng Seller"), đăng bài khảo sát ẩn danh xin quy trình làm việc chung.

#### Cách 4: Phân tích Dựa trên Giao diện (UI-based Process Mapping)

Quy tắc vàng: **"Nếu trên App có nút bấm, thì phía sau phải có một Task xử lý".**

* *Ví dụ:* Trên App có nút "Đã nhận được hàng".
* *Suy ra BPMN:* Khi khách bấm nút này -> Hệ thống kích hoạt Task "Giải phóng tiền cho người bán" -> Gửi Message "Cập nhật ví tiền".

---

### Lời khuyên cho Đồ án

Khi viết báo cáo, hãy thành thật về nguồn dữ liệu để tăng tính thuyết phục:

> *"Do giới hạn về bảo mật thông tin doanh nghiệp, nhóm thực hiện xây dựng quy trình TO-BE dựa trên phương pháp **Black-box Testing** (Kiểm thử hộp đen) thông qua việc trải nghiệm thực tế dịch vụ, kết hợp tham khảo tài liệu hướng dẫn vận hành công khai của Shopee University dành cho đối tác bán hàng."*

Câu này sẽ giúp các bạn tránh bị Giảng viên bắt bẻ là "số liệu bịa" và chứng minh được tư duy phân tích sắc bén của nhóm.

