# Luồng sử dụng dự kiến

Trạng thái: bản nháp thiết kế, chưa triển khai. Các chính sách còn mở xem
`requirements.md`; quyền xem dữ liệu xem `permissions.md`.

## UC-01. Đăng ký và đăng nhập

- Người dùng chọn tài khoản ứng viên hoặc nhà tuyển dụng.
- Hệ thống kiểm tra dữ liệu, trùng email và lưu mật khẩu đã băm.
- Đăng nhập thành công đưa tới khu vực phù hợp với vai trò.
- Đăng ký Admin không xuất hiện trên giao diện công khai.
- Ngoại lệ: thông tin không hợp lệ, email đã tồn tại, sai thông tin đăng nhập,
  tài khoản bị khóa hoặc nhà tuyển dụng đang chờ duyệt nếu chọn quy trình duyệt.

## UC-02. Đăng tuyển

- Nhà tuyển dụng đăng nhập, nhập tiêu đề, mô tả, nhiệm vụ và yêu cầu.
- Hệ thống kiểm tra dữ liệu, lưu tin gắn với chủ sở hữu.
- Tin chuyển sang trạng thái được chọn trong quy trình đăng/duyệt.
- Chủ tin có thể sửa hoặc đóng tin theo quy tắc nghiệp vụ.
- Ngoại lệ: thiếu trường bắt buộc, không có quyền, tin không còn hoạt động.

## UC-03. Tải và phân tích CV

- Ứng viên đăng nhập, chọn tệp hoặc kéo thả tệp.
- Hệ thống kiểm tra định dạng thực tế, dung lượng và khả năng đọc.
- Tạo bản ghi phiên bản CV, lưu tệp và trạng thái chờ xử lý.
- PDF văn bản/DOCX được trích xuất trực tiếp; ảnh/PDF scan qua OCR.
- Lưu văn bản trích xuất và các trường có bằng chứng.
- Giao diện hiển thị kết quả, thông tin thiếu và trạng thái cần kiểm tra/lỗi.
- Không suy diễn kỹ năng hoặc kinh nghiệm không xuất hiện trong nội dung.
- DOCX có thông tin nằm trong ảnh cần phát hiện và xử lý hoặc báo giới hạn rõ ràng.

## UC-04. Ứng tuyển

- Ứng viên mở chi tiết một tin đang nhận hồ sơ.
- Chọn phiên bản CV và xác nhận nộp.
- Backend kiểm tra quyền sở hữu CV, tình trạng tin và quy tắc trùng đơn.
- Tạo hồ sơ gắn với phiên bản CV lúc nộp; hiển thị kết quả nộp đơn.
- CV tải mới về sau không âm thầm thay đổi hồ sơ đã nộp.
- Cần chốt: cho nộp khi CV đang xử lý hay yêu cầu xử lý xong; quy tắc rút/nộp lại.

## UC-05. Nhà tuyển dụng xem hồ sơ

- Nhà tuyển dụng chọn một tin của mình.
- Xem danh sách hồ sơ đã nộp và mở chi tiết từng hồ sơ được phép.
- Có thể đọc CV gốc và thông tin trích xuất theo quyền.
- Giai đoạn 2 bổ sung thứ hạng, điểm đối sánh và bằng chứng.
- Chuyển trạng thái tuyển chọn theo quy trình đã thống nhất; AI chỉ hỗ trợ xem xét.

## UC-06. Quản trị

- Admin vào khu vực quản trị để xem tài khoản, tin tuyển dụng và trạng thái hệ thống.
- Khóa/mở tài khoản hoặc xử lý tin theo quy tắc đã duyệt, kèm lý do khi cần.
- Quyền quản trị tài khoản không tự cấp quyền đọc mọi nội dung CV.
- Cần xác định tác động của việc khóa tài khoản lên tin đang đăng và đơn đã nộp.
