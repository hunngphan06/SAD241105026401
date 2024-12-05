# Thiết kế các ca sử dụng cho hệ thống "Payroll System"

## **1. Login**
### **Mô tả thiết kế**
- **Thành phần:**
  - **LoginForm**: Biểu mẫu cho phép người dùng nhập tên đăng nhập và mật khẩu.
  - **SystemClockInterface**: Đồng bộ hóa thông tin thời gian cho phiên làm việc.
  - **PayrollController**: Xử lý logic xác thực thông tin đăng nhập.
- **Mô tả quy trình:**
  1. Người dùng mở **LoginForm** để nhập thông tin tên đăng nhập và mật khẩu.
  2. **PayrollController** nhận thông tin, kiểm tra tính hợp lệ qua cơ chế xác thực.
  3. Nếu xác thực thành công, quyền truy cập được cấp, đồng thời đồng bộ thời gian qua **SystemClockInterface**.

### **Sơ đồ UML**
![Diagram](https://www.planttext.com/api/plantuml/png/R50x2W913Etd5C7U2rY8i2W85iAYVNOswk1C0fbiiLxDmYDv1NSGVxXLFk-JH-xNso8RgdKfElGc2fDT9fq0PYYDQwJZ5hM7ZHm3hqIJyyAc4c6B_L1YzHpZG0vif0Vq17MVZL8LnP_NhwLpnH6cyu_N39O51Q_K4bl0cDqRBCo_6pEekoO5-v7yiOfqBCAWxjcVL3XS22ma6jT-1TnZ32rQ40Qbt4Lp2-As_Ei1003__mC0)

---

## **2. Maintain Timecard**
### **Mô tả thiết kế**
- **Thành phần:**
  - **TimecardForm**: Giao diện để nhân viên nhập giờ làm việc.
  - **TimecardController**: Xử lý logic liên quan đến thẻ chấm công.
  - **ProjectManagementDatabase**: Truy xuất mã dự án từ cơ sở dữ liệu quản lý dự án.
- **Mô tả quy trình:**
  1. Nhân viên mở **TimecardForm** và nhập các thông tin giờ làm việc, mã dự án.
  2. **TimecardController** gửi yêu cầu truy vấn danh sách mã dự án từ **ProjectManagementDatabase**.
  3. Nhân viên điều chỉnh hoặc lưu thông tin mới qua **TimecardController**.
  4. Thẻ chấm công được cập nhật trong cơ sở dữ liệu.

### **Sơ đồ UML**
![Diagram](https://www.planttext.com/api/plantuml/png/T9593i8m34NtFeN5lXVe0Y4nx128uG0ciHZKn9NZ8d4s5Xo9Ar260XLq5VdRVlydkPulWsIaLeK2o9aeziQXBEJ4t4DAs1ImaIfwqXEkze4TgP-81d0IJQLuYyDdNR229wCD9SQvoe6TJIdIbWD76xqw00qTitwBc-EivFYMyE7rFV2zyF7CSHoD5NTIQKAA7ikdTuBVuJkYCrgE2pRTyv7HxKYtzI6U4tGkODQHQCbrZ1RZVvJszTTb_NoCzX9XK5FkNmGt0000__y30000)

---

## **3. Run Payroll**
### **Mô tả thiết kế**
- **Thành phần:**
  - **PayrollController**: Điều phối toàn bộ quy trình tính toán và xử lý bảng lương.
  - **SystemClockInterface**: Kiểm tra ngày trả lương.
  - **BankSystem**: Xử lý các giao dịch chuyển khoản lương.
  - **PrintService**: In bảng lương.
  - **Paycheck**: Thực thể đại diện cho thông tin lương của từng nhân viên.
- **Mô tả quy trình:**
  1. **PayrollController** kiểm tra xem ngày trả lương có hợp lệ không thông qua **SystemClockInterface**.
  2. Tiến hành tính toán lương dựa trên dữ liệu từ **Timecard** và loại nhân viên (nhân viên theo giờ, cố định, hoa hồng).
  3. Gửi thông tin lương qua **BankSystem** để thực hiện giao dịch.
  4. Sử dụng **PrintService** để in bảng lương cho nhân viên.

### **Sơ đồ UML**
![Diagram](https://www.planttext.com/api/plantuml/png/T551Zi8m3Bpx5HPtFj332kXfRsZx0czgHDJKMJdkIdaR1vx45qWe5IlHlSKp7i_OkLskksIaDeq1o5bKt1mfQmm1z_tePOEKvXUuA5O8VFBjN0PMy6Ai9tACNKx6OnkY6puN45ZCMwuwTsOtm7USf2VDU20PPiKBEsgPrh7--gA4XpDkFzvD6_oQP87XZQwQjJ0DjZK3_b3kAQ_hbg2bbuAR0XbZeb3IhVU_rcYmO-dHb2ILQ_eewH-BFrisSrKZFMmJxCgG-Y5m1m00__y30000)

---

# **Lý do thiết kế chung**

1. **Phân tách rõ ràng trách nhiệm**:
   - Các thành phần được chia thành lớp **Boundary**, **Control**, và **Entity**, giúp tăng tính rõ ràng và dễ bảo trì.
   - **Boundary** xử lý giao diện người dùng.
   - **Control** quản lý logic nghiệp vụ.
   - **Entity** lưu trữ dữ liệu và thực thể nghiệp vụ.

2. **Tính linh hoạt và mở rộng**:
   - Các thành phần như **BankSystem**, **PrintService**, và **ProjectManagementDatabase** được tích hợp qua giao diện (**Interface**) để dễ thay đổi hoặc mở rộng.

3. **Tăng tính bảo trì**:
   - Quy trình thiết kế tập trung vào việc giảm phụ thuộc giữa các lớp. Mỗi lớp đảm nhiệm một nhiệm vụ cụ thể.

4. **Tương thích với hệ thống bên ngoài**:
   - Hệ thống được thiết kế sẵn sàng tích hợp với ngân hàng, dịch vụ in, và cơ sở dữ liệu cũ.

5. **Hiệu quả hoạt động**:
   - Các lớp như **PayrollController** tối ưu hóa quy trình, đảm bảo xử lý chính xác và hiệu quả toàn bộ vòng đời xử lý bảng lương.
