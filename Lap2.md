
Họ và tên: Hán Thị Triểu
MSV: 4451051008
Tiêu đề: Lap 2
I. Tiến hành phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System.
1. Phân tích ca sử dụng Add New Employee
Các lớp phân tích chính bao gồm:
- PayrollAdministrator: Người dùng có quyền thêm mới nhân viên.
- PayrollSystem: Xử lý các yêu cầu thêm mới nhân viên.
- Employee: Đại diện cho nhân viên được thêm vào hệ thống.
- EmployeeRepository: Lớp lưu trữ và quản lý dữ liệu của nhân viên.\
Biểu đồ Sequence
- PayrollAdministrator gửi yêu cầu thêm nhân viên mới.
- PayrollSystem xử lý yêu cầu và tạo đối tượng Employee mới.
- PayrollSystem lưu trữ thông tin Employee mới vào EmployeeRepository.
2. Phân tích ca sử dụng Delete Employee
Các lớp phân tích chính bao gồm:
- PayrollAdministrator: Người dùng có quyền xóa nhân viên.
- PayrollSystem: Xử lý yêu cầu xóa nhân viên.
- EmployeeRepository: Lớp lưu trữ nhân viên và thực hiện việc xóa khi có yêu cầu.
Biểu đồ Sequence
- PayrollAdministrator gửi yêu cầu xóa một nhân viên.
- PayrollSystem tìm kiếm thông tin nhân viên trong EmployeeRepository.
- Nếu nhân viên tồn tại, PayrollSystem xóa nhân viên từ EmployeeRepository.
3. Phân tích ca sử dụng Update Employee Information
Các lớp phân tích chính bao gồm:
- PayrollAdministrator: Thực hiện cập nhật thông tin nhân viên.
- PayrollSystem: Xử lý yêu cầu cập nhật.
- EmployeeRepository: Lưu trữ thông tin nhân viên và cập nhật khi có thay đổi.
Biểu đồ Sequence
- PayrollAdministrator gửi yêu cầu cập nhật thông tin nhân viên.
- PayrollSystem tìm kiếm và cập nhật dữ liệu trong EmployeeRepository
4. Phân tích ca sử dụng Process Payment
Các lớp phân tích chính bao gồm:
- PayrollSystem: Hệ thống xử lý thanh toán cho nhân viên.
- Employee: Nhận thông tin thanh toán.
- TimecardRepository: Lấy thông tin timecard của nhân viên theo giờ.
- SalesReceiptRepository: Lấy thông tin về đơn hàng (đối với nhân viên hưởng hoa hồng).
- PaymentMethod: Lựa chọn phương thức thanh toán cho nhân viên (chuyển khoản, bưu điện, nhận tại văn phòng).
Biểu đồ Sequence
- PayrollSystem xác định nhân viên cần thanh toán.
- Nếu là HourlyEmployee, PayrollSystem lấy dữ liệu từ TimecardRepository và tính lương.
- Nếu là CommissionedEmployee, PayrollSystem lấy dữ liệu từ SalesReceiptRepository để tính hoa hồng.
- Hệ thống sử dụng PaymentMethod của nhân viên để hoàn tất thanh toán.
5. Phân tích ca sử dụng Generate Employee Reports
Các lớp phân tích chính bao gồm:
- Employee: Nhân viên yêu cầu báo cáo.
- PayrollSystem: Hệ thống xử lý và tạo báo cáo.
- TimecardRepository: Lấy dữ liệu thời gian làm việc.
- SalesReceiptRepository: Lấy dữ liệu bán hàng (nếu là nhân viên có hoa hồng).
- Report: Báo cáo bao gồm số giờ làm việc, doanh thu, và tổng lương.
Biểu đồ Sequence
- Employee gửi yêu cầu tạo báo cáo.
- PayrollSystem truy vấn từ TimecardRepository và/hoặc SalesReceiptRepository.
- PayrollSystem tạo đối tượng Report với thông tin cần thiết và gửi kết quả cho Employee.
6. Phân tích ca sử dụng Change Payment Method
Các lớp phân tích chính bao gồm:
- Employee: Thực hiện thay đổi phương thức thanh toán.
- PayrollSystem: Xử lý yêu cầu thay đổi.
- PaymentMethod: Cập nhật phương thức thanh toán (chuyển khoản, bưu điện, nhận tại văn phòng).
- EmployeeRepository: Lưu trữ cập nhật mới.
Biểu đồ Sequence
- Employee gửi yêu cầu thay đổi phương thức thanh toán.
- PayrollSystem cập nhật PaymentMethod cho Employee và lưu vào EmployeeRepository.
7. Phân tích ca sử dụng Change Payment Method
Các lớp phân tích chính bao gồm:
- PayrollSystem: Truy cập cơ sở dữ liệu quản lý dự án khi cần thiết.
- ProjectManagementDB: Cung cấp thông tin về mã dự án và chi phí.
Biểu đồ Sequence
- PayrollSystem truy vấn thông tin từ ProjectManagementDB khi cần tính toán thanh toán.
- ProjectManagementDB gửi thông tin dự án cho PayrollSystem.

