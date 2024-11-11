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
Ca sử dụng "Payment" tập trung vào việc xử lý thanh toán cho nhân viên dựa trên thông tin về thời gian làm việc (đối với nhân viên làm theo giờ) hoặc dựa trên các đơn hàng bán hàng (đối với nhân viên có hoa hồng). Hệ thống sẽ tự động tính toán và tạo thanh toán vào ngày quy định.
Các lớp phân tích chính trong ca sử dụng “Payment”:
- Employee: Đại diện cho thông tin của nhân viên.
- Timecard: Chứa dữ liệu về thời gian làm việc của nhân viên (chỉ - dành cho nhân viên làm theo giờ).
- SalesReceipt: Chứa dữ liệu về đơn hàng bán hàng của nhân viên (chỉ dành cho nhân viên có hoa hồng).
- Payroll: Xử lý các chức năng tính toán lương.
- Payment: Thực hiện chức năng thanh toán, bao gồm các phương thức thanh toán khác nhau.
- PaymentMethod: Lưu trữ thông tin về phương thức thanh toán mà nhân viên đã chọn (chuyển khoản, nhận trực tiếp, hoặc qua bưu điện).
- ProjectDatabase: Chứa thông tin về các dự án và mã số thanh toán cho từng dự án (chỉ để tham chiếu, không cập nhật).
![Diagram](https://www.planttext.com/api/plantuml/png/V5FBJiCm4BpdAwoS0AaLN7igKZXm0A6s4kUjlMei_8ZiDLA4-38EV1A_W9CwIPEqzSNoxEpCsfFy_VokFO6Ze5MMSGNUioTTALiZig-CnRLWc83dWgsOD9HW0neZi2KdpI5X88J3g361EuLTNSrQF2XmTKI53Nk52ULMQ-czj6O3X4Frkvjo9pLoSAAVKXnvHTmIKjhW_Bjr7oX6W_CIt05VWzwZIuLUTWiA_GOvoegkI8EsmT2PiTwWTbQflhM2kfXraoLGZnC9rYuEYWSLgL58ew6Rs_CcJUtKf3bFyadet3uLjWGK9b4nLZdBOuAdzfzMYfdv2r9fXzVNxV5Sli1vSz422QIQsNcaaU38iFyIyuUSBHOilrykx_8X-XKB7lqbsYZAIzIuTP6jM0aN6ITNFlAohctEYum36dJnnNtMOLVasicoDHhH_8N_0000__y30000)
Giải thích:
1. Employee là lớp chính liên kết với Timecard và SalesReceipt để ghi nhận thông tin làm việc của nhân viên theo giờ hoặc hưởng hoa hồng.
2. Payroll thực hiện tính toán lương dựa trên dữ liệu liên kết từ Employee, Timecard, và SalesReceipt.
3. Payment thực hiện thanh toán dựa trên phương thức thanh toán từ PaymentMethod.
4. Phân tích ca sử dụng Maintain Timecard
Các lớp cho ca sử dụng Maintain Timecard
- Employee: Đại diện cho nhân viên thực hiện việc ghi lại thông tin thời gian làm việc (timecard).
- Timecard: Lớp lưu trữ và quản lý thông tin về số giờ làm việc và ngày làm việc.
- ProjectManagementDB: Hệ thống cơ sở dữ liệu dự án hiện tại lưu trữ các thông tin về mã số dự án (charge number) để tính phí cho các giờ làm việc.
- TimecardRepository: Cơ chế lưu trữ và truy xuất dữ liệu Timecard từ cơ sở dữ liệu.

![Diagram](https://www.planttext.com/api/plantuml/png/b5FDJeD04Bxp51jED2alq8DfAXvCh35j4yzJ6065NTmPQeZnoJpuIBw2IzcbW7YGP9FDVFFjzyqFtvzVQsBGN9U5vyK548cRiYfKWoZUFM6-KA0Dt4PY9VQiSvbQH4A9qrW5JOcIjyYPIgPWzrIB7vfgGXMYX5ooEOUyn1Xq4YJ0k1IPgZKzAls2oLB46UWKx-loY7hXVJZJ3z1eLHJxXXZBthdXmn6e5OhirI9qJZH1Yw6rK6aL8v5piCFN6ec3ImkMuX-cj7h6cBSW8SMsw6ZJMnjIo7YuoubT1pjQXAONHOjjeRBsJb3ahVxrW1tyeUvg67PZL6quBC80JuK2dh4tFyJnFlnItM6bA6UbcrwVBJGgLmY24_OJTpacnSKMDYz5TY7QD6vBWnat2oTWNFNR78PNaorP2PzG6Zkwcx9WvNlZb3DfPeg6waP1jbT2TirwopcRU-PmgSoFDRPCt-k3mun1wrgBvc94SkbxtjhORV_K7m000F__0m00)
Giải thích: 
1. Employee gửi yêu cầu ghi nhận thông tin timecard.
2. PayrollSystem nhận yêu cầu và xác thực mã số dự án qua ProjectManagementDB.
3. Nếu mã số dự án hợp lệ, PayrollSystem tạo một bản ghi Timecard và lưu trữ thông qua TimecardRepository.
4. TimecardRepository đảm bảo bản ghi được lưu trữ an toàn trong cơ sở dữ liệu của hệ thống.
