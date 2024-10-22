Tên: Hán Thị Triểu
Mã SV: 445101008

1. Phân tích kiến trúc
- Model:
  + Model sẽ tương tác với cơ sở dữ liệu.
  + Chứa các thành phần quản lý dữ và logic nghiệp vụ.
  + Bao gồm các lớp dữ liệu: Sinh viên, Giảng viên, Khóa học, Bảng điểm, Thanh toán.
- View:
  + Hiển thị thông tin cho người dùng (sinh viên, giảng viên, quản trị viên) và nhận đầu vào từ người dùng.
  + Các thành phần hiển thị các giao diện người dùng của ứng dụng: Giao diện đăng nhập, giao diện đăng ký sinh viên, giao diện đăng ký giảng, giao diện đăng ký khóa học, giao diện xem bảng điểm, giao diện thanh toán, giao diện đăng ký giảng dạy các khóa học, giao diện ghi lại điểm, giao diện danh mục khóa học,...
- Controller:
  + Các thành phần xử lý tương tác của người dùng để làm việc với Model (cập nhật logic dữ liệu) hoặc/ và với View (cập nhật hiển thị giao diện người dùng).
  + Nhận yêu cầu từ người dùng, gọi Model để xử lý logic nghiệp vụ và sau đó trả kết quả về View để hiển thị cho người dùng.
  

