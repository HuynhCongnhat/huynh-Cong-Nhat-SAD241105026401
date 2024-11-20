#I. Phân tích kiến trúc


## Giới Thiệu
Trong bài lab này, chúng ta sẽ phân tích hệ thống đăng ký sinh viên cho Wylie College. Hệ thống mới sẽ thay thế hệ thống cũ sử dụng công nghệ mainframe và cho phép sinh viên đăng ký khóa học và xem bảng điểm từ máy tính cá nhân trên mạng LAN của trường.

## Yêu Cầu Hệ Thống
### Chức Năng Chính
1. **Đăng ký khóa học**: Sinh viên có thể chọn 4 khóa học chính và 2 khóa học thay thế mỗi học kỳ.
2. **Thay đổi lịch trình**: Sinh viên có thể thêm hoặc bỏ khóa học trong thời gian cho phép.
3. **Xem bảng điểm**: Sinh viên có thể truy cập hệ thống để xem bảng điểm điện tử cuối học kỳ.
4. **Giảng dạy và ghi điểm**: Giáo sư có thể đăng ký giảng dạy và ghi điểm cho sinh viên.

### Phi Chức Năng
1. **Hiệu Suất**: Hệ thống phải truy cập dữ liệu từ cơ sở dữ liệu cũ một cách nhanh chóng.

## Kiến Trúc Hệ Thống
### Kiến Trúc Client-Server
- **Client (Frontend)**: Sử dụng HTML, CSS, JavaScript, và một framework frontend như React hoặc Angular.
- **Server (Backend)**: Sử dụng Node.js, ASP.NET Core, hoặc Java Spring Boot để xử lý logic kinh doanh và truy cập cơ sở dữ liệu.

### Tầng Ứng Dụng
- **Application Server**: Xử lý các yêu cầu từ client, thực hiện các hoạt động như đăng ký khóa học, thay đổi lịch trình, truy xuất bảng điểm và ghi điểm.

### Truy Cập Cơ Sở Dữ Liệu
- **Data Access Layer (DAL)**: Kết nối và truy vấn cơ sở dữ liệu catalog khóa học cũ mà không cập nhật nó.


