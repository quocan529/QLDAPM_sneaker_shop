# Bản quản lý phạm vi dự án SneakerShop

## 1. Thông tin chung

| Nội dung | Mô tả |
|---|---|
| Tên dự án | SneakerShop - Website thương mại điện tử bán giày sneaker |
| Loại dự án | Phát triển website bán hàng trực tuyến và hệ thống quản trị |
| Phiên bản phạm vi | 1.0 |
| Ngày lập | 24/09/2026 |
| Công nghệ chính | PHP 8.x, MySQL 8.0, HTML/CSS/JavaScript, Bootstrap 5 |
| Đối tượng sử dụng | Khách hàng, quản trị viên, nhân viên vận hành |
| Môi trường triển khai | XAMPP hoặc Docker/Apache, cơ sở dữ liệu MySQL |

> Tài liệu này là đường cơ sở để xác định dự án phải làm gì, không làm gì, khi nào được xem là hoàn thành và cách xử lý yêu cầu phát sinh.

## 2. Mục đích dự án

Mục đích là định hướng tổng quát, không dùng trực tiếp để đo lường từng hạng mục:

- Xây dựng một kênh bán giày sneaker trực tuyến thuận tiện, tin cậy và dễ sử dụng.
- Hỗ trợ khách hàng tìm hiểu sản phẩm, đặt hàng, thanh toán và theo dõi đơn hàng trên cùng một hệ thống.
- Hỗ trợ cửa hàng quản lý sản phẩm, biến thể size/màu, nhập hàng, tồn kho, mã giảm giá, đơn hàng và người dùng.
- Số hóa các hoạt động bán hàng và quản trị, giảm phụ thuộc vào việc ghi nhận thủ công qua điện thoại, tin nhắn hoặc bảng tính.
- Tạo nền tảng có thể triển khai trên môi trường máy chủ thực tế và mở rộng thêm tính năng sau phiên bản đầu tiên.

## 3. Mục tiêu dự án theo SMART

Các mục tiêu dưới đây cụ thể hóa mục đích. Mục tiêu phải có chỉ số kiểm tra và thời hạn; khi toàn bộ mục tiêu đạt được, mục đích dự án được xem là đạt ở phạm vi phiên bản này.

| Mã | Mục tiêu SMART | Tiêu chí đo lường/nghiệm thu | Thời hạn dự kiến |
|---|---|---|---|
| OBJ-01 | Hoàn thiện website bán sneaker cho khách hàng | Có các luồng xem sản phẩm, tìm kiếm, xem chi tiết, giỏ hàng và đặt hàng chạy được trên môi trường cài đặt chuẩn | Kết thúc giai đoạn phát triển |
| OBJ-02 | Cung cấp danh mục sản phẩm có biến thể | Mỗi sản phẩm có thể quản lý mã, tên, danh mục, giá vốn, tỷ lệ lợi nhuận, ảnh, thương hiệu, chất liệu, xuất xứ, size, màu và số lượng tồn | Kết thúc giai đoạn quản lý sản phẩm |
| OBJ-03 | Hoàn thiện quy trình đặt hàng | Người dùng đăng nhập có thể tạo đơn với thông tin giao hàng, chọn COD hoặc thanh toán trực tuyến; đơn được lưu cùng chi tiết sản phẩm | Trước nghiệm thu hệ thống |
| OBJ-04 | Tích hợp thanh toán trực tuyến | Có luồng VNPay và ZaloPay sandbox; trạng thái thanh toán và trạng thái đơn được cập nhật qua URL trả về/callback trong môi trường kiểm thử | Trước nghiệm thu thanh toán |
| OBJ-05 | Kiểm soát tồn kho theo biến thể | Khi tạo đơn, hệ thống kiểm tra và trừ đúng tồn theo sản phẩm, size, màu; không cho đặt vượt số lượng tồn | Trước nghiệm thu nghiệp vụ |
| OBJ-06 | Cung cấp khu vực quản trị | Admin có dashboard và các màn hình quản lý sản phẩm, danh mục, nhập hàng, đơn hàng, mã giảm giá, người dùng, tồn kho và báo cáo | Trước nghiệm thu quản trị |
| OBJ-07 | Cung cấp khuyến mãi có kiểm soát | Admin tạo được mã giảm theo tiền hoặc phần trăm, giới hạn thời gian/lượt dùng/phạm vi; khách có thể kiểm tra và áp dụng mã hợp lệ | Trước nghiệm thu khuyến mãi |
| OBJ-08 | Đảm bảo các yêu cầu bảo mật nền tảng | Mật khẩu được băm; phân quyền admin/customer; session admin tách biệt; dữ liệu đầu vào được kiểm tra và truy vấn quan trọng dùng prepared statement | Trước nghiệm thu bảo mật |
| OBJ-09 | Đạt khả năng vận hành cơ bản | Có tài liệu cài đặt, cấu hình biến môi trường, sao lưu cơ sở dữ liệu và hướng dẫn chạy local/Docker | Khi bàn giao |
| OBJ-10 | Hoàn thành trong giới hạn nguồn lực | Phiên bản 1.0 được bàn giao trong khoảng 8-10 tuần, với ngân sách phát triển dự kiến không vượt mức được phê duyệt | Cuối dự án |

