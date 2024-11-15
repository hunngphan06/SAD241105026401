# 1. Phân tích kiến trúc

## * Đề xuất kiến trúc

### Dựa trên các yêu cầu đã nêu trong tài liệu:

#### - Hệ thống Payroll System cần hỗ trợ các nghiệp vụ như quản lý thông tin nhân viên, tính toán tiền lương, lưu trữ thời gian làm việc, và hỗ trợ truy cập bảo mật.

#### - Kiến trúc đề xuất là Client-Server Architecture với các thành phần chính :

##### + Client Layer: Giao diện người dùng để tương tác (Desktop UI dựa trên Windows).
##### + Application Server: Chứa logic nghiệp vụ xử lý yêu cầu từ Client.
##### + Database Server: Lưu trữ thông tin nhân viên, dự án và các nghiệp vụ liên quan.

## * Giải thích thành phần
### Client Layer: Giao diện Windows giúp nhân viên và quản trị viên dễ sử dụng để đăng nhập, cập nhật timecard, chọn phương thức thanh toán, v.v.
### Application Server:
#### Thực hiện các yêu cầu bảo mật (xác thực/ủy quyền).
#### Xử lý các thao tác liên quan đến nghiệp vụ như thêm, sửa, xóa dữ liệu timecard và chọn phương thức thanh toán.
#### Tương tác với Database Server qua JDBC để lấy dữ liệu.
### Database Server: Sử dụng DB2 để lưu dữ liệu nhân viên, thời gian làm việc, và các giao dịch thanh toán. Kế thừa và tích hợp với cơ sở dữ liệu quản lý dự án hiện có.
