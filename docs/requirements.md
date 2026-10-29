# Yêu cầu hệ thống

Trạng thái: bản nháp ban đầu. Phần “Đã thống nhất” phản ánh phạm vi đã chọn;
các quy tắc nghiệp vụ và điều kiện nghiệm thu dưới đây là đề xuất để duyệt trước
khi lập trình, chưa phải chức năng đã triển khai.

## 1. Đã thống nhất

- Đề tài: xây dựng hệ thống tuyển dụng thông minh ứng dụng AI trong phân tích và đối sánh CV.
- Vai trò: Admin, Người dùng (ứng viên), Nhà tuyển dụng.
- CV tiếng Việt và tiếng Anh; nhận PDF, DOCX, ảnh JPG/PNG và PDF scan.
- React cho frontend, FastAPI cho backend, MongoDB cho dữ liệu.
- Cách đối sánh ban đầu: embedding và cosine similarity.

## 2. Mục tiêu giai đoạn 1

Hoàn thành phân tích/thiết kế, các chức năng web cơ bản và bước đọc, phân tích CV.
Phần xếp hạng AI hoàn chỉnh, đánh giá thực nghiệm và triển khai sản phẩm thuộc
giai đoạn 2. Giai đoạn 1 có thể thử embedding độc lập trên dữ liệu nhỏ.

| Mã | Chức năng đề xuất | Điều kiện nghiệm thu dự kiến |
| --- | --- | --- |
| AUTH-01 | Đăng ký, đăng nhập, đăng xuất | Phân biệt đúng ba vai trò; từ chối đăng nhập sai; mật khẩu không lưu dạng rõ |
| AUTH-02 | Kiểm tra quyền | Người dùng không truy cập tài nguyên riêng của người khác qua API |
| JOB-01 | Nhà tuyển dụng tạo/sửa tin | Tin gắn với người đăng; chỉ chủ tin hoặc chức năng quản trị được phép mới sửa được |
| JOB-02 | Xem danh sách/chi tiết việc | Chỉ hiển thị tin đủ điều kiện công khai; có trạng thái rỗng và lỗi |
| CV-01 | Tải và quản lý CV cá nhân | Nhận các định dạng đã chọn; từ chối tệp không hợp lệ; tệp gắn với chủ sở hữu |
| CV-02 | Trích xuất nội dung | Có văn bản kết quả hoặc thông báo lỗi/cần kiểm tra; không báo hoàn thành giả |
| CV-03 | Tách thông tin CV | Lưu kỹ năng, kinh nghiệm, học vấn, dự án/chứng chỉ khi có bằng chứng |
| APP-01 | Ứng tuyển | Gắn ứng viên, tin tuyển dụng và phiên bản CV lúc nộp |
| APP-02 | Theo dõi hồ sơ | Ứng viên xem hồ sơ mình; nhà tuyển dụng xem hồ sơ thuộc tin mình |
| ADM-01 | Quản lý tài khoản | Admin xem thông tin quản trị và khóa/mở tài khoản theo quy tắc đã duyệt |
| ADM-02 | Quản lý tin | Admin xử lý tin vi phạm/không hợp lệ theo quy trình đã duyệt |

## 3. Mục tiêu giai đoạn 2

- Đối sánh CV–JD, xếp hạng và hiển thị bằng chứng liên quan.
- So sánh TF-IDF + cosine, embedding + cosine và phương án kết hợp tiêu chí nếu có.
- Đánh giá trên dữ liệu có nhãn do người chấm; báo cáo theo ngôn ngữ và định dạng.
- Hoàn thiện giao diện, kiểm thử, triển khai, hướng dẫn sử dụng và báo cáo.
- Điểm tương đồng không trình bày như xác suất tuyển thành công.

## 4. Quy tắc đề xuất

- Không cho đăng ký công khai với vai trò Admin.
- Mỗi CV tải lên tạo một phiên bản; hồ sơ đã nộp giữ nguyên phiên bản tại thời điểm nộp.
- Thiếu thông tin trong CV được đánh dấu chưa đủ bằng chứng, không tự suy diễn.
- Quyền xem tệp CV phải kiểm tra qua backend; không dùng đường dẫn công khai mặc định.
- Nhà tuyển dụng chỉ xem CV được nộp cho tin thuộc quyền của mình.
- Trạng thái xử lý CV: chờ xử lý, đang xử lý, hoàn thành, cần kiểm tra, thất bại.
- Giới hạn dung lượng, số trang và thời gian xử lý sẽ chốt sau khi thử mẫu.

## 5. Dữ liệu thử ban đầu

Chuẩn bị 10 CV và 3 JD để kiểm tra luồng. Có tiếng Việt/Anh, PDF văn bản, DOCX,
PDF scan và ảnh chụp. Ghi nguồn, quyền sử dụng, văn bản chuẩn và các trường chuẩn.
CV thật đặt ngoài Git tại `data/private/` hoặc `uploads/`.

Quy mô 90 CV/18 JD và các nhóm Web/Backend, QA, phân tích dữ liệu từng được đề xuất
cho thực nghiệm mở rộng; chưa chốt thành yêu cầu bắt buộc.

## 6. Các quyết định còn mở

| Vấn đề | Đề xuất để thảo luận |
| --- | --- |
| Đổi PostgreSQL sang MongoDB trong phiếu giao đề tài | Thống nhất với giảng viên và cập nhật tài liệu |
| Xác minh tài khoản nhà tuyển dụng | Chọn tự đăng ký hoặc Admin duyệt trước khi đăng tin |
| Duyệt tin tuyển dụng | Chọn đăng ngay hoặc chờ duyệt; quy định lý do từ chối |
| Admin đọc CV | Mặc định không có quyền đọc nội dung CV; bổ sung phạm vi nếu cần |
| Ứng viên xem điểm AI | Chưa chốt; tránh coi đây là tính năng bắt buộc của giai đoạn 1 |
| Nộp lại/rút đơn | Đề xuất một đơn cho mỗi ứng viên–tin; cần chốt chính sách cập nhật/rút |
| Tài khoản và tổ chức | Đề xuất mỗi tài khoản nhà tuyển dụng quản lý tin của mình; chưa có phân quyền nhiều thành viên công ty |
| Ngành nghề thực nghiệm | Chọn nhóm nghề sau khi kiểm tra khả năng thu thập dữ liệu |
| Đối sánh chéo ngôn ngữ | Có CV Việt–Anh; cần chốt tiêu chí kiểm nghiệm CV Việt với JD Anh và ngược lại |

## 7. Điều kiện chuyển sang lập trình giao diện

- Đã duyệt phạm vi chức năng và bảng quyền.
- Đã chọn luồng đăng tuyển, ứng tuyển, xử lý CV và các trạng thái lỗi.
- Đã có mô hình dữ liệu/API sơ bộ và wireframe các trang chính.
- Repository có cấu trúc, `.gitignore` và tài liệu được quản lý phiên bản.