### 3.1. Quan hệ giữa mục đích và mục tiêu

- Mục đích trả lời câu hỏi: **Dự án muốn tạo ra giá trị gì?**
- Mục tiêu trả lời câu hỏi: **Cần hoàn thành những kết quả cụ thể nào để chứng minh mục đích đã đạt được?**
- OBJ-01 đến OBJ-05 phục vụ trải nghiệm mua hàng và vận hành đơn hàng.
- OBJ-06 đến OBJ-08 phục vụ quản trị, kiểm soát và an toàn hệ thống.
- OBJ-09 đến OBJ-10 phục vụ khả năng bàn giao, triển khai và kiểm soát nguồn lực.
- Không mục tiêu nào được xem là hoàn thành chỉ dựa trên việc viết mã; phải có tiêu chí kiểm tra hoặc nghiệm thu tương ứng.

## 4. Phạm vi dự án

Phạm vi là danh sách những gì dự án phải thực hiện và những gì được loại trừ trong phiên bản 1.0.

### 4.1. Phạm vi sản phẩm: phải thực hiện

#### A. Chức năng dành cho khách hàng

- Xem trang chủ, danh mục và sản phẩm đang kinh doanh.
- Tìm kiếm sản phẩm theo tên/mã và lọc theo danh mục, khoảng giá.
- Xem thông tin chi tiết: ảnh, mô tả, thương hiệu, chất liệu, xuất xứ, giá, size, màu và tồn kho.
- Đăng ký, đăng nhập, đăng xuất và quản lý thông tin tài khoản.
- Chọn biến thể sản phẩm, thêm/cập nhật/xóa sản phẩm trong giỏ hàng.
- Đặt hàng với thông tin người nhận và địa chỉ giao hàng.
- Thanh toán COD.
- Thanh toán trực tuyến qua VNPay và ZaloPay ở môi trường sandbox.
- Xem danh sách và chi tiết đơn hàng cá nhân.
- Theo dõi trạng thái đơn, thanh toán lại hoặc đổi phương thức cho đơn chờ thanh toán.
- Nhập mã giảm giá, xem mã đang có và lưu mã giảm giá khi đăng nhập.

#### B. Chức năng dành cho quản trị viên

- Đăng nhập và phân quyền khu vực admin bằng session riêng.
- Xem dashboard: sản phẩm đang bán, đơn hàng, khách hàng, doanh thu và sản phẩm sắp hết hàng.
- Quản lý sản phẩm: thêm, sửa, ẩn/xóa theo điều kiện dữ liệu, tải ảnh, cập nhật thuộc tính và tỷ lệ lợi nhuận.
- Quản lý danh mục: thêm, sửa, xóa khi không còn sản phẩm tham chiếu.
- Quản lý nhập hàng: tạo phiếu, thêm dòng nhập theo size/màu, tính giá vốn bình quân, cộng tồn và hoàn thành phiếu.
- Quản lý đơn hàng: xem, lọc và cập nhật trạng thái theo quy trình nghiệp vụ.
- Quản lý mã giảm giá: tạo, bật/tắt, giới hạn số lần dùng, thời gian, giá trị và phạm vi áp dụng.
- Quản lý tài khoản: tạo người dùng, phân vai trò, khóa/mở khóa, đặt lại mật khẩu.
- Tra cứu tồn kho theo ngày và danh mục.
- Xem thống kê đơn hàng, doanh thu, cảnh báo sắp hết hàng và quản lý giá bán.

