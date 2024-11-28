# 1. Subsystem context diagrams
## BankSystem
![Diagram](https://www.planttext.com/api/plantuml/png/P951JWCn34NtFaNKVI_00ZKCqzKiAeOBk1apYffnIkn88CJ9M70aha12MwRgBEt_yk8uFr_V6r5CcgS0w3GcqsJHE54oAAOvzwnpCRDw7ljtKPfgPljps4NaNOgEH2gGz_BFTBiBrBuf9SPWy-2rHgq5IEGKUGnaLW_8XvDxLTEvD1_m2T2OzVh-kdjddXEo5BcFR9xeDPCeN06LRswm9lABJnFM0cvXsnTwwndPUGn5UOn91KfxSVLCFQBYmbHUNQ2wbijWfbVKB52JXUqFd1TOpaWEkh2sjh2dzNLn52ZrGjN4wHXycOtCbcZOepl0XdYel_iB003__mC0)
### 1 Customer:

* Người dùng thực hiện các yêu cầu giao dịch như chuyển tiền, kiểm tra số dư.
* Hệ thống trả về thông tin xác nhận giao dịch.
### 2 AccountingSystem:

* Hỗ trợ quản lý dữ liệu tài chính, nhận báo cáo từ BankSystem và gửi dữ liệu kế toán.
### 3 LoanProcessingSubsystem:

* Xử lý các yêu cầu vay vốn, trả về kết quả xử lý (đồng ý hoặc từ chối).
### 4 ExternalAudit:

* Đảm bảo rằng các giao dịch tuân thủ quy định pháp luật thông qua việc nhận nhật ký kiểm toán.
## PrintService
![Diagram](https://www.planttext.com/api/plantuml/png/R9112i9034NtESNWtWku48jKK13KeGU8DPQ1JbfdCgA89tFXaRo2dLf5iSly__BvoUDsdtX19y6MWBbKJcMUd4AlicvETjPm599EI4z2Zh7KPozaevDg04Uv81SbgS7A6HPDxcXo6aJ_Mr0Nk09aQZWS_-gZrwWsT0Za1NxCI6SVP5hntZYBOYe6IFgobiXOKCUl0mNw3qmQhhMK5fJW0LBTbpKppLLphaDFgMRZtMfHRPjcjYwfxJKXtiMlFW400F__0m00)
### 1 User:

* Gửi yêu cầu in tài liệu và nhận xác nhận từ hệ thống in.
### 2 Admin:

* Quản lý hàng đợi in và theo dõi trạng thái hàng đợi.
### 3 ExternalSystem:

* Hệ thống bên ngoài có thể gửi tài liệu để in và nhận thông báo hoàn thành.
## Project Management Database:
![Diagram](https://www.planttext.com/api/plantuml/png/L51BRi903Dtx51Pxn3wB2ah4gf6YX1x012jDEvb4OmS9LJqP2ux45N2OL86LvVURvxbThcjH2Zgq3gZIBc0Ukc-kD2DFDGSamJoRg9HFxBe-ehPCSC5z5xJnTNaMvNOaYn8WM0hvsZ4kNZ9RzfgIqe645p4_VSTV-0F8CrmktoAGu3OmAQy--wED_ru23pRAJ3J1M2hf801MwpcZO0sDrSOzoGz-DAApVvGcaOXlcBqedzqxrkfhlW_7shFVj0bkFBcpD7Ooo-2itfhzSVpDEm000F__0m00)
### 1 ProjectManager:

* Tạo và cập nhật thông tin dự án, đồng thời theo dõi trạng thái dự án.
### 2 Developer:

* Lấy danh sách công việc và gửi cập nhật tiến độ.
### 3 ReportingSystem:

* Kết nối để lấy dữ liệu báo cáo và phân tích thông tin từ hệ thống quản lý dự án.
# 2 Analysis class to design element map
