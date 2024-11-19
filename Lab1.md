1 Phân tích kiên trúc 

Tính tái sử dụng (Reusability): Tách biệt các thành phần chức năng để dễ dàng mở rộng và bảo trì.

Tính bảo mật (Security): Đảm bảo chỉ các đối tượng được phép mới truy cập dữ liệu nhạy cảm.

Tính tích hợp (Integration): Hỗ trợ giao tiếp với các hệ thống hiện có như cơ sở dữ liệu khóa học hoặc hệ thống tài chính.

Hiệu năng (Performance): Đảm bảo hoạt động đồng thời với số lượng lớn người dùng.

Đề xuất kiến trúc

Mô hình kiến trúc

Kiến trúc được đề xuất là Layered Architecture với các lớp chính sau:


Presentation Layer:


Chứa giao diện người dùng (UI) để sinh viên, giảng viên, và quản trị viên tương tác với hệ thống.

Ví dụ: Form đăng nhập, màn hình đăng ký môn học, màn hình xem bảng điểm.

Application Layer:


Chứa các logic nghiệp vụ của hệ thống, xử lý các yêu cầu từ Presentation Layer.

Ví dụ: Kiểm tra điều kiện tiên quyết của môn học, tính toán số tiền học phí.

Data Access Layer:


Chịu trách nhiệm giao tiếp với cơ sở dữ liệu, sử dụng giao thức JDBC để truy cập hệ thống khóa học kế thừa hoặc ObjectStore để làm việc với dữ liệu đối
tượng.

Ví dụ: Lấy danh sách khóa học từ cơ sở dữ liệu hoặc lưu thông tin đăng ký của sinh viên.

Integration Layer:

Chịu trách nhiệm tích hợp với các hệ thống bên ngoài như hệ thống tài chính (billing system), ngân hàng (bank system), hoặc cơ sở dữ liệu di sản.

Security Layer:


Kiểm soát truy cập và bảo mật dữ liệu, đảm bảo rằng chỉ người dùng được phép mới có thể thực hiện các thao tác nhất định.

Ví dụ: Hạn chế quyền sửa đổi lịch học chỉ cho sinh viên liên quan.

Ý nghĩa của từng thành phần

Presentation Layer:


Cung cấp giao diện tương tác dễ sử dụng.

Đảm bảo tuân thủ các tiêu chuẩn UI (Windows 95/98 compliant).


Application Layer:


Xử lý logic nghiệp vụ, giúp đảm bảo các quy tắc hệ thống được thực thi.

Ví dụ: Hủy lớp học nếu số sinh viên đăng ký < 3.

Data Access Layer:


Tăng tính tái sử dụng mã và dễ dàng thay đổi cách truy cập dữ liệu.

Giảm thiểu phụ thuộc giữa lớp logic nghiệp vụ và cơ sở dữ liệu.

Integration Layer:


Đảm bảo tích hợp mượt mà giữa hệ thống mới và các hệ thống cũ mà không làm gián đoạn hoạt động.

Ví dụ: Truy xuất thông tin khóa học từ cơ sở dữ liệu kế thừa (Ingres RDBMS).

Security Layer:


Bảo vệ dữ liệu nhạy cảm và ngăn chặn truy cập trái phép.

Áp dụng các cơ chế như mã hóa, kiểm tra vai trò người dùng.