#### C. Dữ liệu và kỹ thuật

- Cơ sở dữ liệu MySQL cho người dùng, sản phẩm, biến thể, đơn hàng, thanh toán, nhập hàng và khuyến mãi.
- Kết nối cấu hình qua biến môi trường; hỗ trợ chạy local và Docker.
- API nội bộ cho kiểm tra, lấy và lưu mã giảm giá.
- Callback/IPN cho các cổng thanh toán được tích hợp.
- Kiểm tra dữ liệu đầu vào, mã hóa mật khẩu, phân quyền truy cập và quản lý session.
- Tài liệu hướng dẫn cài đặt, cấu hình và khôi phục dữ liệu cơ bản.

### 4.2. Ngoài phạm vi phiên bản 1.0

Các nội dung sau không nằm trong phạm vi cam kết của phiên bản đầu tiên, trừ khi được phê duyệt thành yêu cầu thay đổi:

- Ứng dụng native riêng cho iOS hoặc Android.
- Tích hợp cổng thanh toán production, đối soát tự động với ngân hàng hoặc kế toán.
- Tích hợp đơn vị vận chuyển, in vận đơn và theo dõi GPS thời gian thực.
- Quản lý nhiều kho, nhiều chi nhánh hoặc chuỗi cửa hàng.
- Đồng bộ tự động với sàn thương mại điện tử, mạng xã hội hoặc hệ thống ERP/CRM bên ngoài.
- Chat thời gian thực giữa khách hàng và cửa hàng.
- AI tư vấn size, đề xuất sản phẩm cá nhân hóa hoặc nhận diện hình ảnh.
- Chương trình khách hàng thân thiết, tích điểm và hạng thành viên nâng cao.
- Đa ngôn ngữ, đa tiền tệ và mở rộng ra thị trường ngoài Việt Nam.
- Cam kết SLA, giám sát 24/7, kiểm thử tải quy mô lớn hoặc chứng nhận bảo mật độc lập.
- Nhập dữ liệu lớn tự động từ hệ thống cũ, trừ dữ liệu được thống nhất trong kế hoạch bàn giao.

## 5. Sản phẩm bàn giao

1. Mã nguồn website PHP và các module quản trị/API/thanh toán.
2. Lược đồ và bản sao cơ sở dữ liệu MySQL mẫu.
3. File cấu hình mẫu và hướng dẫn thiết lập biến môi trường.
4. Website chạy được trên XAMPP hoặc Docker.
5. Tài liệu hướng dẫn sử dụng cho khách hàng và admin ở mức cơ bản.
6. Danh sách ca kiểm thử và biên bản nghiệm thu các luồng chính.
7. Danh sách lỗi còn tồn tại, rủi ro và khuyến nghị cho phiên bản tiếp theo.

## 6. Giả định và ràng buộc

### 6.1. Giả định

- Nhà tài trợ cung cấp nội dung sản phẩm, ảnh, giá, danh mục và chính sách bán hàng.
- Có sẵn máy chủ hoặc môi trường XAMPP/Docker và cơ sở dữ liệu MySQL.
- Tài khoản sandbox VNPay/ZaloPay được cung cấp khi kiểm thử thanh toán.
- Người dùng có trình duyệt hiện đại và kết nối Internet.
- Quy trình trạng thái đơn hàng, chính sách đổi trả và cách tính khuyến mãi được thống nhất trước nghiệm thu.

### 6.2. Ràng buộc