II. Viết code Java mô phỏng ca sử dụng Maintain Timecard.

import java.util.*;

// Lớp đại diện cho nhân viên

class Employee {
    private int employeeId;
    private String name;

    public Employee(int employeeId, String name) {
        this.employeeId = employeeId;
        this.name = name;
    }

    public int getEmployeeId() {
        return employeeId;
    }

    public String getName() {
        return name;
    }
}

// Lớp đại diện cho thông tin Timecard

class Timecard {
    private Date date;
    private double hoursWorked;
    private String chargeNumber;

    public Timecard(Date date, double hoursWorked, String chargeNumber) {
        this.date = date;
        this.hoursWorked = hoursWorked;
        this.chargeNumber = chargeNumber;
    }

    public Date getDate() {
        return date;
    }

    public double getHoursWorked() {
        return hoursWorked;
    }

    public String getChargeNumber() {
        return chargeNumber;
    }
}

// Lớp đại diện cho cơ sở dữ liệu dự án hiện tại (ProjectManagementDB)

class ProjectManagementDB {
    private static Set<String> validChargeNumbers = new HashSet<>(Arrays.asList("PROJ001", "PROJ002", "PROJ003"));

    public static boolean validateChargeNumber(String chargeNumber) {
        return validChargeNumbers.contains(chargeNumber);
    }
}

// Lớp đại diện cho kho lưu trữ và truy xuất Timecard

class TimecardRepository {
    private List<Timecard> timecards = new ArrayList<>();

    public void saveTimecard(Timecard timecard) {
        timecards.add(timecard);
        System.out.println("Timecard saved successfully!");
    }

    public List<Timecard> getTimecards() {
        return timecards;
    }
}

// Lớp đại diện cho hệ thống PayrollSystem xử lý yêu cầu từ Employee

class PayrollSystem {
    private TimecardRepository timecardRepository = new TimecardRepository();

    public void maintainTimecard(Employee employee, Date date, double hoursWorked, String chargeNumber) {
        System.out.println("Employee " + employee.getName() + " is submitting a timecard...");
        
        // Bước 2: Xác thực mã số dự án qua ProjectManagementDB
        if (ProjectManagementDB.validateChargeNumber(chargeNumber)) {
            // Bước 3: Nếu mã số dự án hợp lệ, tạo bản ghi Timecard
            Timecard timecard = new Timecard(date, hoursWorked, chargeNumber);
            
            // Bước 4: Lưu trữ Timecard qua TimecardRepository
            timecardRepository.saveTimecard(timecard);
        } else {
            System.out.println("Invalid charge number! Timecard not saved.");
        }
    }

    public void showTimecards() {
        System.out.println("All recorded timecards:");
        for (Timecard timecard : timecardRepository.getTimecards()) {
            System.out.println("Date: " + timecard.getDate() + ", Hours Worked: " + timecard.getHoursWorked() +
                    ", Charge Number: " + timecard.getChargeNumber());
        }
    }
}

// Lớp chính để chạy chương trình mô phỏng ca sử dụng Maintain Timecard

public class Main {
    public static void main(String[] args) {
        // Tạo một nhân viên
        Employee employee = new Employee(1, "John Doe");
        
        // Tạo hệ thống PayrollSystem
        PayrollSystem payrollSystem = new PayrollSystem();
        
        // Nhân viên gửi yêu cầu ghi nhận thông tin timecard
        payrollSystem.maintainTimecard(employee, new Date(), 8, "PROJ001");
        payrollSystem.maintainTimecard(employee, new Date(), 9, "PROJ004"); // mã số dự án không hợp lệ

        // Hiển thị tất cả các Timecard đã ghi nhận
        payrollSystem.showTimecards();
    }
}

