Tên: Hán Thị Triểu
MSV: 4451051008
Dựa vào mô tả các ca sử dụng, hệ thống Payroll System có thể được chia thành các hệ thống con chính như sau:

1. Timecard Management Subsystem
Chức năng chính: Quản lý thông tin về thời gian làm việc của nhân viên.
Liên quan đến ca sử dụng: Maintain Timecard
Các thành phần:
Timecard Entry Module: Ghi nhận thông tin thời gian làm việc, bao gồm số giờ và mã dự án.
Validation Service: Xác thực tính hợp lệ của mã số dự án (Charge Number).
Timecard Database: Lưu trữ thông tin timecard.
Tích hợp với hệ thống khác:
Kết nối với Project Management System để xác thực mã dự án.
Cung cấp dữ liệu cho Payroll Processing Subsystem.
2. Payroll Processing Subsystem
Chức năng chính: Xử lý bảng lương cho nhân viên.
Liên quan đến ca sử dụng: Process Payroll
Các thành phần:
Pay Calculation Engine: Tính toán lương dựa trên loại hình công việc (theo giờ, lương cố định, hoa hồng).
Payment Generation Module: Tạo các khoản thanh toán, tích hợp với ngân hàng hoặc xuất phiếu chi.
Payroll Database: Lưu trữ thông tin về bảng lương.
Tích hợp với hệ thống khác:
Sử dụng dữ liệu từ Timecard Management Subsystem.
Tích hợp với hệ thống thanh toán bên ngoài (Banking API).
3. Reporting Subsystem
Chức năng chính: Tạo và cung cấp các báo cáo liên quan đến công việc và lương.
Liên quan đến ca sử dụng: Generate Reports
Các thành phần:
Report Generation Module: Tạo báo cáo về số giờ làm việc, lương, và thời gian nghỉ phép.
Data Analytics Service: Phân tích dữ liệu để hỗ trợ quản lý hiệu suất.
Reporting UI: Giao diện cho nhân viên và quản trị viên xem báo cáo.
Tích hợp với hệ thống khác:
Lấy dữ liệu từ Timecard Management Subsystem và Payroll Processing Subsystem.
4. Employee Management Subsystem
Chức năng chính: Quản lý thông tin nhân viên.
Liên quan đến ca sử dụng: Manage Employee Information
Các thành phần:
Employee Database: Lưu trữ thông tin nhân viên.
Employee CRUD Module: Thêm, sửa, xóa thông tin nhân viên.
Validation Service: Đảm bảo thông tin nhập vào hợp lệ.
Tích hợp với hệ thống khác:
Cung cấp dữ liệu cho Payroll Processing Subsystem và Reporting Subsystem.
5. Payment Method Subsystem
Chức năng chính: Cung cấp tùy chọn phương thức nhận lương cho nhân viên.
Liên quan đến ca sử dụng: Select Payment Method
Các thành phần:
Payment Preference Module: Quản lý các tùy chọn nhận lương (chuyển khoản, phiếu chi qua thư, nhận trực tiếp).
Payment Integration Service: Tích hợp với hệ thống thanh toán bên ngoài (Direct Deposit, Mail Check).
Employee Portal: Giao diện cho nhân viên chọn phương thức thanh toán.
Tích hợp với hệ thống khác:
Kết nối với Payroll Processing Subsystem để đảm bảo thanh toán đúng phương thức.

Mô hình tổng quan:
![Diagram](https://www.planttext.com/api/plantuml/png/V9LDJiCm48NtFiMe6rQz0g9gMQ2s0b7e5fbaL2poKoMcA49Ti-O6t81zk-YY9-a9k09n6YSpiKCMMSmRJzvdFok_-yDLhcMct-98QAKZXAawxGu9wEou2s2-7CFBQVy9kdn_9IkuaqMMHX4iYbnZBCHQ1gzoXJ1OAdmVm8U0yWaYcUTm7Q-Zj41yUhmXrL4OguINPkdgNDgIUUCqqUPBcF6f3oh6G6PXgnEnTkVLxd6TPjehMQTzCsDCw49gSvw665c7JNM1sKO523DPjFvTXhgjezOGVl5CuTSiHkzOmq75RVNcrYTIInW50Pg3-T_-P7JRuy1LQYXNE0FPUf-ZPvdtxgRLwm7bwLp0jComXgJCh8ALEkr_99Y0mkRu3UGaIKHXEBpqXQlRuiQXs-44pKRUhkz4bCcUA3BT6MulJzzg_sQq3TMML2aMBZtR59iSXu1osQQkJsBUjhXc6GFv7DzmUWosoK_9hc45wgHRTEWOiKabvwAeHcL4XD5e7H06PtI_PyTXuxkz0u8OhCOsLu3CvqBhcTSRkxmihZ09pJ_X3m00__y30000)
