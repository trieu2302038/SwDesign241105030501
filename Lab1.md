Tên: Hán Thị Triểu
Mã SV: 445101008

1. Phân tích kiến trúc

1.1 Đề xuất kiến trúc MVC cho hệ thống
- Model:
  + Model sẽ tương tác với cơ sở dữ liệu.
  + Chứa các thành phần quản lý dữ và logic nghiệp vụ.
- View:
  + Cung cấp giao diện cho người dùng và nhận đầu vào từ người dùng.
- Controller:
  + Các thành phần xử lý tương tác của người dùng để làm việc với Model (cập nhật logic dữ liệu) hoặc/ và với View (cập nhật hiển thị giao diện người dùng).
  + Nhận yêu cầu từ người dùng, gọi Model để xử lý logic nghiệp vụ và sau đó trả kết quả về View để hiển thị cho người dùng.
  
=> Với cách tiếp cận này, MVC đáp ứng tốt yêu cầu bảo mật, tính năng phân chia logic, và khả năng mở rộng, giúp xây dựng hệ thống dễ dàng quản lý và hiệu quả.

1.2 Biểu đồ package mô tả kiến trúc MVC
![Diagram](https://www.planttext.com/api/plantuml/png/R99D2i8m48NtSugX6rUzWXJKfI0exaCxQZ0_9Ob8aPxCXKVo2hOrQcAoVM_utdimp_kZieuPTv42MbQVsP6msB3EQ25msrb7ii0R87xDjMv8l3N4MZ1hSILReJkYGDfnIJKpJI0DL4dA3KeVylQShddSw6IGVxB7UZL2BxHoun0oSO3VzxCpuLdpKo5h-YAHrqCFCrpIWIj2Gu8vhfKzyTP2k1BBSfvB3YTFDva2mVxf9Aq1AJaAX9GQXK6238C0AbBD-3yl0000__y30000)
2. Cơ chế phân tích
Đề xuất các cơ chế:
- Lưu trữ dữ liệu:
  + Lưu trữ thông tin nhân viên, bao gồm tên, địa chỉ, phương thức thanh toán (chuyển khoản ngân hàng, nhận tại văn phòng, qua bưu điện), thông tin về lương (lương theo giờ, lương cố định, hoặc có hoa hồng).
  + Lưu trữ thông tin thời gian làm việc, đơn hàng bán hàng (cho nhân viên có hoa hồng) và các loại dữ liệu thanh toán.
  -> Lý do: Cần lưu trữ các thông tin liên quan đến lương, giờ làm việc và các đơn hàng để tính toán lương chính xác và quản lý thanh toán đúng hạn.
- Bảo mật:
  + Xác thực: Chỉ cho phép người dùng hợp lệ (như nhân viên và quản trị viên) đăng nhập và truy cập vào hệ thống. Lý do: Bảo vệ hệ thống khỏi các truy cập trái phép và đảm bảo rằng chỉ người dùng có quyền mới có thể thao tác với dữ liệu quan trọng như thông tin lương và thanh toán.
  + Phân quyền: Phân quyền cho từng loại người dùng, bao gồm nhân viên (chỉ truy cập và sửa chữa thông tin của chính mình), quản trị viên (quản lý thông tin người dùng và tạo báo cáo), và nhân viên bộ phận thanh toán (truy cập và xử lý thông tin thanh toán). Lý do: Đảm bảo rằng mỗi loại người dùng chỉ có thể truy cập vào các chức năng và dữ liệu mà họ có quyền sử dụng, đảm bảo tính bảo mật và phân quyền rõ ràng trong hệ thống.
  + Mã hóa: Mã hóa thông tin nhạy cảm như dữ liệu tài khoản ngân hàng, thông tin thanh toán và bảng lương của nhân viên. Lý do: Bảo vệ thông tin quan trọng khỏi các mối đe dọa bảo mật, giảm thiểu rủi ro bị lộ lọt thông tin nhạy cảm.
- Xử lý thanh toán:
  + Sau khi nhân viên hoàn tất việc đăng ký hoặc hoàn thành công việc, hệ thống sẽ gửi thông tin đến hệ thống thanh toán để tạo hóa đơn và xử lý thanh toán tự động.
  + Đảm bảo rằng chỉ những nhân viên đã thanh toán học phí hoặc các khoản chi phí (nếu có) mới có thể thực hiện các giao dịch tiếp theo hoặc yêu cầu thanh toán.
  + Sau khi nhân viên thanh toán, hệ thống sẽ gửi hóa đơn điện tử đã thanh toán cho nhân viên qua email hoặc phương thức liên lạc đã đăng ký.
  -> Lý do: Đảm bảo rằng hệ thống thanh toán hoạt động tự động và chỉ thanh toán cho những nhân viên có đủ điều kiện, đồng thời cung cấp bằng chứng thanh toán cho nhân viên để duy trì tính minh bạch.
- Cơ chế thông báo:
  + Thông báo tình trạng thanh toán: Nếu giao dịch thanh toán không thành công (ví dụ: tài khoản ngân hàng không hợp lệ), hệ thống sẽ gửi thông báo ngay cho nhân viên và yêu cầu họ cập nhật lại thông tin thanh toán.
  + Thông báo về tình trạng lương: Hệ thống sẽ thông báo về các thay đổi trong lương (ví dụ: tăng lương, hoa hồng mới, v.v.) để nhân viên nắm bắt kịp thời.
  + Thông báo khi thanh toán thành công: Sau khi thanh toán thành công, hệ thống sẽ gửi thông báo xác nhận cho nhân viên về việc họ đã nhận được thanh toán và gửi bản sao hóa đơn điện tử.
  -> Lý do: Đảm bảo rằng nhân viên luôn nhận được thông tin kịp thời về tình trạng thanh toán và các thay đổi liên quan đến lương của họ. Điều này giúp duy trì sự minh bạch và giảm thiểu các tranh chấp về thanh toán.
  - Cơ chế báo cáo và theo dõi
  + Hệ thống sẽ cung cấp các báo cáo tự động về tình trạng thanh toán, lương của nhân viên, tổng số giờ làm việc và các khoản hoa hồng.
  + Báo cáo sẽ được gửi tự động cho quản trị viên và nhân viên khi có sự thay đổi hoặc vào các thời điểm nhất định (ví dụ: vào cuối mỗi tuần hoặc cuối tháng).
  -> Lý do: Đảm bảo rằng hệ thống cung cấp thông tin cần thiết cho các bên liên quan để quản lý và theo dõi các khoản thanh toán cũng như tình trạng lương của nhân viên.
    
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
