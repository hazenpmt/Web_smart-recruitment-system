# Thiết kế dữ liệu và API sơ bộ

Trạng thái: đề xuất ban đầu cho MongoDB, chưa tạo database, collection hoặc API.
Tên trường và endpoint có thể điều chỉnh sau khi duyệt yêu cầu.

## Kiến trúc dự kiến

React gọi API FastAPI. FastAPI kiểm tra quyền, làm việc với MongoDB và kho tệp.
Thành phần xử lý CV đọc tài liệu/OCR; thành phần AI tạo embedding và đối sánh.
Việc chọn tác vụ nền và nơi triển khai sẽ thực hiện sau khi thử thời gian xử lý.

## Collection dự kiến

| Collection | Trường chính đề xuất | Quy tắc |
| --- | --- | --- |
| `users` | `_id`, `email`, `password_hash`, `role`, `status`, `created_at` | Email chuẩn hóa và duy nhất; vai trò thuộc ba giá trị cho phép |
| `jobs` | `_id`, `recruiter_id`, `title`, `description`, `requirements`, `language`, `status`, `created_at`, `updated_at` | Gắn nhà tuyển dụng; yêu cầu bắt buộc/ưu tiên có cấu trúc nếu có |
| `resumes` | `_id`, `candidate_id`, `file_key`, `original_name`, `mime_type`, `language`, `processing_status`, `raw_text`, `parsed_data`, `created_at` | Một bản ghi ứng với một phiên bản CV; không ghi đè phiên bản đã nộp |
| `applications` | `_id`, `candidate_id`, `job_id`, `resume_id`, `job_snapshot`, `status`, `applied_at` | `resume_id` trỏ tới phiên bản lúc nộp; giữ nội dung JD tại thời điểm nộp để đối chiếu |
| `match_results` | `_id`, `application_id`, `model_version`, `scoring_version`, `score`, `evidence`, `created_at` | Giai đoạn 2; lưu phiên bản mô hình/quy tắc và dữ liệu đầu vào tương ứng |

`parsed_data` có thể chứa mảng `skills`, `experience`, `education`, `projects`,
`certifications`; giá trị không xác định không được tự biến thành 0 hoặc chuỗi giả.
Schema validation và kiểm tra tại API sẽ thống nhất kiểu dữ liệu.

Tệp PDF/DOCX/ảnh gốc nằm ở kho tệp; MongoDB lưu `file_key` và metadata.
Backend kiểm tra quyền trước khi trả tệp. Chưa chọn dịch vụ lưu trữ cụ thể.

## Index cần cân nhắc khi triển khai

- `users.email`: unique sau khi chuẩn hóa email.
- `jobs.recruiter_id`, `jobs.status`: theo truy vấn quản lý/tìm việc.
- `resumes.candidate_id`: quản lý CV của ứng viên.
- `applications.job_id`, `applications.candidate_id`: truy vấn hồ sơ.
- Unique trên `(candidate_id, job_id)` chỉ sau khi chốt chính sách nộp lại.

## Ranh giới API đề xuất

| Nhóm | Endpoint dự kiến | Mục đích |
| --- | --- | --- |
| Auth | `POST /auth/register`, `POST /auth/login`, `POST /auth/logout` | Tài khoản và phiên đăng nhập; cơ chế token/session cần thiết kế |
| Cá nhân | `GET /users/me`, `PATCH /users/me` | Thông tin tài khoản hiện tại |
| Tin | `GET /jobs`, `GET /jobs/{id}` | Xem tin đủ điều kiện công khai |
| Tin | `POST /jobs`, `PATCH /jobs/{id}` | Nhà tuyển dụng quản lý tin của mình |
| CV | `POST /resumes`, `GET /resumes`, `GET /resumes/{id}` | Tải, liệt kê CV cá nhân và đọc chi tiết theo quyền |
| Tệp CV | `GET /resumes/{id}/file` | Trả tệp sau khi kiểm tra quyền |
| Ứng tuyển | `POST /jobs/{id}/applications`, `GET /applications/me` | Nộp đơn và xem đơn cá nhân |
| Hồ sơ nhận được | `GET /jobs/{id}/applications` | Nhà tuyển dụng xem hồ sơ của tin mình |
| Quản trị | `/admin/users`, `/admin/jobs` | Thiết kế chi tiết sau khi chốt quyền quản trị |

Chưa dùng dữ liệu thiết kế này như một hợp đồng API hoàn chỉnh. Trước khi code
cần bổ sung schema request/response, phân trang, trạng thái lỗi, xác thực và các
quy tắc xóa/lưu giữ dữ liệu có liên kết.
