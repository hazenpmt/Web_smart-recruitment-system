# Web_smart-recruitment-system

Hệ thống tuyển dụng thông minh, phân tích và đối sánh CV Việt–Anh.

## Trạng thái

Dự án đang ở bước chuẩn bị cấu trúc và tài liệu yêu cầu. Chưa có ứng dụng React,
API FastAPI, kết nối MongoDB, OCR hoặc mô hình AI hoạt động.

## Phạm vi đã thống nhất

- Ba vai trò: Admin, Người dùng (ứng viên), Nhà tuyển dụng.
- Nội dung CV bằng tiếng Việt và tiếng Anh.
- Đầu vào: PDF có văn bản, PDF scan, DOCX và ảnh chụp/scan JPG hoặc PNG.
- Frontend: React. Backend: Python/FastAPI. Cơ sở dữ liệu: MongoDB.
- Phân tích CV và đối sánh với mô tả công việc (JD), sử dụng embedding và cosine similarity.
- Website được triển khai trực tuyến khi hoàn thiện.

MongoDB là lựa chọn hiện tại của dự án. Phiếu giao đề tài ban đầu ghi PostgreSQL;
cần thống nhất thay đổi với giảng viên và cập nhật tài liệu học thuật tương ứng.

## Cấu trúc

```text
frontend/             Hướng dẫn và mã nguồn React trong các bước tiếp theo
backend/              Hướng dẫn và mã nguồn FastAPI trong các bước tiếp theo
docs/
  requirements.md     Phạm vi, chức năng và điều kiện nghiệm thu
  permissions.md      Bảng quyền của ba vai trò
  use-cases.md         Luồng thao tác dự kiến
  database.md          Bản nháp thiết kế MongoDB và ranh giới API
  ui/README.md         Danh sách màn hình cần thiết kế
.gitignore            Quy tắc loại trừ cấu hình riêng, tệp sinh ra và CV thật
```

## Lộ trình

1. Hoàn thiện yêu cầu và những quyết định còn mở trong `docs/requirements.md`.
2. Duyệt phân quyền, luồng sử dụng, dữ liệu và danh sách API.
3. Chuẩn bị bộ CV/JD nhỏ và thử đọc các định dạng.
4. Vẽ bố cục giao diện trước khi lập trình React.
5. Dựng React, FastAPI, MongoDB; hoàn thành luồng đăng tuyển và ứng tuyển.
6. Tích hợp xử lý CV, đối sánh, đánh giá, triển khai và hoàn thiện báo cáo.

## Làm việc với Git

- `main`: giữ các mốc đã kiểm tra.
- Mỗi chức năng hoặc thay đổi tài liệu dùng một nhánh, ví dụ `feature/ui-layout`
  hoặc `docs/requirements`.
- Trước khi đổi nhánh, kiểm tra `git status` và xử lý các thay đổi đang làm.
- Sau mỗi phần hoàn chỉnh: xem diff, commit, push nhánh và mở Pull Request để xem
  lại trước khi merge. Không cần thêm nhánh `develop` ở giai đoạn hiện tại.

Ví dụ bắt đầu công việc mới khi thư mục làm việc sạch:

```sh
git switch main
git pull --ff-only origin main
git switch -c feature/ui-layout
```

Chưa có lệnh chạy frontend/backend vì chưa khởi tạo ứng dụng. Hướng dẫn chạy sẽ
được bổ sung khi có mã nguồn và tệp khai báo phụ thuộc.

## Dữ liệu và cấu hình

- CV thật và thông tin cá nhân để trong `data/private/` hoặc `uploads/`, không commit.
- Không đưa mật khẩu MongoDB, khóa API hay token vào mã nguồn, tài liệu hoặc commit.
- `.env` dùng cho cấu hình máy cá nhân; `.env.example` chỉ chứa giá trị mẫu.
- Chỉ thêm dữ liệu mẫu giả lập/đã được phép sử dụng và kiểm tra thông tin cá nhân.
- `.gitignore` không loại bỏ dữ liệu đã được commit trước đó.
