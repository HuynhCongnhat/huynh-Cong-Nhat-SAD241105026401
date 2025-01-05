#  BÁO CÁO CUỐI KỲ
# A WILDERNESS WEATHER STATION

## Mục lục
#### I. Mô tả công việc
1. **Thông tin thành viên nhóm, vai trò**
2. **Phân công công việc, mức độ hoàn thành**
#### II. Mô tả tóm tắt bài toán
1. **Sự cần thiết, lợi ích khi giải quyết bài toán**
2. **Các yêu cầu chức năng**
3. **Các yêu cầu phi chức năng**
#### III. Phân tích các ca sử dụng
1. **Kiến trúc đề xuất**
2. **Các cơ chế phân tích**
3. **Kết quả phân tích của từng ca sử dụng**
#### IV. Xác định các phần tử thiết kế
#### V. Thiết kế hệ thống con
#### VI. Thiết kế các lớp
#### VII. Kết luận

---

## I. Mô tả công việc
### 1. Thông tin thành viên nhóm, vai trò

| Mã sinh viên | Họ và tên | Vai trò |
| ------ | ---------- | ------- |
| 4551190041  | Lê Thị Hồng Nhung | Nhóm trưởng|
| 4551190040 | Huỳnh Công Nhất | Thành viên |
| 4551190039 | Nguyễn Hồ Khôi Nguyên | Thành viên |
| 4551190018 | Vũ Duy Giáp | Thành viên|

### 2. Phân công công việc, mức độ hoàn thành

| Thành viên nhóm | Phân công công việc | Mức độ hoàn thành |
| ------ | ---------- | ------- |
| Lê Thị Hồng Nhung | Mô tả bài toán, Thiết kế các lớp, Kết luận | 90% |
| Huỳnh Công Nhất | Mô tả bài toán, Phân tích các ca sử dụng  | 90% |
| Nguyễn Hồ Khôi Nguyên | Thiết kế hệ thống con | 90% |
| Vũ Duy Giáp | Xác định các phần tử thiết kế | 90% |

---

## II. Mô tả tóm tắt bài toán:
### 1. Sự cần thiết và lợi ích khi giải quyết bài toán:
#### 1.1. **Sự cần thiết:** 
Phần mềm được phát triển cho một trạm thời tiết hoang dã nhằm giúp theo dõi khí hậu và cải thiện độ chính xác của dự báo thời tiết ở các vùng xa xôi. Nó giải quyết các vấn đề sau:
- **Cơ sở hạ tầng hạn chế:** Nhiều khu vực xa xôi không có cơ sở hạ tầng về điện, giao thông và truyền thông.
- **Biến đổi khí hậu:** Việc theo dõi thời tiết và khí hậu ở các khu vực xa xôi là cần thiết để hiểu rõ hơn về ảnh hưởng của biến đổi khí hậu toàn cầu.
- **Thông tin dự báo:** Các thông tin thời tiết chính xác và kịp thời giúp các nhà dự báo thời tiết, nhà nghiên cứu và các tổ chức chính phủ lên kế hoạch và ứng phó với các hiện tượng thời tiết cực đoan.
- **Bảo trì khó khăn:** Việc bảo trì thiết bị tại các khu vực xa xôi có thể khó khăn và tốn kém. Hệ thống tự động hóa có thể giảm thiểu sự cần thiết phải bảo trì thường xuyên.

#### 1.2. **Lợi ích:**
- **Tăng cường năng lực thu thập dữ liệu:** Có thể thu thập và lưu trữ dữ liệu thời tiết từ nhiều khu vực khác nhau, giúp cải thiện độ chính xác của dự báo thời tiết và phân tích khí hậu.
- **Tiết kiệm chi phí:** Giảm chi phí vận hành và bảo trì nhờ vào thiết kế tự động và khả năng tự phục hồi của hệ thống.
- **Hỗ trợ nghiên cứu khí hậu:** Cung cấp dữ liệu quan trọng cho các nhà nghiên cứu về khí hậu, giúp hiểu rõ hơn về các xu hướng và biến đổi trong môi trường.
- **Tăng cường an ninh và an toàn:** Cung cấp thông tin thời tiết cần thiết cho các hoạt động ngoài trời, giúp bảo vệ con người và tài sản trong các tình huống thời tiết cực đoan.
- **Khả năng tái cấu hình và cập nhật:** Hệ thống có thể tự tái cấu hình và cập nhật phần mềm, đảm bảo tính linh hoạt và khả năng thích ứng với các thay đổi và yêu cầu mới.
- **Khả năng phát triển bền vững:** Sử dụng năng lượng tái tạo và công nghệ thông minh, giúp giảm thiểu tác động đến môi trường và hỗ trợ phát triển bền vững.

### 2. Các yêu cầu chức năng:
- **Thu thập dữ liệu thời tiết:** Hệ thống phải có khả năng thu thập dữ liệu từ các cảm biến khí hậu như nhiệt độ, độ ẩm, áp suất, tốc độ gió, và hướng gió.
- **Lưu trữ dữ liệu:** Dữ liệu thu thập phải được lưu trữ an toàn và có khả năng truy xuất khi cần.
- **Phân tích dữ liệu:** Hệ thống phải có khả năng phân tích dữ liệu thu thập để dự báo thời tiết và nhận diện các xu hướng khí hậu.
- **Gửi thông báo:** Hệ thống phải có khả năng gửi thông báo thời tiết cho các cơ quan dự báo và người dùng cuối.
- **Bảo trì tự động:** Hệ thống phải có khả năng tự động kiểm tra và thông báo về tình trạng của các thiết bị để giảm thiểu nhu cầu bảo trì thủ công.
- **Giao diện người dùng:** Cung cấp giao diện thân thiện và dễ sử dụng để người dùng có thể tương tác và theo dõi dữ liệu thời tiết.




