# I. Phân tích kiến trúc

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
### Biểu đồ mô tả kiến trúc
![PlantText](https://www.planttext.com/api/plantuml/png/Z5HBJiCm4Dtd555NHO8xq3O8HK824Ng0mPca5euTnauXGZqP2ux45N0-_SKsu4qKpVEycVV6y_tvTQqDa6ag4TN0Ng34UFQ89TU6m70buwpL1gjP_175zXmmQuqKfz8W5S1m7-uE4w1rd9acHsdMwKcaFzGdHrgfXZJEBywZMuvlZrWhCYkWV1g5FB-dX5JjNDvDw1z85QYr8hS0pKkvhf_K4mBRJ1a8cQBybY17xQjjRElEjk2mxw9pYHPrBJWRLBo35ibLwLJf36dB6ORq6fddUlYcoMNCUXNIP58dsu0iCMCRp1k1_xWWbU55wo6eh8IsbR3CIou4bsMWT8qo7n6fBDGnSpZXO6mWNubcY3lM72896k12pzrE_HubO21UC6OR3Naq9Ew6KdEZg0rMjMpJn4Ey1os4SAkVzZ-Qy2lRYEdfF98EqiCM9uR-ux7yIdj0zSJr_izBVS0USNyvSVDkXro261UE3Xcnieu9LIRBQOcl3L8Rc8-Js5yJSkJR3tTVpvJjsGOzBmOgrRXIZxqwI_FgohSb1gndUtHmTs07k6UGExYZQhIBhkspxFRz3m000F__0m00)

# II. Cơ chế phân tích
## Các Cơ Chế Cần Giải Quyết

### 1. Xác Thực và Phân Quyền (Authentication and Authorization)
**Lý do**: Đảm bảo rằng chỉ những người dùng được phép mới có thể truy cập vào hệ thống và thực hiện các hành động tương ứng với quyền hạn của họ (sinh viên, giảng viên, quản trị viên).

**Cơ chế**: Sử dụng các phương thức xác thực như username/password, OAuth, và phân quyền thông qua các vai trò và quyền hạn cụ thể.

### 2. Đăng Ký và Quản Lý Khóa Học (Course Registration and Management)
**Lý do**: Đảm bảo quy trình đăng ký khóa học diễn ra mượt mà, sinh viên có thể chọn và đăng ký các khóa học phù hợp, và các khóa học được quản lý hiệu quả.

**Cơ chế**: Xây dựng dịch vụ đăng ký khóa học, kiểm tra điều kiện khóa học, quản lý số lượng sinh viên đăng ký và cung cấp thông tin thay thế khi khóa học đầy.

### 3. Thông Báo và Cảnh Báo (Notification and Alerts)
**Lý do**: Cung cấp thông tin kịp thời cho sinh viên và giảng viên về các thay đổi trong đăng ký khóa học, thời gian thay đổi lịch học, và các thông báo quan trọng khác.

**Cơ chế**: Sử dụng email, SMS, hoặc thông báo đẩy (push notifications) để gửi thông báo và cảnh báo tới người dùng.

### 4. Quản Lý Điểm (Grade Management)
**Lý do**: Giúp giảng viên nhập và quản lý điểm số của sinh viên, đồng thời cung cấp cho sinh viên khả năng tra cứu điểm số một cách bảo mật.

**Cơ chế**: Xây dựng dịch vụ quản lý điểm, bao gồm các công cụ để nhập điểm, tính toán điểm trung bình, và cung cấp báo cáo điểm số trực tuyến.

### 5. Bảo Mật Dữ Liệu (Data Security)
**Lý do**: Bảo vệ thông tin nhạy cảm của sinh viên và giảng viên, ngăn chặn truy cập trái phép và bảo vệ dữ liệu khỏi các mối đe dọa bảo mật.

**Cơ chế**: Sử dụng mã hóa dữ liệu (encryption), bảo mật truyền thông (SSL/TLS), và các chính sách bảo mật nghiêm ngặt để bảo vệ dữ liệu.

### 6. Tích Hợp Hệ Thống Cũ (Legacy System Integration)
**Lý do**: Đảm bảo hệ thống mới có thể truy cập và sử dụng dữ liệu từ hệ thống cũ một cách hiệu quả mà không làm gián đoạn hoạt động của hệ thống.

**Cơ chế**: Sử dụng giao diện SQL mở để truy cập cơ sở dữ liệu hiện tại và xây dựng các dịch vụ tích hợp dữ liệu từ hệ thống cũ.

# III. Phân Tích Ca Sử Dụng Payment

## Các Lớp Phân Tích

### 1. Payment
- **Mô tả**: Lớp này chịu trách nhiệm lưu trữ thông tin về các giao dịch thanh toán của sinh viên.
- **Thuộc tính**:
  - paymentId: String
  - amount: Double
  - date: Date
  - status: String
- **Quan hệ**:
  - N/A

### 2. Student
- **Mô tả**: Lớp này đại diện cho sinh viên thực hiện thanh toán.
- **Thuộc tính**:
  - studentId: String
  - name: String
  - email: String
- **Quan hệ**:
  - Một sinh viên có nhiều giao dịch thanh toán (1-n với Payment)

### 3. CourseRegistration
- **Mô tả**: Lớp này đại diện cho thông tin đăng ký khóa học của sinh viên.
- **Thuộc tính**:
  - registrationId: String
  - courseId: String
  - studentId: String
- **Quan hệ**:
  - Một đăng ký khóa học liên kết với một giao dịch thanh toán (1-1 với Payment)

### 4. BillingSystem
- **Mô tả**: Lớp này chịu trách nhiệm xử lý thanh toán và cập nhật trạng thái thanh toán.
- **Thuộc tính**:
  - systemId: String
  - name: String
- **Quan hệ**:
  - N/A
## Sơ đồ 
![PlantText](https://www.planttext.com/api/plantuml/png/R94zZW8n34RxdC9AJq5BXPPjw11p0ZEn8DhyeDWfHeYJRS6Hk09XXW42aoB5S_py9Rd-NvOic2HxfrJha1ass7aA0YS5PJMIRDZ3SO1hqyFVc7UE07tCGGQ2Gc3AzjvKp99PdKTp8zbycNc03_C31lILYJnQznAjOavCMzfRbeHYOwYTwQrIYzk-isQl1Cy1FzQvKcew5l8VUNis4RSqZnVKSmsp6UYWdw-v07r0rceY-dXwNfss32N27ncGg5KTQDf_JB4bPYfJbXJC_Kjl0000__y30000)

# IV. Phân tích ca sử dụng Maintain Timecard
## Các Lớp Phân Tích

### 1. Student
**Mô tả**: Lớp này đại diện cho sinh viên thực hiện việc duy trì timecard.

**Thuộc tính**:
- studentId: String
- name: String
- department: String

**Quan hệ**:
- Một sinh viên có nhiều timecards (1-n với Timecard)

### 2. Timecard
**Mô tả**: Lớp này lưu trữ thông tin về timecard của sinh viên.

**Thuộc tính**:
- timecardId: String
- date: Date
- hoursWorked: Double
- studentId: String

**Quan hệ**:
- Một timecard thuộc về một sinh viên (n-1 với Student)

### 3. TimecardSystem
**Mô tả**: Lớp này chịu trách nhiệm xử lý và cập nhật timecard.

**Thuộc tính**:
- systemId: String
- name: String

**Quan hệ**:
- N/A

## Nhiệm Vụ của Từng Lớp Phân Tích 
### Student
**Nhiệm vụ**: Thực hiện việc nộp timecard và nhận xác nhận từ hệ thống. 
### Timecard 
**Nhiệm vụ**: Lưu trữ thông tin về timecard của sinh viên. 
### TimecardSystem 
**Nhiệm vụ**: Xử lý việc nộp timecard, lưu trữ timecard và cập nhật hệ thống tính

## Sơ đồ phân tích
![PlantText](https://www.planttext.com/api/plantuml/png/T50n3i8m3Dpz2Yjx1rQc3YpCHM9EQmigcWJ5pe0GBsFWINo1G8iefNYmvDFvxkpxzLQAsgZ9TT1qLWGhJSHUyGoOgzBO-XrA3wvf37hhU3mJ7xEIopoumA2sQHqtDjAtd0xeeBUooaYvzLD8TSUu3odADiG3qtoI7u_g9Cfk4lo5pUJEsm3lMyt2O56WyUOJU8b6KkrQ5GCJXtzq3P4p6qhsz7pe0m00__y30000)

## Giải Thích

### Student
**Mô tả**: Đại diện cho sinh viên thực hiện việc duy trì timecard.

**Thuộc tính**:
- studentId
- name
- department

**Quan hệ**: Một sinh viên có nhiều timecards (1-n với Timecard).

### Timecard
**Mô tả**: Lưu trữ thông tin về timecard của sinh viên.

**Thuộc tính**:
- timecardId
- date
- hoursWorked
- studentId

**Quan hệ**: Một timecard thuộc về một sinh viên (n-1 với Student).

### TimecardSystem
**Mô tả**: Xử lý và cập nhật timecard.

**Thuộc tính**:
- systemId
- name

**Quan hệ**: Lưu trữ nhiều timecards (1-n với Timecard) và cập nhật hệ thống tính lương (1-n với PayrollSystem).

# V.Phân Tích Hệ Thống Đăng Ký Sinh Viên: Payment và Maintain Timecard

## Các Lớp Phân Tích

### 1. Student
**Mô tả**: Lớp này đại diện cho sinh viên thực hiện việc duy trì timecard và thanh toán.

**Thuộc tính**:
- studentId: String
- name: String
- department: String

**Quan hệ**:
- Một sinh viên có nhiều timecards (1-n với Timecard)
- Một sinh viên có nhiều giao dịch thanh toán (1-n với Payment)

### 2. Timecard
**Mô tả**: Lớp này lưu trữ thông tin về timecard của sinh viên.

**Thuộc tính**:
- timecardId: String
- date: Date
- hoursWorked: Double
- studentId: String

**Quan hệ**:
- Một timecard thuộc về một sinh viên (n-1 với Student)

### 3. Payment
**Mô tả**: Lớp này chịu trách nhiệm lưu trữ thông tin về các giao dịch thanh toán của sinh viên.

**Thuộc tính**:
- paymentId: String
- amount: Double
- date: Date
- status: String

**Quan hệ**:
- Một payment thuộc về một sinh viên (n-1 với Student)

### 4. CourseRegistration
**Mô tả**: Lớp này đại diện cho thông tin đăng ký khóa học của sinh viên.

**Thuộc tính**:
- registrationId: String
- courseId: String
- studentId: String

**Quan hệ**:
- Một đăng ký khóa học liên kết với một giao dịch thanh toán (1-1 với Payment)

### 5. TimecardSystem
**Mô tả**: Lớp này chịu trách nhiệm xử lý và cập nhật timecard.

**Thuộc tính**:
- systemId: String
- name: String

**Quan hệ**:
- Lưu trữ nhiều timecards (1-n với Timecard)

### 6. BillingSystem
**Mô tả**: Lớp này chịu trách nhiệm xử lý thanh toán và cập nhật trạng thái thanh toán.

**Thuộc tính**:
- systemId: String
- name: String

**Quan hệ**:
- Cập nhật trạng thái thanh toán (1-n với Payment)

### 7. PayrollSystem
**Mô tả**: Lớp này chịu trách nhiệm xử lý tính lương dựa trên thông tin timecard.

**Thuộc tính**:
- systemId: String
- name: String

**Quan hệ**:
- Nhận cập nhật từ hệ thống timecard (n-1 với TimecardSystem)

## Nhiệm Vụ của Từng Lớp Phân Tích

### Student
**Nhiệm vụ**: Thực hiện việc nộp timecard, đăng ký khóa học, và nhận xác nhận từ hệ thống về cả hai hành động.

### Timecard
**Nhiệm vụ**: Lưu trữ thông tin về timecard của sinh viên.

### Payment
**Nhiệm vụ**: Lưu trữ thông tin về các giao dịch thanh toán của sinh viên.

### CourseRegistration
**Nhiệm vụ**: Quản lý thông tin đăng ký khóa học của sinh viên.

### TimecardSystem
**Nhiệm vụ**: Xử lý việc nộp timecard, lưu trữ timecard và cập nhật hệ thống tính lương.

### BillingSystem
**Nhiệm vụ**: Xử lý thanh toán, cập nhật trạng thái thanh toán, và thông báo cho sinh viên.

### PayrollSystem
**Nhiệm vụ**: Xử lý và cập nhật thông tin tính lương dựa trên timecard được gửi lên từ hệ thống.

## Biểu Đồ Sequence

![PlantText](https://www.planttext.com/api/plantuml/png/d5FBJiCm4BpdArQ-zz0hfmguz8O84cStNXMhVaJUzQ52V1a7FebVODCy6hUf4EGGoPEPsV7O-VxysX3hnDcxgd6Q26hE1WF3UmNor9nis0FruDRCmQ0zpjS6Mt7omgi-gi7jnNfiT3Ab7G_euFUe6S78gr_5l7C8Rp4dUetfW6OvoJJZIH_zLUAs1yS9lQVsCKkwwvcJkUPCP-U7BWC-uzuI9yqsXd98cdqfksbEokrlqSTwwYCn-elEJzX2vPFwtZedwF_4qbgAplrLF5uFjLQmMe4Awdp6Tw0exxnbKakyyPo4vlK1XRJGxyXV5tnB83kLgm0SLNNHsgqe75Ctv3Qxh40akUrkX6ZAPfVtqARO8557ts0mtH_q0m00__y30000)

