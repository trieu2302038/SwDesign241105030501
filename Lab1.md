Tên: Hán Thị Triểu
Mã SV: 445101008

1. Phân tích kiến trúc
1.1 Đề xuất kiến trúc MVC cho hệ thống
- Model:
  + Model sẽ tương tác với cơ sở dữ liệu.
  + Chứa các thành phần quản lý dữ và logic nghiệp vụ.
- View:
  + Hiển thị thông tin cho người dùng (sinh viên, giảng viên, quản trị viên) và nhận đầu vào từ người dùng.
  + Các thành phần hiển thị các giao diện người dùng của ứng dụng.
- Controller:
  + Các thành phần xử lý tương tác của người dùng để làm việc với Model (cập nhật logic dữ liệu) hoặc/ và với View (cập nhật hiển thị giao diện người dùng).
  + Nhận yêu cầu từ người dùng, gọi Model để xử lý logic nghiệp vụ và sau đó trả kết quả về View để hiển thị cho người dùng.
  
=> Với cách tiếp cận này, MVC đáp ứng tốt yêu cầu bảo mật, tính năng phân chia logic, và khả năng mở rộng của Payroll System, giúp xây dựng hệ thống dễ dàng quản lý và hiệu quả.

1.2 Biểu đồ package mô tả kiến trúc MVC

![Diagram](https://www.planttext.com/api/plantuml/png/V9D1JiCm44NtFaKkq2jK5UscKe6AIkodpZXOk1vaJuGgr9Enu4XS0SUj4iTsoNB-r_ZzcSdlzy_ACpZkJqPyW7o73firMNPa3BhcIpJXamQyRrwmqvuTi2OxMHB3tf52xybLrGFtBLgkQZlgTBtdWpP6soxHBc84VQGMpOpnzaWDAgcjgNSUYyApKkZ2OtSobrI7isSyRIsZKo3JXZliG9utm704ZvCZWN_L-3bZZqFO1wdCim7_TYHmRIrOJRm6sbf5MSCdOgsqZ86Y58YIVIyMo-jKy-90AqInmwWLa9L3YCOAShRvQ9i6KJ-vQCeI_kCi8eiSEDZ6ooaP1tMwelcxWtQxfdl2U5LYXROT_hC_0000__y30000)
2. Cơ chế phân tích
Đề xuất các cơ chế:
- Lưu trữ dữ liệu:
  + Lưu trữ thông tin của tài khoản người dùng (Sinh viên, giảng viên, và quản trị viên), thông tin đăng ký khóa học, điểm số và tài khoản người dùng.
- Bảo mật:
  + Xác thực: Chỉ những người dùng hợp lệ mới có thể truy cập vào hệ thống.
  + Phân quyền: Cho sinh viên, giảng viên và quản trị viên.
  + Mã hóa: Thông tin quan trọng như bảng điểm của sinh viên và dữ liệu đăng nhập.
- Xử lý thanh toán:
  + Sau khi sinh viên hoàn tất việc đăng ký, hệ thống sẽ gửi thông tin đến hệ thống thanh toán để tạo hóa đơn.
  + Đảm bảo rằng chỉ những sinh viên đã thanh toán học phí trước đó mới có thể đăng ký khóa học mới.
  + Sau khi sinh viên thanh toán học phí, hệ thống sẽ gửi bill điện tử đã thanh toán.
- Cơ chế thông báo:
  + Thông báo tình trạng khóa học: Nếu khóa học bị hủy cần thông báo ngay cho sinh viên.
  + Sau khi đăng ký khóa học thành công, hệ thống sẽ gửi thông báo xác nhận đăng ký thành công.
  

