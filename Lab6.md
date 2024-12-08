LAB 6

1. Xác định các lớp và operations
Dựa trên mô hình tổng quan và hệ thống con, dưới đây là danh sách các lớp chính:
Timecard Management Subsystem
- TimecardEntry
+ Operations: addEntry(), updateEntry(), deleteEntry()
+ Trạng thái: New, Updated, Deleted
- ValidationService
+ Operations: validateChargeNumber(chargeNumber: String): boolean
- TimecardDatabase
+ Operations: saveTimecard(timecard: Timecard), 
getTimecard(employeeId: String): Timecard
Payroll Processing Subsystem
- PayCalculationEngine
+ Operations: calculatePay(employeeId: String): double
- PaymentGenerationModule
+ Operations: generatePayment(payDetails: PaymentDetails)
- PayrollDatabase
+ Operations: storePayrollRecord(record: PayrollRecord), getPayrollRecords(employeeId: String): List<PayrollRecord>
Reporting Subsystem
- ReportGenerationModule
+ Operations: generateWorkHoursReport(), generatePayrollReport()
- DataAnalyticsService
+ Operations: analyzePerformance(employeeId: String)
- ReportingUI
+ Operations: viewReport(reportId: String)
Employee Management Subsystem
- Employee
+ Operations: updateEmployeeDetails(details: EmployeeDetails)
- EmployeeCRUDModule
+ Operations: createEmployee(details: EmployeeDetails), deleteEmployee(employeeId: String)
- EmployeeDatabase
+ Operations: getEmployee(employeeId: String): Employee, saveEmployee(employee: Employee)
Payment Method Subsystem
- PaymentPreferenceModule
+ Operations: setPreference(employeeId: String, method: PaymentMethod)
- PaymentIntegrationService
+ Operations: processPayment(payment: PaymentDetails)
- EmployeePortal
+ Operations: selectPaymentMethod(method: PaymentMethod)
2. Xác định các thuộc tính
Dưới đây là một vài thuộc tính cơ bản:
- TimecardEntry: entryId, employeeId, hoursWorked, projectCode, status
- PayrollRecord: recordId, employeeId, grossPay, netPay, deductions
- Employee: employeeId, name, jobTitle, department, salaryDetails
- PaymentMethod: methodId, type (DirectDeposit, Check, etc.), details

