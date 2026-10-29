# Backend

Phần API dự kiến sử dụng Python, FastAPI, MongoDB và PyMongo.
Chưa có ứng dụng, môi trường Python, kết nối cơ sở dữ liệu hay tác vụ OCR/AI.

## Các phần dự kiến

- Xác thực và phân quyền ba vai trò.
- Quản lý tin tuyển dụng, CV và hồ sơ ứng tuyển.
- Lưu tệp riêng với nội dung đã trích xuất trong MongoDB.
- Đọc PDF/DOCX, OCR ảnh và PDF scan tiếng Việt/Anh.
- Đối sánh embedding và cosine similarity ở giai đoạn 2.

## Trước khi viết code

Đọc `../docs/requirements.md`, `../docs/permissions.md`,
`../docs/use-cases.md` và `../docs/database.md`.

Khi triển khai, bổ sung tệp khai báo phụ thuộc, `.env.example` không chứa bí mật,
hướng dẫn chạy và kiểm thử. Mật khẩu phải được băm; quyền truy cập phải được kiểm
tra trên từng tài nguyên, không chỉ theo vai trò chung.
