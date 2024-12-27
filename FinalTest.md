# 5. Thiết kế các lớp
* Phần này trình bày chi tiết thiết kế của từng lớp trong hệ thống Mentcare, bao gồm các thuộc tính, phương thức và mối quan hệ giữa các lớp. Thiết kế này nhằm đảm bảo hệ thống đáp ứng đầy đủ các yêu cầu chức năng và phi chức năng đã được xác định trong tài liệu yêu cầu.
* ![Diagram](https://www.planttext.com/plantuml/png/ZLNRRjim37qFa7ymyhGBMcolmJ0qcmiiQ8i6QVi1YiGuMcN9qyLhCEpVH_aocvwIxYq-fCbp3XdwodbcVIZLVCOLSoxRC2z1--pNV9PbxwlsQPqlimTlfIuQLBCI2C24iE0SmGJpSB__8gq_BBCS7ngK6-qPzpbu9XLzmK8XdGSBuWw4v4njB6PAJbjfUF7t-nkf2SejO8UE-nQuiUBDssLM6ocQUAZ445_hlI7H0dmN-eOCZ3sIg8KV0PnVSOuIXyZl-QptxAlHBYYF9OpkZECZQE9UsjF8xr56N_FkLrj7IIsvPDgjTMrK3MAPtIB9J-shdvia5tRV0QsgOLrMSH3Ob7hhepybTjrWc5kvIzOf6zyZPNSspqhtl78E6yMIYK6C3JavZLUIS2ZZZ6vZalxV_UNTkJy8UMrpXN6ie92J0gxtUpIKUiYDGwsv2JlLpgRgFHhw4mKrKp8AFH56WKFadBnLLHcfc_5r-jY0_DTojLiq0KT5ylJouMtmWPhW-054K33Yb1ZjAFhGr9WA7oMSK_xam7QI0_wS28ZGFmEjyBsVk4lqj1X5ix2wlpL5l294CGl-W9pYK20s9xoniYpq5cib9CTiUbX6EhPG6TiFppOF4oqj-7YiACy2D5YiBYBBwMd0Kphz-_NvRKD2qx4w1SDBXAQ14VS7uC5AV-pOW-RsMCMLlO4ZtQSWP3JL9Iv6znRoPwIxW3IkJD7tlQwdEuOho9_RSxm1Myhstat8zz-nnST5Td6HBJvSNhvRa4jzAcUqc_CPEUqqR_ZppcVDej9mQsaor4kBFAz0Y-Rp-mS0)
## 1. Patient (Bệnh nhân)
* Mô tả:
* Lớp Patient quản lý thông tin cơ bản của bệnh nhân, bao gồm thông tin cá nhân và liên hệ. Lớp này là trung tâm của hệ thống vì mọi hoạt động đều liên quan đến bệnh nhân.

* Các thuộc tính chính:
* patientID: Định danh duy nhất cho mỗi bệnh nhân, dựa trên số y tế quốc gia nếu có.
* name, address, dateOfBirth, contactDetails: Các thông tin cá nhân cơ bản.
* registeredMedicalPractice: Thông tin về cơ sở y tế mà bệnh nhân đăng ký.
* nextOfKin: Liên hệ của người thân trong trường hợp khẩn cấp.
* Các phương thức:
* createPatientRecord(): Tạo hồ sơ bệnh nhân mới.
* updatePatientInfo(): Cập nhật thông tin cá nhân.
* getPatientHistory(): Lấy lịch sử bệnh án.
* requestAccess(): Yêu cầu quyền truy cập hồ sơ cá nhân.
## 2. Consultation (Tư vấn)
* Mô tả:
* Lớp này lưu trữ thông tin về các cuộc tư vấn của bệnh nhân với bác sĩ, bao gồm nội dung, đánh giá rủi ro, và liệu pháp được đề xuất.

* Các thuộc tính chính:
* consultationID: Định danh duy nhất của mỗi cuộc tư vấn.
* patientID: Liên kết đến bệnh nhân.
* dateTime: Ngày và giờ của buổi tư vấn.
* cliniciansInvolved: Danh sách các nhân viên y tế tham gia.
* treatmentPrescribed: Liệu pháp được kê đơn.
* riskAssessment: Đánh giá rủi ro tự làm hại hoặc gây hại.
* Các phương thức:
* createConsultationRecord(): Tạo hồ sơ tư vấn mới.
* updateConsultationRecord(): Cập nhật thông tin tư vấn.
* getConsultationDetails(): Lấy chi tiết thông tin buổi tư vấn.
## 3. Medication (Thuốc)
* Mô tả:
* Lớp này quản lý thông tin về các loại thuốc được kê đơn trong hệ thống, bao gồm liều lượng, tác dụng phụ, và chi phí.

* Các thuộc tính chính:
* medicationID: Định danh duy nhất cho mỗi loại thuốc.
* name: Tên của thuốc.
* dosage: Liều lượng thuốc.
* sideEffects: Tác dụng phụ.
* cost: Chi phí.
* Các phương thức:
* prescribeMedication(): Kê đơn thuốc.
* validateMedication(): Kiểm tra thuốc trước khi kê đơn.
* getMedicationDetails(): Lấy thông tin chi tiết về thuốc.
## 4. Appointment (Cuộc hẹn)
* Mô tả:
* Lớp này lưu trữ thông tin các cuộc hẹn giữa bệnh nhân và phòng khám.

* Các thuộc tính chính:
* appointmentID: Định danh duy nhất của cuộc hẹn.
* patientID: Liên kết đến bệnh nhân.
* clinicID: Phòng khám liên quan đến cuộc hẹn.
* appointmentDateTime: Ngày và giờ của cuộc hẹn.
* status: Trạng thái cuộc hẹn (đã đến, đã bỏ lỡ, hoặc hủy).
* Các phương thức:
* scheduleAppointment(): Lên lịch hẹn mới.
* updateAppointmentStatus(): Cập nhật trạng thái hẹn.
* getAppointmentDetails(): Lấy thông tin chi tiết cuộc hẹn.
* 5. User (Người dùng)
* Mô tả:
* Quản lý thông tin và quyền truy cập của tất cả người dùng trong hệ thống, bao gồm nhân viên y tế, quản trị viên, và quản lý.

* Các thuộc tính chính:
* userID: Định danh duy nhất của người dùng.
* username, password: Thông tin đăng nhập.
* role: Vai trò (nhân viên y tế, quản trị viên, v.v.).
* lastLogin: Thời gian đăng nhập gần nhất.
* Các phương thức:
* authenticateUser(): Xác thực người dùng khi đăng nhập.
* assignRole(): Phân quyền vai trò.
* updateUserInfo(): Cập nhật thông tin người dùng.
## 6. Report (Báo cáo)
* Mô tả:
* Lớp này tạo và lưu trữ các báo cáo cho quản lý, đảm bảo dữ liệu được trình bày rõ ràng.

* Các thuộc tính chính:
* reportID: Định danh báo cáo.
* reportType: Loại báo cáo (tuần, quản lý, ẩn danh).
* generatedDate: Ngày tạo.
* content: Nội dung.
* Các phương thức:
* generateReport(): Tạo báo cáo.
* saveReport(): Lưu trữ báo cáo.
* exportReport(): Xuất báo cáo.
## 7. Security (Bảo mật)
* Mô tả:
* Quản lý tất cả các cơ chế bảo mật trong hệ thống, bảo vệ dữ liệu nhạy cảm.

* Các thuộc tính chính:
* encryptionKey: Khóa mã hóa.
* auditLogs: Ghi nhận các sự kiện bảo mật.
* Các phương thức:
* encryptData(), decryptData(): Mã hóa và giải mã dữ liệu.
* logSecurityEvent(): Ghi nhận các sự kiện bảo mật.
* checkAccessPermissions(): Kiểm tra quyền truy cập.
## Mối quan hệ giữa các lớp
* Patient ↔ Consultation: Một bệnh nhân có thể có nhiều buổi tư vấn.
* Consultation ↔ Medication: Một buổi tư vấn có thể kê đơn nhiều loại thuốc.
* Patient ↔ Appointment: Một bệnh nhân có thể có nhiều cuộc hẹn.
* User ↔ Report: Người dùng có thể tạo và quản lý nhiều báo cáo.
* User ↔ Security: Mỗi người dùng chịu sự kiểm soát của cơ chế bảo mật.
# Nguồn tham khảo
## Dựa trên thông tin từ tài liệu yêu cầu hệ thống Mentcare requirements document, thông tin được trích xuất từ các phần:
* Phần 1: Mô tả hệ thống và người dùng – xác định chức năng và dữ liệu liên quan đến bệnh nhân, cuộc tư vấn, thuốc, và cuộc hẹn.
* Phần 3: Yêu cầu người dùng – mô tả chi tiết về các hoạt động và thông tin cần quản lý trong hệ thống.
* Phần 6: Yêu cầu bảo mật và quyền riêng tư – làm rõ các yêu cầu liên quan đến bảo mật và kiểm soát truy cập.
