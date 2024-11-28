
# Code Java mô phỏng ca sử dụng Maintain Timecard:

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

// Lớp để biểu diễn mục nhập thẻ chấm công
class Timecard {
    private String employeeName;
    private String date;
    private double hoursWorked;

    public Timecard(String employeeName, String date, double hoursWorked) {
        this.employeeName = employeeName;
        this.date = date;
        this.hoursWorked = hoursWorked;
    }

    public String getEmployeeName() {
        return employeeName;
    }

    public String getDate() {
        return date;
    }

    public double getHoursWorked() {
        return hoursWorked;
    }

    @Override
    public String toString() {
        return "Timecard{" +
                "Employee Name='" + employeeName + '\'' +
                ", Date='" + date + '\'' +
                ", Hours Worked=" + hoursWorked +
                '}';
    }
}

// Lớp quản lý thẻ chấm công
class TimecardManager {
    private List<Timecard> timecards;

    public TimecardManager() {
        timecards = new ArrayList<>();
    }

    public void addTimecard(Timecard timecard) {
        timecards.add(timecard);
        System.out.println("Timecard added: " + timecard);
    }

    public void updateTimecard(int index, double hoursWorked) {
        if (index >= 0 && index < timecards.size()) {
            Timecard tc = timecards.get(index);
            timecards.set(index, new Timecard(tc.getEmployeeName(), tc.getDate(), hoursWorked));
            System.out.println("Timecard updated: " + timecards.get(index));
        } else {
            System.out.println("Invalid index.");
        }
    }

    public void displayTimecards() {
        System.out.println("Timecards:");
        for (Timecard tc : timecards) {
            System.out.println(tc);
        }
    }
}

// Lớp chính để mô phỏng việc sử dụng
public class TimecardApplication {
    public static void main(String[] args) {
        TimecardManager manager = new TimecardManager();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("\n1. Add Timecard");
            System.out.println("2. Update Timecard");
            System.out.println("3. Display Timecards");
            System.out.println("4. Exit");
            System.out.print("Choose an option: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter employee name: ");
                    String name = scanner.nextLine();
                    System.out.print("Enter date (YYYY-MM-DD): ");
                    String date = scanner.nextLine();
                    System.out.print("Enter hours worked: ");
                    double hours = scanner.nextDouble();
                    manager.addTimecard(new Timecard(name, date, hours));
                    break;
                case 2:
                    System.out.print("Enter timecard index to update: ");
                    int index = scanner.nextInt();
                    System.out.print("Enter new hours worked: ");
                    double newHours = scanner.nextDouble();
                    manager.updateTimecard(index, newHours);
                    break;
                case 3:
                    manager.displayTimecards();
                    break;
                case 4:
                    System.out.println("Exiting...");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid option. Please try again.");
            }
        }
    }
}
## Giải thích mã
### 1. class Timecard: 
Lớp này lưu trữ thông tin về tên nhân viên, ngày làm việc và số giờ làm việc. Nó cũng cung cấp phương thức toString() để hiển thị thông tin.
### 2. class TimecarsManager:
 Lớp này quản lý danh sách các timecard. Nó có các phương thức để thêm, cập nhật và hiển thị các timecard.
### 3. class TimecardApplication:
Đây là lớp chính để tương tác với người dùng. Nó sử dụng vòng lặp để tiếp nhận các tùy chọn từ người dùng và thực hiện các thao tác tương ứng.



# Phân tích Ca sử dụng "Payroll"

## 1. Xác định các lớp phân tích
- **PayrollSystem**: Lớp quản lý hệ thống bảng lương, thực hiện các thao tác liên quan đến tính toán lương.
- **Employee**: Lớp đại diện cho nhân viên, chứa các thông tin như tên, ID, lương cơ bản, số giờ làm việc.
- **Timecard**: Lớp quản lý thời gian làm việc của nhân viên, ghi lại số giờ làm việc mỗi ngày.
- **Paycheck**: Lớp đại diện cho bảng lương của nhân viên, chứa thông tin chi tiết về lương, các khoản khấu trừ và thu nhập cuối cùng.
- **TaxCalculation**: Lớp tính toán thuế, dựa trên mức thu nhập của nhân viên.
- **Bonus**: Lớp quản lý các khoản thưởng cho nhân viên.

## 2. Nhiệm vụ từng lớp phân tích
- **PayrollSystem**: Tính toán lương của nhân viên, quản lý quá trình thanh toán và phát lương cho nhân viên.
- **Employee**: Cung cấp thông tin về nhân viên (tên, ID, mức lương cơ bản).
- **Timecard**: Ghi nhận thời gian làm việc của nhân viên và cung cấp dữ liệu cho quá trình tính toán lương.
- **Paycheck**: Xuất thông tin về bảng lương của nhân viên sau khi tính toán, bao gồm lương cơ bản, khấu trừ và thưởng.
- **TaxCalculation**: Tính toán các khoản thuế cần khấu trừ từ lương của nhân viên.
- **Bonus**: Quản lý và tính toán các khoản thưởng cho nhân viên.

