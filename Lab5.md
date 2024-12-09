# Thiết kế các hệ thống con trong hệ thống Payroll System

Dựa trên tài liệu bài Lab4 về thiết kế ca sử dụng, các hệ thống con của Payroll System được chia thành các thành phần chính như sau:

## 1. Subsystem: User Management
- **Ca sử dụng liên quan:**
  - Đăng nhập vào hệ thống (Login).
  - Cập nhật thông tin cá nhân (Update Personal Information).
- **Chức năng chính:**
  - Quản lý tài khoản người dùng (nhân viên, quản lý).
  - Xác thực thông tin đăng nhập và phân quyền người dùng.
  - Hỗ trợ nhân viên cập nhật thông tin cá nhân.
- **Các module:**
  - Module xác thực (Authentication Module).
  - Module quản lý hồ sơ (Profile Management Module).

---

## 2. Subsystem: Payroll Processing
- **Ca sử dụng liên quan:**
  - Tính toán lương (Calculate Payroll).
  - Quản lý bảng lương (Manage Payroll Records).
- **Chức năng chính:**
  - Xử lý các dữ liệu liên quan đến tính lương: giờ làm việc, phụ cấp, khấu trừ.
  - Tự động tính toán lương và lưu trữ kết quả.
  - Cho phép quản lý tạo, sửa, xóa các bảng lương.
- **Các module:**
  - Module xử lý lương (Payroll Calculation Engine).
  - Module quản lý bảng lương (Payroll Records Management).

---

## 3. Subsystem: Timecard Management
- **Ca sử dụng liên quan:**
  - Cập nhật thông tin chấm công (Maintain Timecard).
- **Chức năng chính:**
  - Quản lý thời gian làm việc của nhân viên.
  - Hỗ trợ ghi nhận giờ làm việc, nghỉ phép, và cập nhật thông tin này vào hệ thống.
- **Các module:**
  - Module giao diện chấm công (Timecard UI Module).
  - Module xử lý dữ liệu chấm công (Timecard Data Handler).

---

## 4. Subsystem: Reporting
- **Ca sử dụng liên quan:**
  - Tạo báo cáo lương (Generate Payroll Reports).
- **Chức năng chính:**
  - Cung cấp khả năng tạo báo cáo tùy chỉnh theo các tiêu chí như thời gian, phòng ban.
  - Xuất báo cáo ra các định dạng phổ biến như PDF, Excel.
- **Các module:**
  - Module tạo báo cáo (Report Generator).
  - Module định dạng báo cáo (Report Formatter).

---

## 5. Subsystem: Security
- **Ca sử dụng liên quan:**
  - Xác thực thông tin đăng nhập.
  - Bảo vệ dữ liệu khi xử lý và lưu trữ.
- **Chức năng chính:**
  - Đảm bảo tính bảo mật và an toàn cho hệ thống.
  - Hỗ trợ xác thực người dùng và phân quyền truy cập theo vai trò.
- **Các module:**
  - Module phân quyền (Role-Based Access Control - RBAC).
  - Module mã hóa dữ liệu (Encryption Module).

---

## 6. Subsystem: Data Management
- **Ca sử dụng liên quan:**
  - Lưu trữ thông tin lương, nhân viên, và thời gian làm việc.
- **Chức năng chính:**
  - Quản lý cơ sở dữ liệu để lưu trữ và truy xuất thông tin.
  - Đảm bảo tính nhất quán và hiệu năng của dữ liệu.
- **Các module:**
  - Module quản lý cơ sở dữ liệu (Database Management Module).
  - Module đồng bộ hóa dữ liệu (Data Synchronization Module).

---

## Tương tác giữa các hệ thống con
- **Đăng nhập**: Xác thực thông qua Subsystem **User Management**, kiểm tra quyền thông qua Subsystem **Security**.
- **Quản lý chấm công và tính lương**: Dữ liệu từ Subsystem **Timecard Management** được xử lý bởi Subsystem **Payroll Processing**.
- **Báo cáo**: Subsystem **Reporting** truy xuất dữ liệu từ **Data Management** và **Payroll Processing** để tạo báo cáo.
- **Bảo mật**: Tất cả các tương tác đều đi qua Subsystem **Security** để đảm bảo quyền truy cập hợp lệ.

---

## Ưu điểm của thiết kế này
- **Dễ bảo trì:** Các chức năng được phân tách rõ ràng, giúp dễ dàng nâng cấp hoặc sửa lỗi.
- **Khả năng mở rộng:** Có thể bổ sung các chức năng mới mà không ảnh hưởng đến các hệ thống con khác.
- **Hiệu quả:** Hệ thống xử lý theo luồng công việc, tối ưu hóa hiệu năng và quản lý dữ liệu.

---

## Mô hình giao tiếp giữa các hệ thống con

![alt](https://www.planttext.com/api/plantuml/png/X5JBJiCm4BpdArQvymCz811GoW6fQYdthRDjBVm8wmrIG7mP1pw9Ny1kaof0N7BqpkwCPyVv-lYy288iZJL5ZUe9jmJb75lsni2o3KAsXBS2ugUyhRqZ9r2k0Z7Seuje6mzwHFgq4-8DAkfGbutioh7gdFr66u9LNQ7G0V9U_6PQacfOIvkXk5IAGe0hxoGgpWrvq9OKSlM_v2FopjMDZEe-GgvH46ReAaESO-wTZ9TDGhNRPeXxu1KQrHWKxTsuQnrkGSfp5OOtoaXOKErPyio7EjoI8yxpTgYfPukodvQXsxlohyy9jSP0S5ZWAEL-qh9rQiVUwTU1jlSYyluDuTdP-J0manYF6BvOqYecx4YLQHnRrIHT_BcX8D2NawhiZ87NWzR3QMGknfDuYdxPhAqM-16wyjISF_wd8UAPO93jZKzYnYYpCnOahEc5uCRMnhT4lPJib1-RU4IZqpk7ER7L4URTtf21OwTiwDxvSGaag4tQvU_-CUbJ4hM3cGxHXXY5VeV5G66szyOfRclfMYx8LUbF-Gq00F__0m00)
