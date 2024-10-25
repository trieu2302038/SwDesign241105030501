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
  
=> Với cách tiếp cận này, MVC đáp ứng tốt yêu cầu bảo mật, tính năng phân chia logic, và khả năng mở rộng, giúp xây dựng hệ thống dễ dàng quản lý và hiệu quả.

1.2 Biểu đồ package mô tả kiến trúc MVC
![Diagram](https://www.planttext.com/api/plantuml/png/V9D1JiCm44NtFaKkq2jK5UscKe6AIkodpZXOk1vaJuGgr9Enu4XS0SUj4iTsoNB-r_ZzcSdlzy_ACpZkJqPyW7o73firMNPa3BhcIpJXamQyRrwmqvuTi2OxMHB3tf52xybLrGFtBLgkQZlgTBtdWpP6soxHBc84VQGMpOpnzaWDAgcjgNSUYyApKkZ2OtSobrI7isSyRIsZKo3JXZliG9utm704ZvCZWN_L-3bZZqFO1wdCim7_TYHmRIrOJRm6sbf5MSCdOgsqZ86Y58YIVIyMo-jKy-90AqInmwWLa9L3YCOAShRvQ9i6KJ-vQCeI_kCi8eiSEDZ6ooaP1tMwelcxWtQxfdl2U5LYXROT_hC_0000__y30000)
2. Cơ chế phân tích
Đề xuất các cơ chế:
- Lưu trữ dữ liệu:
  + Lưu trữ thông tin tài khoản người dùng (Sinh viên, giảng viên, và quản trị viên), thông tin đăng ký khóa học, điểm số và tài khoản người dùng.
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

3. Phân tích ca sử dụng Payment
Các lớp chính trong ca sử dụng “Payment”
- Student: Đại diện cho sinh viên thực hiện thanh toán.
- Registration: Đại diện cho quá trình đăng ký các khóa học của sinh viên trong hệ thống.
- PaymentProcessor: Xử lý các yêu cầu thanh toán từ sinh viên, bao gồm xác nhận và thực hiện thanh toán.
- BillingSystem: Giao diện kết nối với hệ thống thanh toán bên ngoài để quản lý các hóa đơn và nhận thông tin thanh toán từ PaymentProcessor.
- Invoice: Đại diện cho hóa đơn mà sinh viên cần thanh toán.
- Transaction: Ghi lại thông tin giao dịch khi thanh toán được thực hiện.

![Diagram](https://www.planttext.com/api/plantuml/png/Z991JiCm44NtEOMNxO8BH0WL24YLM5I42pZsABBasCKp1Yh4oLXm9Ax0975CqdPHBopvU_JV-7j-ltysI39Gx6nHA2iHHKrHWoFnMGXULmB7yxOg-IeOroRToGwEf4PQwHIhbO-DXK4L8i1h1AITF7JiirgNuiqRNNnDm6Te3LAGPBpBr30JJz3Anu3mn0MbwFVh-q6uIK0bhOfM4Zm2OCzBxMHYQcKNl0947pALWGwbEWlbd2ZYGXHYFrfCRvETZuucu3eNP_ATiPQ5-e04NSOsetg4pEuF7mJ1INinPUiuOGNPtupdaoSjZPAe8rIS7QkyfqPQeDkXjeem2tIyZ7lDbVKGpyh1Uxq8wkIxN_uplYXtlMpcRDVza2aVzCnxFcV51fpkH_mF003__mC0)

4. Phân tích ca sử dụng Maintain Timecard
Các lớp cho ca sử dụng Maintain Timecard
- Employee: Đại diện cho nhân viên có thời gian làm việc cần được ghi lại.
- Timecard: Lưu trữ thông tin về thời gian làm việc của nhân viên trong một khoảng thời gian nhất định.
- TimecardProcessor: Xử lý các thao tác ghi nhận, cập nhật và lưu trữ dữ liệu từ Timecard.
- PayrollSystem: Giao diện kết nối với hệ thống tính lương để xử lý và lưu thông tin về thời gian làm việc.
- Project: Thể hiện các dự án mà nhân viên đã dành thời gian làm việc và cần ghi nhận.

![Diagram](https://www.planttext.com/api/plantuml/png/T99D2i8m44RtFSKiTU45kd9HGJSYABYEoL2hIQTCKg689tFXaRo23KtgJp2BGBw1Ds-IFE-FkNM2NMjqbaajh8M5QJHrY73De5ypm12iYXosZgkw38LQ6FoA0Df62OUxog0Kh2RJ72vKgUmMuR4ombq84lYHMhPxuZEg70fg3nf3nNVeetuFJHabiVBeiU6lpN-J3PD4Qub7fIOcFquGA__7suYEIUjjPnsQDt184zpWlVI3Jk8zvADO2cSweNIVdlwSt5p8r-dhz9Igh0FdqtwEjV9Vu0K00F__0m00)