## 3. Xác định thuộc tính và quan hệ giữa các lớp
- **PayrollSystem**: Thuộc tính `employeeList`, `paycheckList`, `taxCalculator`, `bonusList`. Quan hệ: liên kết với lớp Employee, Paycheck, TaxCalculation, và Bonus.
- **Employee**: Thuộc tính `name`, `employeeID`, `baseSalary`. Quan hệ: liên kết với lớp Timecard và Paycheck.
- **Timecard**: Thuộc tính `hoursWorked`, `employeeID`. Quan hệ: liên kết với lớp Employee.
- **Paycheck**: Thuộc tính `salary`, `tax`, `bonus`, `netSalary`. Quan hệ: liên kết với lớp Employee, TaxCalculation, và Bonus.
- **TaxCalculation**: Thuộc tính `taxRate`, `income`. Quan hệ: liên kết với lớp Paycheck.
- **Bonus**: Thuộc tính `bonusAmount`. Quan hệ: liên kết với lớp Paycheck.

## 4. Biểu đồ
![Biểu đồ lớp Payroll](https://www.planttext.com/api/plantuml/png/T5DBJiCm4Dtd55x2eXUmK5MWI5HYKP5AhAVEgBNgJsLF417YP2mu4bSWJkoqRaqMbZn-yzwRJtw_VnQUm56hLIKKUC_Mq3chLDrvGiq-AnO-r4TbEyGNwOcpSDuznT1yH1oX4tiKXpF4EeOYWk3Z4PHe5P1rd6rELsdD2DbQq_epXeTmJmBE2lG-shkvvUpTogRwggBlv2TPDg2HivgSDBkyYDMICsaeIeB76XIuZhF6jbk5Oto7b1YNI22L3vAHRXBTI8q2N9D4zxPr_isw0pOvNL6xrtWE2O4vWYVcrBp4x0iU-uxcWQ5_USWWbSipw80moLptCvzFij5BllPfEPaqmkgBc8YvsFEKwXj6crW7t_VQjeR-OHdWEK--gBFPV5g1mbEgi_1qiOZNW46xclPho8bphwOnbPbERoF90atJ_sf_0000__y30000)

---

# Phân tích Ca sử dụng "Generate Employee Reports"

## 1. Xác định các lớp phân tích
- **ReportGenerator**: Lớp tạo báo cáo về nhân viên.
- **Employee**: Lớp chứa thông tin của nhân viên.
- **PayrollSystem**: Lớp quản lý bảng lương và thông tin về lương của nhân viên.
- **Report**: Lớp đại diện cho báo cáo đã tạo ra, có thể là bảng lương hoặc các loại báo cáo khác.

## 2. Nhiệm vụ từng lớp phân tích
- **ReportGenerator**: Tạo các báo cáo cho hệ thống (báo cáo bảng lương, thông tin nhân viên, v.v.).
- **Employee**: Cung cấp thông tin cần thiết cho báo cáo (tên, ID, v.v.).
- **PayrollSystem**: Cung cấp thông tin về bảng lương của nhân viên.
- **Report**: Lưu trữ các dữ liệu báo cáo đã tạo ra.

## 3. Xác định thuộc tính và quan hệ giữa các lớp
- **ReportGenerator**: Thuộc tính `employeeList`, `payrollSystem`. Quan hệ: Liên kết với lớp Employee và PayrollSystem.
- **Employee**: Thuộc tính `name`, `employeeID`. Quan hệ: Liên kết với lớp ReportGenerator và PayrollSystem.
- **PayrollSystem**: Thuộc tính `employeeList`, `paycheckList`. Quan hệ: Liên kết với lớp ReportGenerator.
- **Report**: Thuộc tính `reportContent`, `reportDate`. Quan hệ: Liên kết với lớp ReportGenerator.

## 4. Biểu đồ
![Biểu đồ lớp Generate Employee Reports](https://www.planttext.com/api/plantuml/png/b59B2i8m4Dtt55dgeXS8KWfMH71Hx0b2EzHWcfHa58fuCXSUoIlOcAGOKSGi1kRtthoPtA-tt23JUEn4KWjc3Db1hpIkGO9cg3Gv9yG-w7gX1e0jDqY9jOkL3sMkecU3La9KWq7eA2bVNLVHEb1m5BCvzMJ99V7a0JAmIjO19HLgBjjuZar12PSOW35q5e2C2sF1VTi47atqbwvw3_NXfQBqeIpMvGc-otD-eDPFRwaaWiHOfKiL8oObriOy5lgaU6E1ty-LfjcqnO_9-2xnJdusUq4vo6RyCGy0003__mC0)