Biểu đồ package
![Diagram](https://www.planttext.com/api/plantuml/png/T99DRiCW44RtFiKe-roXYjseaYjBZMgrcyeBGaQK1eC5myAjUh8kUgHUeVb1mYQO7H_VFC4JVp-_6qVCakzLCJ1-P09XjRFeK1CZQJGqR4IxWgy2JkljfOO7OtlNXQr32xKUF7N5Tn49vJ0eoNE0oZkfqJbeZ90yO9wzGWUlJCd3PMOEsp9YK79-cPh17hVLFPIxEc2UzX_8gILZyPfEARKc53Px9QcKr0BQqH7sWLKnVPmd3Gh6nv2vERn5xgsaCI6NdjvF8eE9BeR6oi_uqcWLrkkxMqTJpVb6aIRNMlIJFxyHbg-bWXPQKsFvIgfmePPgMsvDF6vG7yw_-1y00F__0m00)

 2 Cơ chế phân tích
 
 Cơ chế bảo mật (Security Mechanism) 
 
Mô tả:

Xác thực (Authentication): Đảm bảo rằng chỉ người dùng hợp lệ (sinh viên, giảng viên, quản trị viên) có thể truy cập hệ thống.

Phân quyền (Authorization): Xác định và kiểm soát quyền hạn của từng loại người dùng (ví dụ: chỉ giảng viên được phép nhập điểm, sinh viên chỉ xem bảng 
điểm của mình).
Mã hóa (Encryption): Bảo vệ thông tin nhạy cảm như mật khẩu, bảng điểm, và thông tin thanh toán khi truyền qua mạng.

Lý do:

Dữ liệu nhạy cảm (như điểm, thông tin cá nhân) yêu cầu mức độ bảo mật cao để tuân thủ các quy định và tránh vi phạm quyền riêng tư.

Cơ chế giao tiếp với hệ thống kế thừa (Legacy System Integration Mechanism)
 
Mô tả:

Tích hợp cơ sở dữ liệu khóa học (Ingres RDBMS) thông qua giao diện SQL mở (Open SQL Interface).

Truy xuất dữ liệu kế thừa nhưng không cập nhật trực tiếp vào hệ thống này để đảm bảo an toàn dữ liệu.

Sử dụng lớp trung gian (middleware) hoặc JDBC để truy vấn và xử lý dữ liệu từ hệ thống di sản.

Lý do:

Dữ liệu khóa học hiện tại được lưu trong cơ sở dữ liệu di sản, và hệ thống mới phải hoạt động song song với cơ sở dữ liệu này để tránh gián đoạn.

Cơ chế xử lý đồng thời (Concurrency Mechanism)

Mô tả:

Cho phép nhiều người dùng (sinh viên, giảng viên, quản trị viên) truy cập và thao tác với hệ thống đồng thời.

Sử dụng cơ chế quản lý giao dịch (Transaction Management) để đảm bảo tính toàn vẹn dữ liệu, ví dụ:

Khóa dữ liệu khi một người dùng đang thao tác để tránh xung đột.

Thông báo ngay khi lớp học đã đầy trong thời gian thực.

Lý do:

Hệ thống cần hỗ trợ tối đa 2000 người dùng đồng thời, vì vậy cần giải quyết vấn đề cạnh tranh tài nguyên và đồng bộ dữ liệu.

Cơ chế quản lý trạng thái (State Management Mechanism)

Mô tả:

Lưu trạng thái tạm thời của quá trình đăng ký môn học (ví dụ: danh sách các môn học được chọn nhưng chưa gửi).

Sử dụng session hoặc cache để lưu thông tin trạng thái của người dùng trong một phiên làm việc.

Lý do:

Hỗ trợ trải nghiệm người dùng mượt mà, tránh mất dữ liệu khi thao tác.

Cơ chế xử lý giao dịch (Transaction Mechanism)

Mô tả:

Đảm bảo các thao tác quan trọng như đăng ký môn học hoặc tính toán học phí là nguyên tử (atomic), tức là hoàn thành hoàn toàn hoặc không thay đổi gì.

Sử dụng các phương pháp như:

Commit và rollback khi có lỗi.

Ghi log các thay đổi để khôi phục trong trường hợp hệ thống bị lỗi.

Lý do:

Giảm thiểu rủi ro mất dữ liệu và tăng tính tin cậy của hệ thống trong các thao tác phức tạp.

Cơ chế quản lý lỗi (Error Handling Mechanism)

Mô tả:

Hiển thị thông báo lỗi rõ ràng và thân thiện với người dùng khi xảy ra sự cố.

Log lỗi chi tiết cho quản trị viên để xử lý và cải thiện hệ thống.

Đảm bảo hoạt động liên tục (ví dụ: nếu hệ thống tài chính không khả dụng, cho phép xử lý giao dịch lại sau).

Lý do:

Hệ thống cần có khả năng phục hồi trước lỗi và cung cấp trải nghiệm người dùng tốt.

Cơ chế hiệu năng (Performance Mechanism)

Mô tả:

Giảm thiểu độ trễ khi truy cập dữ liệu từ cơ sở dữ liệu kế thừa (Ingres RDBMS).

Tối ưu hóa truy vấn SQL và sử dụng bộ nhớ đệm (caching) để tăng tốc độ phản hồi.

Hỗ trợ hoàn thành 80% giao dịch trong vòng 2 phút.

Lý do:

Đảm bảo hệ thống hoạt động hiệu quả với số lượng người dùng lớn.

Danh sách cơ chế phù hợp:

STT	Cơ chế	Lý do

*	Bảo mật (Security)	Bảo vệ dữ liệu nhạy cảm và phân quyền.

* Tích hợp hệ thống kế thừa	Sử dụng cơ sở dữ liệu khóa học hiện tại.

*	Xử lý đồng thời	Hỗ trợ nhiều người dùng thao tác đồng thời.

* Quản lý trạng thái	Lưu thông tin tạm thời khi thao tác.

*	Giao dịch (Transaction)	Đảm bảo tính toàn vẹn dữ liệu.

*	Xử lý lỗi	Cải thiện độ tin cậy và trải nghiệm người dùng.

*	Hiệu năng	Đáp ứng nhu cầu xử lý nhanh và mượt mà.

3 Phân tích ca sử dụng Payment

Xác định các lớp phân tích

Dựa trên yêu cầu của ca sử dụng Payment, các lớp phân tích được xác định như sau:

Tên Lớp	Mô tả

PaymentProcessor	Lớp xử lý logic thanh toán, bao gồm tính toán và thực hiện giao dịch.

Employee	Đại diện cho nhân viên nhận lương, chứa thông tin cá nhân và thông tin thanh toán.

Paycheck	Đại diện cho thông tin chi tiết về thanh toán của nhân viên, bao gồm lương và khấu trừ.

BankSystem	Tích hợp với hệ thống ngân hàng để thực hiện giao dịch trực tuyến.

PayrollSystem	Hệ thống tổng quát quản lý quy trình thanh toán.

TransactionLog	Lưu trữ thông tin về các giao dịch thanh toán đã thực hiện.

Biểu đồ sequence cho ca sử dụng Payment

Biểu đồ sequence dưới đây minh họa quy trình thanh toán:
![Diagram](https://www.planttext.com/api/plantuml/png/T99BJiD044JtSufMzhc05oWYWXL24U42ut4xZ9WVqpqBdur5ZiGLwF4laH5UM9Qg-bMLv9_lwu5OPoxUAMquPdZooSK14JG1-gIIgDROf0F3xgI779qx3yJeTzMIw8_3O-1JZWQ9OfvC6yoZ3fztZ7R3UCywaBInCRp4osXnyQAKr87zWqGsy8PV1OaXJN4gqQYa1kRaHO4yELKQRmNHm3Eo-QYVqz0EMLj7iwCoZjgPuZJZZJzghIIVCNGhV3dLZc5U3bHCBT0Nfq2UTcrsZA6tsQ_CgavSMTU0J0M-BR-JnzAlaMq_B7I5Zd2DxAK4Tfku-Q1g9UC_k4MLKUeWh_eV_0800F__0m00)

Nhiệm vụ của từng lớp phân tích

Lớp	Nhiệm vụ

PaymentProcessor	- Tính toán lương dựa trên thời gian làm việc và các khoản khấu trừ.

- Gửi yêu cầu thanh toán đến ngân hàng.
- 
Employee	- Cung cấp thông tin cá nhân và phương thức nhận lương.

Paycheck	- Lưu trữ thông tin chi tiết về lương của nhân viên (ví dụ: lương cơ bản, hoa hồng, giờ làm thêm).

BankSystem	- Xử lý giao dịch thanh toán qua tài khoản ngân hàng.

PayrollSystem	- Quản lý quy trình thanh toán tổng thể và giao tiếp với các lớp khác.

TransactionLog	- Ghi lại thông tin giao dịch (ví dụ: thành công, thất bại).

Biểu đồ lớp mô tả các lớp phân tích

![Diagram](https://www.planttext.com/api/plantuml/png/X5FBJiCm4BpdArOv5QazSCq15GIS05KgFx1rjcbKnmxU3LA4-38EV1A_WFEoahI5NABCUcR7ivkVh-yr2pgf2XqfZSpmK9JQraJm4O5_Lc2me0IsudAJzL29TK56daaEDftLTcYEjqhPoiYa0f2HR3hYFGdccXTN2NX47KWTey-eDp0WmS0EcRQeqTK9xBL56N1hAfv2AQMLajoQ2GwWKAjAez1Bww5ft9N7NHjd6sSLCLlNTmSeEwIlBwYF9mb1UQrtcwVpJdyIJczzvsFRrYnKXCxYqF2Ut6DbKbxWDDCbOD5zjnVncZjhDQ6PNCbPhMUgkSab_yzVUw4WzDeOmJRN9vi59MspKUMCq1ByRaapeyxpI3XiMNmTmsfrqxv3AYV3Q4u4IWBndiIVP3_lTf7YyuomIPuHviB3zbuWZGRXQKm--u41ZjugualCMKoUxHFYRemTt197C-bDJgKyBoLDsTJhsXjfVj9V0000__y30000)

Thuộc tính và quan hệ giữa các lớp
 
Employee:

Thuộc tính:

name: String - Tên nhân viên.

paymentMethod: String - Phương thức thanh toán (chuyển khoản, nhận trực tiếp).

bankAccount: String - Tài khoản ngân hàng (nếu thanh toán qua ngân hàng).

Quan hệ:

1-1 với Paycheck (mỗi nhân viên có một phiếu lương chi tiết).

Paycheck:


Thuộc tính:

baseSalary: float - Lương cơ bản.

bonus: float - Tiền thưởng (hoa hồng).

deductions: float - Các khoản khấu trừ.

Phương thức:

calculateNetPay(): float - Tính lương ròng (net pay).

PaymentProcessor:


Phương thức:

processPayment(employee: Employee): void - Xử lý thanh toán.

calculatePayment(employee: Employee): Paycheck - Tính toán lương cho nhân viên.

BankSystem:


Phương thức:

transferFunds(account: String, amount: float): boolean - Chuyển tiền qua tài khoản.

PayrollSystem:


Phương thức:

initiatePayment(employee: Employee): void - Bắt đầu quy trình thanh toán.

TransactionLog:


Phương thức:

logTransaction(employee: Employee, status: String): void - Lưu thông tin giao dịch.

4 Phân tích ca sử dụng Maintain Timecard

Xác định các lớp phân tích

Dựa trên yêu cầu của ca sử dụng Maintain Timecard, các lớp phân tích sau đây được xác định:


Tên Lớp	Mô tả

Employee	Đại diện cho nhân viên sử dụng hệ thống để cập nhật thông tin timecard.

Timecard	Lưu trữ thông tin về giờ làm việc của nhân viên trong một kỳ lương.

Project	Chứa thông tin về dự án hoặc mã công việc mà nhân viên báo cáo giờ làm việc.

TimecardProcessor	Xử lý logic cho việc tạo, cập nhật, và lưu timecard của nhân viên.

ProjectDatabase	Tích hợp với hệ thống cơ sở dữ liệu quản lý dự án (Project Management Database).

PayrollSystem	Quản lý toàn bộ quy trình xử lý timecard và giao tiếp với các hệ thống liên quan.

Biểu đồ sequence cho ca sử dụng Maintain Timecard

![Diagram](https://www.planttext.com/api/plantuml/png/R95DJiGm34RtESMdsSy5ka23-97OeD4C5p29eOMq2ROxg6TZmP6u0kcqL0KHAL4aFptxIxu-FdTg9DQtqP6t9BXfSqm3CqZ1RNQvL1lVPEeCcpqDac8y3chSRaOaws_YeMdPauIz9C-gISwK_VL8Uc5lrsJqICgJAVnlcWJUkJ8DjXUbOuK3l_Mi1ajegUciRDZCkwmZPhd2bJ0PewJgSnXl2sEJAbIuPVCryZGGV4topF0fS0aMi9rD1xPUkWKBN5f6dJNcAro6iEfJfruKxqbUEJYAXfymE55iWaDPjgGvqcarsbYR8fJ05UwJDKy3jFVZUpgEohZhpXgKNhHohNaMIUAu2svNZl5xlm400F__0m00)

Nhiệm vụ của từng lớp phân tích

Lớp	Nhiệm vụ

Employee	- Yêu cầu cập nhật timecard, cung cấp giờ làm việc và mã dự án.

Timecard	- Lưu trữ thông tin về giờ làm việc, mã dự án và ngày làm việc.

Project	- Cung cấp thông tin chi tiết về các mã công việc (charge codes).

TimecardProcessor	- Xử lý logic liên quan đến tạo mới, cập nhật hoặc xóa timecard.

ProjectDatabase	- Cung cấp thông tin về mã dự án (charge codes) từ cơ sở dữ liệu quản lý dự án.

PayrollSystem	- Quản lý quy trình duy trì timecard và lưu trữ dữ liệu.

Biểu đồ lớp mô tả các lớp phân tích

![Diagram](https://www.planttext.com/api/plantuml/png/V5F1QiCm3BtdAqHEBRI7NSCeXNQmmHY33dPMRJNrviJ1TWfbxCjss2Vj5wOaZfkbxN98WgJtdlHa_tnzBvr7w-j29qAZSt1NLDeSYU0Z0NxcK6916MoyLMKUGXHg7kIV182hjuNoBweWWLPEVFZ9e0zDCpWO9PFF9CZrYIWdqRFScjyXi3UrTQ_6lXFpxBH17nALDMya_Cf86hM1KjutgCc5abb76AZwVZhS0RLgz2SStXgZ2SjJfyyTLspqcdpCF8sD0yZ91verULJQDKgXuimIhXJadB514a1OukwYlVqQihYqsS2-wSdr0AyhEOIVRsTsQQZBXerjOKNSegFOAu-wsgFDgU5gvtnKpj-6yiM008_MQBqvEaz5X1UeIdQe_6VOGIlnqAOtASpdY_ORfpytj2c9c0pI7Ncn9mUosqfw1H8FAqEwNJZWLEVhLTJO8GPROclfm73HUWIYCIbD_denb3nHCboIfhnLhxemhobDbbJAvXx_0W00__y30000)

Thuộc tính và quan hệ giữa các lớp

Employee:


Thuộc tính:

name: String - Tên nhân viên.

employeeId: String - Mã nhân viên.

Phương thức:

submitTimecard(timecard: Timecard): void - Gửi yêu cầu cập nhật timecard.

Quan hệ:

1-1 với Timecard (mỗi nhân viên có một timecard cụ thể cho kỳ lương).

Timecard:


Thuộc tính:

date: Date - Ngày làm việc.

hoursWorked: float - Số giờ làm việc.

projectCode: String - Mã công việc.

Phương thức:

addHours(projectCode: String, hours: float): void - Thêm giờ làm việc cho mã công việc.

validate(): boolean - Xác minh tính hợp lệ của timecard.

Project:


Thuộc tính:

projectCode: String - Mã công việc.

projectName: String - Tên công việc.

Phương thức:

getProjectDetails(): String - Truy xuất thông tin công việc.

TimecardProcessor:


Phương thức:

createTimecard(employee: Employee, date: Date): Timecard - Tạo mới timecard.

updateTimecard(timecard: Timecard, projectCode: String, hours: float): void - Cập nhật timecard.

ProjectDatabase:


Phương thức:

getChargeCodes(): List<Project> - Lấy danh sách mã công việc từ cơ sở dữ liệu dự án.

PayrollSystem:


Phương thức:

maintainTimecard(employee: Employee): void - Điều phối quy trình duy trì timecard.

5 Hợp nhất kết quả phân tích

Các lớp phân tích chung

Khi hợp nhất hai ca sử dụng Payment và Maintain Timecard, các lớp phân tích có thể được tối ưu hóa để loại bỏ sự trùng lặp. Dưới đây là danh sách các lớp chung:


Tên Lớp	Vai trò (từ hai ca sử dụng)

Employee	Đại diện cho nhân viên, chịu trách nhiệm gửi yêu cầu thanh toán hoặc duy trì timecard.

Timecard	Lưu trữ thông tin về giờ làm việc của nhân viên trong từng kỳ lương.

Paycheck	Quản lý chi tiết thanh toán của nhân viên (dựa trên timecard).

PaymentProcessor	Xử lý logic liên quan đến tính toán lương và gửi yêu cầu thanh toán.

TimecardProcessor	Xử lý logic liên quan đến tạo, cập nhật, và kiểm tra timecard.

Project	Chứa thông tin về các mã dự án, giúp liên kết giờ làm việc trong timecard với các dự án cụ thể.

ProjectDatabase	Tích hợp với cơ sở dữ liệu quản lý dự án, cung cấp thông tin về các mã công việc.

BankSystem	Giao tiếp với ngân hàng để thực hiện giao dịch thanh toán lương.

TransactionLog	Ghi lại thông tin về giao dịch (thanh toán hoặc cập nhật timecard).

PayrollSystem	Quản lý quy trình tổng thể, điều phối hoạt động giữa các lớp khác như thanh toán hoặc duy trì timecard.

Quan hệ giữa các lớp

Lớp	Quan hệ

Employee ↔ Timecard	Mỗi nhân viên có một hoặc nhiều timecard, ghi lại giờ làm việc hàng tuần hoặc hàng tháng.

Timecard ↔ Project	Mỗi timecard có thể liên kết với nhiều mã dự án, cho phép báo cáo giờ làm việc trên các dự án cụ thể.

Employee ↔ Paycheck	Mỗi nhân viên có một paycheck tương ứng với từng kỳ thanh toán, dựa trên giờ làm việc trong timecard.

PaymentProcessor ↔ BankSystem	PaymentProcessor gửi yêu cầu thanh toán tới BankSystem.

PayrollSystem ↔ TransactionLog	PayrollSystem ghi lại tất cả giao dịch vào TransactionLog để theo dõi.

TimecardProcessor ↔ ProjectDatabase	TimecardProcessor truy xuất thông tin mã công việc từ ProjectDatabase.

Biểu đồ lớp hợp nhất

![Diagram](https://www.planttext.com/api/plantuml/png/V5F1QiCm3BtdAqHEBRI7NSCeXNQmmHY33dPMRJNrviJ1TWfbxCjss2Vj5wOaZfkbxN98WgJtdlHa_tnzBvr7w-j29qAZSt1NLDeSYU0Z0NxcK6916MoyLMKUGXHg7kIV182hjuNoBweWWLPEVFZ9e0zDCpWO9PFF9CZrYIWdqRFScjyXi3UrTQ_6lXFpxBH17nALDMya_Cf86hM1KjutgCc5abb76AZwVZhS0RLgz2SStXgZ2SjJfyyTLspqcdpCF8sD0yZ91verULJQDKgXuimIhXJadB514a1OukwYlVqQihYqsS2-wSdr0AyhEOIVRsTsQQZBXerjOKNSegFOAu-wsgFDgU5gvtnKpj-6yiM008_MQBqvEaz5X1UeIdQe_6VOGIlnqAOtASpdY_ORfpytj2c9c0pI7Ncn9mUosqfw1H8FAqEwNJZWLEVhLTJO8GPROclfm73HUWIYCIbD_denb3nHCboIfhnLhxemhobDbbJAvXx_0W00__y30000)

Nhiệm vụ tổng hợp của các lớp

Lớp	Nhiệm vụ chính

Employee	Gửi yêu cầu thanh toán, duy trì timecard, và cung cấp thông tin cá nhân.

Timecard	Lưu thông tin về giờ làm việc, liên kết với mã công việc.

Paycheck	Tính toán lương ròng, lưu chi tiết thanh toán cho nhân viên.

PaymentProcessor	Tính toán lương dựa trên timecard và gửi yêu cầu thanh toán đến hệ thống ngân hàng.

TimecardProcessor	Xử lý logic tạo và cập nhật timecard, xác minh dữ liệu hợp lệ.

Project	Lưu thông tin về mã công việc và dự án mà nhân viên làm việc.

ProjectDatabase	Cung cấp thông tin mã công việc từ cơ sở dữ liệu quản lý dự án.

BankSystem	Thực hiện giao dịch thanh toán trực tuyến.

TransactionLog	Ghi lại thông tin các giao dịch để theo dõi và kiểm tra.

PayrollSystem	Điều phối hoạt động thanh toán và duy trì timecard, tích hợp với các lớp khác để xử lý logic tổng quát.

Giải thích

Tối ưu hóa lớp:


Kết hợp logic tương đồng từ hai ca sử dụng giúp giảm số lượng lớp và tăng tính tái sử dụng.

Ví dụ: Employee, Project, và Timecard có thể được dùng chung trong cả hai ca sử dụng.

Tách biệt trách nhiệm:


Các lớp như PaymentProcessor và TimecardProcessor xử lý logic nghiệp vụ cụ thể, giúp hệ thống dễ bảo trì hơn.

Khả năng mở rộng:


Cách thiết kế đảm bảo khả năng mở rộng, dễ dàng thêm các tính năng mới mà không ảnh hưởng đến cấu trúc hiện tại.


