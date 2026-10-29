# Phân quyền

Ba vai trò đã chốt: Admin, Người dùng (ứng viên), Nhà tuyển dụng.
Bảng sau là đề xuất ban đầu; các ô “Chưa chốt” cần được quyết định trước khi lập trình.

| Chức năng | Ứng viên | Nhà tuyển dụng | Admin |
| --- | --- | --- | --- |
| Cập nhật tài khoản cá nhân | Của mình | Của mình | Của mình |
| Xem tin tuyển dụng công khai | Có | Có | Có |
| Tải, xem và quản lý CV | Của mình | Không tải thay ứng viên | Mặc định không đọc nội dung CV |
| Ứng tuyển | Có | Không trong vai trò này | Không trong vai trò này |
| Xem hồ sơ đã nộp | Của mình | Thuộc tin của mình | Chưa chốt; không mặc định truy cập nội dung |
| Tạo/sửa/đóng tin | Không | Tin của mình | Quản trị theo quy trình đã duyệt |
| Đổi trạng thái tuyển chọn | Không | Hồ sơ thuộc tin của mình | Chưa chốt |
| Xem điểm đối sánh AI | Chưa chốt | Hồ sơ thuộc tin của mình | Chưa chốt |
| Quản lý/khóa tài khoản | Không | Không | Có, theo quy tắc được duyệt |
| Kiểm duyệt tin tuyển dụng | Không | Không | Có nếu chọn quy trình kiểm duyệt |

## Quy tắc thực thi dự kiến

- Backend kiểm tra vai trò và quyền sở hữu tài nguyên trong từng yêu cầu.
- Ẩn nút/menu ở frontend chỉ phục vụ trải nghiệm, không thay thế kiểm tra quyền.
- Không nhận vai trò Admin từ biểu mẫu đăng ký công khai.
- CV không trở thành dữ liệu công khai chỉ vì ứng viên đã ứng tuyển.
- Nhà tuyển dụng không xem CV chưa nộp vào tin của mình.
- Ghi nhận thao tác quản trị cần truy vết; không ghi mật khẩu, token hoặc toàn bộ CV vào log.
- Trường hợp chưa xác định quyền: mặc định từ chối cho đến khi có quy tắc được duyệt.

## Tình huống cần kiểm tra khi có code

1. Ứng viên A dùng mã CV của B: bị từ chối.
2. Nhà tuyển dụng A dùng mã tin/hồ sơ của B: bị từ chối.
3. Tài khoản thường gửi yêu cầu đăng ký hoặc cập nhật vai trò Admin: bị từ chối.
4. Người chưa đăng nhập tải tệp CV riêng tư: bị từ chối.
5. Nhà tuyển dụng đọc phiên bản CV đã nộp, không tự được truy cập các phiên bản khác.