- Phiên bản hiện tại là website PHP thuần, không bao gồm ứng dụng mobile.
- Thanh toán online phụ thuộc vào môi trường sandbox, callback và chính sách của nhà cung cấp.
- Phạm vi nhân sự nhỏ, ưu tiên chức năng cốt lõi hơn các tính năng mở rộng.
- Chi phí cổng thanh toán, máy chủ, tên miền, SMS/email và vận chuyển bên thứ ba chưa nằm trong chi phí phát triển.
- Thay đổi cơ sở dữ liệu hoặc nghiệp vụ sau khi nghiệm thu phạm vi có thể làm tăng thời gian và kinh phí.

## 7. Phương pháp xác định và kiểm soát phạm vi

### 7.1. Cách xác định phạm vi

1. Khảo sát nhu cầu của chủ cửa hàng, khách hàng và nhân viên vận hành.
2. Đối chiếu chức năng đã có trong codebase với quy trình bán hàng thực tế.
3. Phân tích thị trường và các yêu cầu tối thiểu của website thương mại điện tử.
4. Phân rã công việc theo nhóm: khách hàng, admin, đơn hàng/thanh toán, kho, khuyến mãi, hạ tầng.
5. Xác định giả định, ràng buộc, tiêu chí nghiệm thu và phụ thuộc bên ngoài.
6. Lập baseline phạm vi và xin phê duyệt trước khi phát triển hoặc mở rộng.

### 7.2. Quy trình thay đổi phạm vi

Mọi yêu cầu ngoài tài liệu này phải đi qua quy trình sau:

1. Người yêu cầu ghi rõ chức năng, lý do, mức ưu tiên và lợi ích mong đợi.
2. Trưởng dự án phân tích ảnh hưởng đến thời gian, chi phí, cơ sở dữ liệu, bảo mật và các chức năng liên quan.
3. Đội dự án đưa ra phương án, ước lượng và rủi ro.
4. Nhà tài trợ hoặc người có thẩm quyền phê duyệt bằng văn bản.
5. Cập nhật tài liệu phạm vi, kế hoạch, ngân sách và tiêu chí nghiệm thu.
6. Chỉ triển khai sau khi yêu cầu thay đổi được chấp thuận.

Không xem một yêu cầu được trao đổi miệng hoặc một thay đổi đã được lập trình thử là yêu cầu đã được phê duyệt.

## 8. Kế hoạch công việc và mốc chính

| Giai đoạn | Nội dung chính | Thời lượng dự kiến |
|---|---|---:|
| 1. Khởi động | Chốt mục đích, người liên quan, yêu cầu và phạm vi baseline | 1 tuần |
| 2. Phân tích và thiết kế | Mô hình dữ liệu, luồng đặt hàng, phân quyền, giao diện và tiêu chí nghiệm thu | 1-2 tuần |
| 3. Phát triển chức năng cốt lõi | Sản phẩm, danh mục, tìm kiếm, tài khoản, giỏ hàng, đặt hàng | 2 tuần |
| 4. Phát triển vận hành | Admin, nhập hàng, tồn kho, đơn hàng, khuyến mãi và báo cáo | 2 tuần |
| 5. Thanh toán và tích hợp | VNPay/ZaloPay sandbox, callback, xử lý đơn chờ thanh toán | 1 tuần |
| 6. Kiểm thử và sửa lỗi | Kiểm thử chức năng, phân quyền, tồn kho, thanh toán và giao diện responsive | 1-2 tuần |
| 7. Triển khai và bàn giao | Cấu hình môi trường, sao lưu, hướng dẫn và nghiệm thu | 1 tuần |

Tổng thời gian dự kiến: **8-10 tuần**, có thể thay đổi nếu phát sinh yêu cầu ngoài phạm vi hoặc phụ thuộc bên thứ ba bị chậm.

## 9. Dự đoán kinh phí

Đây là dự toán tham khảo cho phiên bản 1.0, tính theo nhân sự và hạ tầng phổ biến tại Việt Nam. Con số chính thức cần được cập nhật sau khi chốt nhân sự, thời gian và nhà cung cấp.

### 9.1. Dự toán chi phí phát triển

