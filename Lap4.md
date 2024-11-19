Thiết kế các ca sử dụng cho hệ thống "Payroll System"

1. Maintain Timecard
![Diagram](https://www.planttext.com/api/plantuml/png/V51B2i8m4Dtd54FslO0B4OfBHQYwbR4TQoIVagI58fxCXKVo2YPAfCNYm6pUo_jadlV7mdcqlbMIOUcDXQLgfEc901sGQXYpL7hKjIJOO6-Db4NlF2cuCWZJEYhH4V0L2kt3mbQe0DcAHuTTVaX4miUoFKfHeIV8psXhWdMhZcIJDh4VSgmiiAEVi0X-WswCXHz0biqdUqnWwUqu5sQ3deqrbt0H4Ffa-3-FOPNeyExRHHi8HiZPWdGLx_u2003__mC0)
Mô tả: Chức năng này cho phép nhân viên ghi lại thông tin thời gian làm việc của họ, bao gồm ngày làm việc, số giờ làm việc và mã số dự án (charge number).
Lý do thiết kế:
Actor: Nhân viên (Employee) là người duy nhất có quyền ghi nhận timecard.
Use Cases:
Validate Charge Number: Đảm bảo rằng mã số dự án được ghi nhận hợp lệ, liên kết với cơ sở dữ liệu dự án.
Save Timecard: Dữ liệu hợp lệ sẽ được lưu trữ vào cơ sở dữ liệu để phục vụ các chức năng xử lý lương và báo cáo.
Kết nối: Maintain Timecard là trung tâm, kết nối với các chức năng xác thực mã số và lưu trữ thông tin.

2. Process Payroll
![Diagram](s://www.planttext.com/api/plantuml/png/T91D2i9034RtEKNelbUGIXTk2-9QmZI8C3ymoIoAU38NFP9Ni2sDKAfPXJVlIyAyNsCZIbbBy41EKyQEXfoyF_RX7f44QMu0CZkbUFDimdaGvO0FmAcAi2DXhBgS78kOLCqJBkrrnIlTHbhohdZIPR85ld1YM_t4aVDg1uug5h47u_04M8x7kZxyE697pDli_cljrZKS-_aRFm000F__0m00)
Mô tả: Chức năng này cho phép quản trị viên xử lý bảng lương dựa trên thông tin timecard đã được lưu trữ.
Lý do thiết kế:
Actor: Quản trị viên (Payroll Admin) chịu trách nhiệm tính lương và tạo các khoản thanh toán.
Use Cases:
Calculate Pay: Dựa trên số giờ làm việc, loại hình công việc (lương cố định, theo giờ, hoa hồng), tính toán lương chi tiết.
Generate Payments: Tạo các khoản thanh toán, tích hợp với hệ thống ngân hàng hoặc xuất phiếu chi.
Kết nối: Process Payroll tích hợp với hệ thống thanh toán và đảm bảo nhân viên nhận được lương chính xác.
3. Generate Reports
![Diagram](s://www.planttext.com/api/plantuml/png/V95D2i8m44RtESNGVQyW5H5TYjQwbA4Tf9YVaaoH8fxCXKVo2ZQbqOgrMINVl1aUa-VzaJX6oxMI0dCs5fQgagOX0dH0gkhJ3JRMI3alLAbz1Vr524ivepv92i2kSKmAhWBQKplAqH54Az9aaGcsL1dBBl8ZzejZoFlukoahwG9hKri71sFFL8GkN-Zo4JurZDBB3E7sEO9cc2ENHaDQAXhYeI1kGhGRW3YUZSd-He7y24uptckQUAjq-_vdaf0k_0U-0000__y30000)

4. Manage Employee Information
![Diagram](s://www.planttext.com/api/plantuml/png/T95D2i8m44RtESNGVQyWBUh2XI18rp8qOn7oKvBfeeWdS-6Hl8AD9QNMDAimttl95_9-lWhFwBZJIc3Dri49UsULAgM-6K0F63P2EAePJQCe0kVUCscu2nXMvwb6Jv0TqM13iDUjiZqH7CpLPk6OQdiPinZzUgMKanJvOPQ6grOYhrmoPcblHufcNbJ6yQGyXFY-6V9yawZzDudSlEugjAYtoYqw5MHa-A8F0000__y30000)

5. Select Payment Method
![Diagram](s://www.planttext.com/api/plantuml/png/T9512eCm44NtESNGlLSeWdOf2D9r2N6emSI4P5n8wScww95wXIRLK6mrco5_tf_yCA_7C_V47OrQCIx8E3Xfgyo42Dm3QikOGq5yk2g4ca_EADLCdb33ZK4ueqV1FSAXGHN0o6WS22gaphI7EELSNERcqblxYiwOK4iPtu4IhV6IaczM5t7JLt6feEXGzCaJbO-moTTIzADDx7nZTyR2Lo7BZlzXVuL4hQFjKTymUyGI8SUXZKju0m00__y30000)
