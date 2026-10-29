# Chuẩn bị thiết kế giao diện

Chưa có wireframe, giao diện hay ứng dụng React. Đây là danh sách màn hình đề xuất.
Màu sắc, font và bố cục chưa được chốt.

## Màn hình giai đoạn 1

| Nhóm | Màn hình |
| --- | --- |
| Chung | Đăng nhập, đăng ký, danh sách việc làm, chi tiết việc làm |
| Ứng viên | Quản lý CV, tải CV/xem nội dung trích xuất, hồ sơ đã ứng tuyển, tài khoản |
| Nhà tuyển dụng | Quản lý tin, tạo/sửa tin, danh sách ứng viên theo tin, chi tiết hồ sơ, tài khoản |
| Admin | Tổng quan quản trị, quản lý tài khoản, quản lý/kiểm duyệt tin |

Giai đoạn 2 bổ sung điểm đối sánh, xếp hạng và giải thích dựa trên bằng chứng.
Không hiển thị điểm AI minh họa như kết quả thực tế.

## Trình tự thiết kế

1. Duyệt yêu cầu và bảng quyền.
2. Vẽ sơ đồ điều hướng theo ba vai trò.
3. Vẽ wireframe các luồng đăng tuyển, tải CV, ứng tuyển và xem hồ sơ.
4. Chốt màu, font, nút, biểu mẫu, bảng và quy tắc hiển thị lỗi.
5. Kiểm tra bố cục máy tính/điện thoại trước khi code.

## Trạng thái phải thể hiện

- Đang tải, chưa có dữ liệu, lỗi và thành công.
- Chưa đăng nhập/không có quyền truy cập.
- Tệp CV không hợp lệ, đang xử lý, cần kiểm tra hoặc xử lý thất bại.
- Tin đã đóng/hết hạn; hồ sơ đã nộp; thao tác bị trùng.
- Thông tin CV còn thiếu được phân biệt với thông tin chắc chắn không đáp ứng.

Các bản thiết kế duyệt sau này được lưu trong thư mục này, dùng dữ liệu giả lập
và không đưa thông tin cá nhân thật vào ảnh chụp màn hình.