| Hạng mục | Cơ sở ước tính | Dự toán (VNĐ) |
|---|---|---:|
| Phân tích yêu cầu và quản lý dự án | 5-7 ngày công | 5.000.000 - 8.000.000 |
| Thiết kế giao diện và trải nghiệm | 5-8 ngày công | 4.000.000 - 7.000.000 |
| Phát triển website khách hàng | 15-20 ngày công | 15.000.000 - 22.000.000 |
| Phát triển khu vực admin, kho và báo cáo | 15-20 ngày công | 15.000.000 - 24.000.000 |
| Cơ sở dữ liệu, API và tích hợp thanh toán | 7-10 ngày công | 8.000.000 - 14.000.000 |
| Kiểm thử, bảo mật và sửa lỗi | 7-10 ngày công | 6.000.000 - 10.000.000 |
| Triển khai và tài liệu bàn giao | 3-5 ngày công | 3.000.000 - 5.000.000 |
| **Tạm tính phát triển** |  | **56.000.000 - 90.000.000** |
| Dự phòng thay đổi/rủi ro | 10-15% tạm tính | 5.600.000 - 13.500.000 |
| **Tổng dự toán phát triển** |  | **61.600.000 - 103.500.000** |

### 9.2. Chi phí vận hành dự kiến

| Hạng mục | Dự toán tham khảo |
|---|---:|
| Tên miền | 300.000 - 800.000 VNĐ/năm |
| Hosting/VPS nhỏ | 2.000.000 - 8.000.000 VNĐ/năm |
| Cơ sở dữ liệu managed hoặc dịch vụ bổ sung | 0 - 12.000.000 VNĐ/năm |
| Phí giao dịch/cước dịch vụ thanh toán | Theo biểu phí nhà cung cấp |
| SSL, email/SMS, sao lưu mở rộng | 0 - 6.000.000 VNĐ/năm |

Chi phí vận hành, phí giao dịch và phí dịch vụ bên thứ ba được theo dõi riêng, không cộng mặc định vào ngân sách phát triển.

### 9.3. Giả định của dự toán

- Dự toán tính cho một website responsive và một môi trường triển khai chính.
- Nội dung, hình ảnh, chính sách và dữ liệu ban đầu do chủ dự án cung cấp.
- Không bao gồm phát triển mobile native, thiết kế thương hiệu toàn diện, nhập liệu số lượng lớn và tích hợp hệ thống bên ngoài ngoài VNPay/ZaloPay sandbox.
- Phần dự phòng chỉ được sử dụng cho rủi ro hoặc thay đổi đã được phê duyệt.
- Dự toán cần được rà soát lại nếu thời gian thực hiện vượt 10 tuần hoặc phạm vi nghiệp vụ thay đổi.

## 10. Tiêu chí kết thúc dự án

Dự án được đề xuất kết thúc khi đáp ứng đồng thời các điều kiện sau:

- Các mục tiêu OBJ-01 đến OBJ-10 đã được kiểm tra và ghi nhận kết quả.
- Các luồng chính: đăng ký/đăng nhập, xem sản phẩm, giỏ hàng, đặt hàng, thanh toán, cập nhật tồn kho và quản trị đã được nghiệm thu.
- Không còn lỗi nghiêm trọng chặn việc mua hàng hoặc quản trị dữ liệu.
- Tài liệu triển khai, tài khoản môi trường và bản sao dữ liệu cần thiết đã được bàn giao.
- Các yêu cầu còn lại được ghi nhận thành backlog cho phiên bản sau, không tự động mở rộng phạm vi 1.0.
- Nhà tài trợ xác nhận nghiệm thu phạm vi và ngân sách bằng văn bản.

## 11. Chỉ số theo dõi sau bàn giao

- Tỷ lệ ca kiểm thử đạt: mục tiêu từ 95% trở lên trước nghiệm thu.
- Tỷ lệ lỗi nghiêm trọng trong luồng đặt hàng: 0 tại thời điểm bàn giao.
- Tỷ lệ đơn bị lỗi do kiểm soát tồn kho: 0 trong bộ kiểm thử cạnh tranh cơ bản.
- Thời gian phản hồi trang chính trong môi trường triển khai chuẩn: mục tiêu dưới 3 giây với dữ liệu mẫu.
- Tỷ lệ yêu cầu ngoài phạm vi được phê duyệt trước khi phát triển: 100%.
