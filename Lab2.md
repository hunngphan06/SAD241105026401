# Phân tích các ca sử dụng trong hệ thống Payroll System

## 1. Add Employee
### Mục đích:
Thêm một nhân viên mới vào hệ thống để quản lý thông tin cá nhân và chế độ trả lương.

### Tác nhân tham gia:
- **Admin:** Người sử dụng hệ thống để thêm nhân viên.

### Luồng chính:
1. Admin cung cấp thông tin nhân viên bao gồm: ID, tên, địa chỉ, loại nhân viên (salaried, hourly, commission).
2. Hệ thống kiểm tra dữ liệu đầu vào để đảm bảo hợp lệ (không trùng ID).
3. Lưu thông tin vào cơ sở dữ liệu nhân viên.

### Kết quả mong đợi:
Nhân viên mới được thêm thành công vào hệ thống.

---

## 2. Delete Employee
### Mục đích:
Loại bỏ thông tin của một nhân viên khi họ không còn làm việc tại công ty.

### Tác nhân tham gia:
- **Admin:** Người quản lý thông tin nhân viên.

### Luồng chính:
1. Admin nhập ID của nhân viên cần xóa.
2. Hệ thống tìm kiếm thông tin nhân viên dựa trên ID.
3. Nếu tìm thấy, hệ thống yêu cầu xác nhận từ Admin.
4. Sau khi xác nhận, hệ thống xóa thông tin nhân viên khỏi cơ sở dữ liệu.

### Kết quả mong đợi:
Thông tin nhân viên bị xóa thành công.

---

## 3. Maintain Timecard
### Mục đích:
Quản lý bảng chấm công cho nhân viên làm việc theo giờ, hỗ trợ tính lương chính xác.

### Tác nhân tham gia:
- **Admin hoặc nhân viên được ủy quyền:** Người chịu trách nhiệm nhập dữ liệu chấm công.

### Luồng chính:
1. Người dùng nhập ID nhân viên, ngày làm việc, và số giờ làm việc.
2. Hệ thống kiểm tra tính hợp lệ của thông tin (ví dụ: số giờ không âm).
3. Lưu bảng chấm công vào cơ sở dữ liệu.

### Kết quả mong đợi:
Bảng chấm công được lưu trữ thành công.

---

## 4. Maintain Sales Receipt
### Mục đích:
Lưu thông tin doanh số của nhân viên làm việc theo mô hình doanh thu (commission-based).

### Tác nhân tham gia:
- **Admin hoặc nhân viên bán hàng:** Người nhập thông tin biên lai.

### Luồng chính:
1. Người dùng nhập ID nhân viên, ngày bán hàng, và số tiền doanh số.
2. Hệ thống xác thực thông tin.
3. Lưu thông tin biên lai vào cơ sở dữ liệu.

### Kết quả mong đợi:
Biên lai bán hàng được lưu trữ thành công.

---

## 5. Run Payroll
### Mục đích:
Tính toán và phát lương cho nhân viên dựa trên dữ liệu bảng chấm công, doanh thu, và chế độ lương.

### Tác nhân tham gia:
- **Hệ thống:** Tự động thực hiện tính toán lương theo chu kỳ.

### Luồng chính:
1. Hệ thống lấy thông tin nhân viên từ cơ sở dữ liệu.
2. Đối với từng loại nhân viên:
   - **Salaried:** Lương cố định hàng tháng.
   - **Hourly:** Lương tính theo số giờ làm việc.
   - **Commission:** Lương cố định cộng thêm phần trăm doanh thu.
3. Tính tổng lương và lưu kết quả vào lịch sử trả lương.
4. Gửi thông báo lương cho nhân viên.

### Kết quả mong đợi:
Lương được tính chính xác và phân phối cho nhân viên.
