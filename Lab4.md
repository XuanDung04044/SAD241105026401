# PAYROLL SYSTEM USE CASE ANALYSIS SOLUTION
## 1. Các Ca Sử Dụng Chính
**Đăng nhập (Login):**
- Người dùng (nhân viên/ quản lý) truy cập hệ thống thông qua giao diện đăng nhập.
- Xác thực thông tin để đảm bảo an toàn.
**Duy trì thẻ thời gian (Maintain Timecard):**
- Nhân viên nhập, chỉnh sửa thông tin giờ làm việc.
- Hỗ trợ liên kết với dự án hoặc hoạt động cụ thể.
**Chạy bảng lương (Run Payroll):**
- Quản lý thực hiện quy trình tính lương.
- Tự động lấy thông tin từ thẻ thời gian và hồ sơ nhân viên.
**Xử lý thanh toán (Process Payments):** Gửi thông tin lương đến hệ thống ngân hàng.
**In bảng lương (Print Paychecks):** Xuất bảng lương dưới dạng in ấn hoặc PDF.
**Lớp và đối tượng liên quan:**
- **Người dùng (User)**: Phân loại thành Nhân viên (Employee) và Quản lý (Manager).
- **Bảng lương (Payroll)**: Bao gồm thông tin chi tiết về lương (giờ làm việc, thuế, khấu trừ).
- **Hệ thống ngân hàng (BankSystem)**: Xử lý thanh toán.
- **Thẻ thời gian (Timecard)**: Lưu thông tin về giờ làm việc, dự án.
- **Cơ sở dữ liệu dự án (ProjectManagementDatabase)**: Hỗ trợ việc quản lý mã số chi phí và dự án.

---
  
## 2. Mô hình hóa các ca sử dụng (Use Case Diagrams)
Các Ca Sử Dụng:

**Đăng nhập (Login):**
- Tác nhân chính: Nhân viên, Quản lý.
- Mục tiêu: Truy cập hệ thống để thực hiện các chức năng.
- Ngoại lệ: Tài khoản bị khóa sau nhiều lần đăng nhập sai.

**Duy trì thẻ thời gian (Maintain Timecard):**
- Tác nhân chính: Nhân viên.
- Mục tiêu: Quản lý giờ làm việc và liên kết với các dự án cụ thể.

**Chạy bảng lương (Run Payroll):**
- Tác nhân chính: Quản lý.
- Mục tiêu: Tự động tính toán lương cho nhân viên.
- Ngoại lệ: Thẻ thời gian chưa đầy đủ hoặc sai thông tin.

**Xử lý thanh toán (Process Payments):**
- Tác nhân chính: Hệ thống ngân hàng.
- Mục tiêu: Thanh toán lương qua ngân hàng.

**In bảng lương (Print Paychecks):**
- Tác nhân chính: Quản lý.
- Mục tiêu: Tạo tài liệu bảng lương để cung cấp cho nhân viên.

---

## 3. Biểu đồ Ca Sử Dụng (Use Case Diagram)

![Diagram](https://www.planttext.com/api/plantuml/png/R59BIiH04DttAOhiSm4H4JyumYYZ1d7RPjfEOr8zT7SMGLo82xTw01UZEr5muMg2k8XuZvp0ArWzHkpvB09DrNlrtglAT_snRXqthYnobeip1qw3KJ9pC5H6f4vfP8odJXlOpve7F5RD4mAti5sCSbq9qJKFIexzoZVsE78fJ5VlYIJJAFSbnnv7wG4R7C-FAkj4mPYNe78k8EgrzGsuhAtl27PGjfD7XBnvXqIrzHKzlrw_nYWZk600fHKfjqJwlFsy9ZXcxUHb5FdfVIqLXf2jiW9dccS_Ur9F5UuLICKn-hMhqD6Ng888PXXIDuanhk3KUv7_3eXrMEA0LqRdUOW_QUkNgMUNSSnebStuLsHWT2gi9KeXqDcGiulBvWyCkI9ucedqtB9Bnlxs3N6yreMSAItawEuGuCDA420ip-d-exhkJ0nOWMY78YlAsxnH0gTm9ZgR9wp6SN1-pr-wiaNTq9Md9NGOFRyunjO53lsV_0C00F__0m00)
