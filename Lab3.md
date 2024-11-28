# 1. Subsystem Context Diagrams

## 1.1. Biểu đồ ngữ cảnh của **BankSystem**

### Biểu đồ:
![Diagram](https://www.planttext.com/api/plantuml/png/h5AnJiCm4Dtz5QTse4X4tQiega0CaJfKT68qpfLOTUp8vm0Hy6KCV1A_W9t4eKbN9f_VtNltxkoVhs-s9SUjQoh5hk3EQ6UDOa9n8bZiUUjlQa0LsWLmWWiKqbJqboo3TmQmNeDjDDHzuUgQVJ8ldck7ziW5CXaZo6-vFXrQSbXvbR5Yq2cmDYJTYlkMeaHnWWt4y0QyYWbq3uOZrqTZA-waqKF3G_D4lVJUchSsJlNNiXjdue16IXqetiTo9vzBzuXAcTV_C7MldNJHooYHfjZXMJPaPkJ0V43LnLJAcjZbAoH9Djdd1WffKRZecA3hHV0YEPii_YD9pjR0pb91CvgSutEBMzH5-4Ri5m00__y30000)

### Giải thích:
Hệ thống **BankSystem** chịu trách nhiệm quản lý việc chuyển tiền vào tài khoản ngân hàng. Biểu đồ mô tả các thành phần tương tác với hệ thống con này:
- **PayrollController (Control)**:
  - Lớp điều khiển chịu trách nhiệm quản lý quy trình lương.
  - Tương tác với dịch vụ ngân hàng thông qua interface `IBankSystem` để thực hiện chuyển tiền vào tài khoản.
- **IBankSystem (Interface)**:
  - Định nghĩa phương thức `deposit(aPaycheck : Paycheck, intoBank : BankInformation)` để chuyển tiền vào tài khoản ngân hàng.
- **BankSystem (Subsystem Proxy)**:
  - Là lớp thực hiện phương thức `deposit` và thực hiện việc chuyển tiền vào tài khoản ngân hàng dựa trên thông tin từ `Paycheck` và `BankInformation`.
- **Paycheck (Entity)**:
  - Thực thể chứa thông tin về phiếu lương cần chuyển.
- **BankInformation**:
  - Thực thể chứa thông tin về tài khoản ngân hàng cần chuyển tiền vào.

---

## 1.2. Biểu đồ ngữ cảnh của **PrintService**

### Biểu đồ:
![Diagram](https://www.planttext.com/api/plantuml/png/f5AnJWCn3Dtp5LOxK2HEtQleL0anL6AeseanN0sDb2PHx2kSW2zZu9Fu1P8cT-9QDZRxsS_lsSdtvzUIM0Lk3qPSmQsp79mHZL54C5chBcQce0R311J11GfIDZcfQtWJ0FCvXDQ2puspQ_4Xul2LPGnFga6X-mXMwn2JBOQZZfcKGq-Pv5Cv2fBHVgPA00ieqGquUveGJKGmHqLkspvIHuo7YBlNRjZfbs1UP-o01ffFjEXZUg-Vz_o0nhYN_vgwiwovzz8pfSGJNDTz8NCIOOD6iNQMzjgJk3nzLTLdHrp0JWTiEDkaz0f9XU2ebJYxztjLZVONetAQNJp-KIWUbsXtyVFy0000__y30000)

### Giải thích:
Hệ thống con **PrintService** chịu trách nhiệm in bảng lương. Các thành phần chính của biểu đồ:
- **PayrollController (Control)**:
  - Lớp điều khiển quản lý quy trình lương và gửi yêu cầu in bảng lương thông qua interface `IPrintService`.
- **IPrintService (Interface)**:
  - Định nghĩa phương thức `printPayslip(aPayslip : Payslip, onPrinter : Printer)` để in bảng lương.
  - Đóng vai trò là cầu nối giữa `PayrollController` và `PrintService`.
- **PrintService (Subsystem Proxy)**:
  - Là lớp triển khai thực tế của `IPrintService`, thực hiện các tác vụ in ấn bảng lương và tương tác với các thực thể `Payslip` và `Printer`.
- **Payslip (Entity)**:
  - Thực thể chứa thông tin bảng lương cần in.
- **Printer**:
  - Thiết bị máy in được sử dụng để in bảng lương.

---

## 1.3. Biểu đồ ngữ cảnh của **ProjectManagementDatabase**

### Biểu đồ:
![Diagram](https://www.planttext.com/api/plantuml/png/f5AnJiCm4Dtz5QSoq0vHzogAAW539H2ecHWloJKnSfnWNreYuCiO-2H-0JjrAweICR3v_9xllRldhu_FfMKqtDLANC9LezaqIkGAhON9WscUAESxr5YI2Q0YCm6qC0P27EVx8adWLG3Cvr0F96ZtJ-nq9jw5arjf9hF1d8Gyd61rZOmfcQrqHHmVAQ7PXZYlF6Nwt97fOG4f6wdBcSEwja2c0JIKDwPmw7tc5ODUscMsjqorD__I_pfcJPfzYmmjdS_v4tNkxB5XwniwZnUtigpuaPHgTlytVADPyi5dCE9aQRXEaW2iXxUUloQ5B1jjAzbQCPfG52MdUrx0402wR60dkGBd2s4hKPp6yHP5u_iGuvloWW7zWnLcMP8k_9Vy1W00__y30000)

### Giải thích:
Hệ thống con **ProjectManagementDatabase** chịu trách nhiệm quản lý dữ liệu dự án. Các thành phần trong biểu đồ:
- **ProjectManagerController (Control)**:
  - Lớp điều khiển quản lý các thao tác với dự án, tương tác với hệ thống cơ sở dữ liệu qua interface `IDataService`.
- **IDataService (Interface)**:
  - Định nghĩa hai phương thức:
    - `fetchData(query : String)`: Lấy dữ liệu từ cơ sở dữ liệu.
    - `updateData(record : Object)`: Cập nhật dữ liệu vào cơ sở dữ liệu.
  - Đóng vai trò là cầu nối giữa `ProjectManagerController` và `ProjectManagementDatabase`.
- **ProjectManagementDatabase (Subsystem Proxy)**:
  - Lớp thực hiện các tác vụ lấy và cập nhật dữ liệu trong cơ sở dữ liệu về dự án thông qua phương thức `fetchData` và `updateData`.
  - Tương tác với các thực thể `Project` và `Record` để lưu trữ thông tin.
- **Project (Entity)**:
  - Thực thể đại diện cho các dự án được quản lý trong cơ sở dữ liệu.
- **Record**:
  - Thực thể đại diện cho các bản ghi dữ liệu phụ trợ trong cơ sở dữ liệu của dự án.

---
# 2. Analysis Class to Design Element Map

## Ánh xạ các lớp phân tích đến các phần tử thiết kế

### 2.1. **PrintService**

| **Analysis Class**     | **Design Element**     |
|------------------------|------------------------|
| PrintServiceController | PrintServiceController |
| PrintJob               | PrintJob               |
| Payslip                | Payslip                |
| PrinterInterface       | PrinterInterface       |

### 2.2. **ProjectManagementDatabase**

| **Analysis Class**     | **Design Element**     |
|------------------------|------------------------|
| ProjectManager         | ProjectManager         |
| ProjectData            | ProjectData            |
| DataService            | DataService            |
| DatabaseConnection     | DatabaseConnection     |
| ProjectRecord          | ProjectRecord          |

---
# 3. Design Element to Owning Package Map

## Ánh xạ các phần tử thiết kế vào các gói

### PrintService

| **Design Element**       | **Owning Package**       |
|---------------------------|--------------------------|
| PrintServiceController    | print.controller         |
| PrintJob                  | print.entity             |
| Payslip                   | print.entity             |
| PrinterInterface          | print.interfaces         |
| PrintService              | print.subsystem          |

### ProjectManagementDatabase

| **Design Element**       | **Owning Package**           |
|---------------------------|------------------------------|
| ProjectManager            | project.controller           |
| ProjectData               | project.entity               |
| ProjectRecord             | project.entity               |
| DataService               | project.interfaces           |
| DatabaseConnection        | project.subsystem.database   |

---
# 4. Architectural layers and their dependencies

## Biểu đồ mô tả các layers trong hệ thống và quan hệ giữa chúng 

![Diagram](https://www.planttext.com/api/plantuml/png/X99DJiCm48NtFiMecwvw0HQebB8e0WcH4qoSAJLrxCWpeOeG9sF1aRW2JbJdfmInikBt_7dyNhu_lzOi6AGkhLh2blR64LXiAB2gK1_nXM1nKrNMQ1JZ7JoqsWBU5O2so0nFs0HlxQrtqguK1YNuLzBoY2vImiZmeGRsfkPuPNHd5DwC9fwmWt5o5kQn9JdPec2EJ1FkdHCZvWA73LjJJV7tFhz4zz_Ff7qe9joT4mfxd1kKGY_smcw3xfWrB5GEU-t0wLLZTbRdt5d7w1d0E9P_SszlMCQNsAu_FfYA8ISv4RbKzAZVhbvO5VxaLjUGoadTm1KKL94h6BnJlzHqB6KVxJKJ_sqSmepMBa7Kmd0oSb0z99dxTA9N-xAiNJipdUqZrEm1j9RLEexU_ka_0000__y30000)
