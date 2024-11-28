# Payroll System Use Case Analysis

## 1. Maintain Timecard (Duy trì bảng chấm công)

### **Mô tả**
- Nhân viên tạo hoặc cập nhật bảng chấm công.
- Bảng chấm công lưu trữ số giờ làm việc trên từng dự án.
- Hệ thống kiểm tra mã tính phí với cơ sở dữ liệu quản lý dự án.

### **Tác nhân liên quan**
- **Nhân viên**: Nhập thông tin giờ làm việc.
- **Cơ sở dữ liệu quản lý dự án**: Kiểm tra mã tính phí hợp lệ.

### **Luồng hoạt động cơ bản**
1. Nhân viên mở form bảng chấm công.
2. Nhân viên nhập thông tin số giờ làm việc cho từng mã tính phí.
3. Hệ thống xác minh mã tính phí với cơ sở dữ liệu.
4. Hệ thống lưu bảng chấm công vào cơ sở dữ liệu.

---

## 2. Generate Paycheck (Tạo phiếu lương)

### **Mô tả**
- Hệ thống tính toán tiền lương dựa trên bảng chấm công đã lưu.
- Tạo phiếu lương và gửi thông tin tới ngân hàng để chuyển khoản.

### **Tác nhân liên quan**
- **Nhân viên**: Nhận phiếu lương.
- **Ngân hàng (BankSystem)**: Thực hiện chuyển khoản lương.

### **Luồng hoạt động cơ bản**
1. Hệ thống truy xuất bảng chấm công và thông tin lương của nhân viên.
2. Hệ thống tính toán tiền lương dựa trên giờ làm việc và mức lương.
3. Tạo phiếu lương (paycheck).
4. Gửi thông tin phiếu lương tới ngân hàng để chuyển khoản.

---

## 3. Manage Employee Information (Quản lý thông tin nhân viên)

### **Mô tả**
- Cập nhật thông tin nhân viên (mức lương, thông tin liên hệ, trạng thái công việc).

### **Tác nhân liên quan**
- **Người quản lý**: Cập nhật thông tin nhân viên.
- **Hệ thống Payroll**: Lưu trữ và quản lý thông tin.

### **Luồng hoạt động cơ bản**
1. Người quản lý chọn nhân viên cần cập nhật.
2. Nhập hoặc sửa đổi thông tin nhân viên.
3. Lưu thông tin vào cơ sở dữ liệu hệ thống.

---

## 4. Submit Purchase Order (Gửi yêu cầu mua hàng)

### **Mô tả**
- Nhân viên gửi yêu cầu mua hàng cho các nhu cầu công việc.
- Hệ thống xác minh và gửi yêu cầu tới người quản lý để phê duyệt.

### **Tác nhân liên quan**
- **Nhân viên**: Gửi yêu cầu mua hàng.
- **Cơ sở dữ liệu quản lý dự án**: Xác minh tính hợp lệ của mã dự án.
- **Người quản lý dự án**: Phê duyệt hoặc từ chối yêu cầu.

### **Luồng hoạt động cơ bản**
1. Nhân viên tạo và gửi yêu cầu mua hàng.
2. Hệ thống xác minh mã dự án.
3. Người quản lý dự án xem xét và phê duyệt.
4. Đơn hàng được gửi tới bộ phận tài chính.

---

## 5. Report Generation (Tạo báo cáo)

### **Mô tả**
- Hệ thống tạo báo cáo liên quan đến nhân viên, dự án hoặc chi phí.

### **Tác nhân liên quan**
- **Người quản lý**: Yêu cầu và xem báo cáo.
- **Hệ thống Payroll**: Tổng hợp dữ liệu và tạo báo cáo.

### **Luồng hoạt động cơ bản**
1. Người quản lý yêu cầu báo cáo (ví dụ: báo cáo chi phí dự án).
2. Hệ thống thu thập dữ liệu từ cơ sở dữ liệu.
3. Tạo báo cáo dưới dạng bảng hoặc biểu đồ.
4. Hiển thị hoặc xuất báo cáo (PDF, Excel).

---

## Bảng tổng hợp các ca sử dụng

| **Ca sử dụng**                | **Mô tả**                                                                                   | **Tác nhân chính**        |
|-------------------------------|---------------------------------------------------------------------------------------------|---------------------------|
| Maintain Timecard             | Nhập, chỉnh sửa, lưu bảng chấm công.                                                       | Nhân viên, CSDL dự án     |
| Generate Paycheck             | Tính lương, tạo phiếu lương và gửi thông tin tới ngân hàng.                                 | Nhân viên, BankSystem     |
| Manage Employee Information   | Cập nhật thông tin nhân viên.                                                              | Người quản lý             |
| Submit Purchase Order         | Gửi yêu cầu mua hàng liên quan đến công việc hoặc dự án.                                   | Nhân viên, Người quản lý  |
| Report Generation             | Tạo các báo cáo hiệu suất, chi phí hoặc thông tin tài chính.                               | Người quản lý             |




# Java Implementation for Maintain Timecard

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.Scanner;

// Class đại diện cho Timecard
class Timecard {
    private HashMap<String, Double> chargeCodes; // Mã dự án và số giờ làm việc

    public Timecard() {
        chargeCodes = new HashMap<>();
    }

    // Thêm giờ làm việc cho mã tính phí
    public void addHours(String code, double hours) {
        chargeCodes.put(code, chargeCodes.getOrDefault(code, 0.0) + hours);
    }

    // Hiển thị thông tin bảng chấm công
    public void display() {
        System.out.println("Timecard Details:");
        chargeCodes.forEach((code, hours) -> 
            System.out.println("Charge Code: " + code + ", Hours: " + hours));
    }
}

// Class kiểm soát Timecard
class TimecardController {
    private ArrayList<String> validChargeCodes; // Các mã hợp lệ
    private Timecard timecard;

    public TimecardController() {
        validChargeCodes = new ArrayList<>();
        validChargeCodes.add("PROJECT123");
        validChargeCodes.add("PROJECT456");
        validChargeCodes.add("PROJECT789");
        timecard = new Timecard();
    }

    // Kiểm tra tính hợp lệ của mã tính phí
    public boolean isValidCode(String code) {
        return validChargeCodes.contains(code);
    }

    // Xử lý duy trì bảng chấm công
    public void maintainTimecard() {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("Enter Charge Code (or 'exit' to finish): ");
            String code = scanner.nextLine();

            if (code.equalsIgnoreCase("exit")) {
                break;
            }

            if (!isValidCode(code)) {
                System.out.println("Invalid Charge Code! Please try again.");
                continue;
            }

            System.out.println("Enter Hours Worked: ");
            double hours = scanner.nextDouble();
            scanner.nextLine(); // Xử lý dòng trống

            timecard.addHours(code, hours);
            System.out.println("Hours added successfully!");
        }

        timecard.display();
        scanner.close();
    }
}

// Class chính để chạy chương trình
public class PayrollSystem {
    public static void main(String[] args) {
        System.out.println("Welcome to the Payroll System!");
        TimecardController controller = new TimecardController();
        controller.maintainTimecard();
    }
}
