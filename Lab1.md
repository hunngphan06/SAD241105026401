# Phân tích kiến trúc, cơ chế, ca sử dụng hệ thống Payroll System

## 1. Phân tích kiến trúc

### Đề xuất kiến trúc
Kiến trúc đề xuất: **Client-Server Architecture** với các thành phần:
1. **Client Layer**: Giao diện người dùng để nhân viên và quản trị viên thao tác.
2. **Application Server**: Chứa logic nghiệp vụ xử lý yêu cầu từ Client.
3. **Database Server**: Lưu trữ dữ liệu nhân viên, timecard và các giao dịch.

### Biểu đồ Package
![Diagram](https://www.planttext.com/api/plantuml/png/R94v3W8n34NxdCAYvm8K2CHIWSHs0PEnK4Gsd0nIX3WP1KVY2eHX7MQwwCLv_dPkb-iWHEHO6YqyoZtk23eZhSX6c64Yxi1904YD8S3CxPITEZOVii1aSccDRPGXYLnKy2o-sg7tMacCobbO4n_hyfTgmKvI28uRlZdQhFdoDScILKp_V8mHjnXeMA2FcVz6UD-rz9yOhrqYsk1MKwDvdRwoFc7s_ssis-stJzlB9rl0YWubXHX4Qr7rkX6q1ykIE5NJYK6sF7xi3W00__y30000)

---

## 2. Cơ chế phân tích

### Danh sách cơ chế cần giải quyết
1. **Persistency**: Lưu trữ dữ liệu qua JDBC.
2. **Security**: Kiểm soát quyền truy cập.
3. **Concurrency**: Đảm bảo đồng thời nhiều người dùng.
4. **Validation**: Kiểm tra dữ liệu đầu vào hợp lệ.
5. **Error Handling**: Xử lý lỗi khi hệ thống phụ trợ không khả dụng.

---

## 3. Phân tích ca sử dụng "Select Payment Method"

### Mô tả Use Case
- Nhân viên chọn phương thức thanh toán: nhận trực tiếp, qua bưu điện, hoặc chuyển khoản.

### Biểu đồ Sequence
![Diagram](https://www.planttext.com/api/plantuml/png/T99DRiCW48Ntd88Bv09PLB6QBYD5oiz-0fCK5GF2urRkrRBeaNg5GXrG0NU7u7syzmQ-xr-RWS3Js6i6WgpdBxtJTa9aBcmheHmOudkOUZIqzrRWC5XV71vGZ5xHj0C3D_HC0i451kJRnw9GfyrEWgEWPicGhvuQ7xuEjsiKEG7V8RrQoHfXWAiSWJsZLzSfL-BT662lFe6KDQpMXojIkCY2Lg49_g55z69Pirhqd5KPbwtDSiyY6t-svgfyZyjDgnd6AS4xrZEgLMM_a_jjbvWZN3IMtLgN1zE9DsC_DCfRH5kVVnuoHZoCyn3RLW7Aarwd_lD3RT38-47P3m000F__0m00)

### Biểu đồ Lớp
![Diagram](https://www.planttext.com/api/plantuml/png/R95D3e8m48NtFSKiTS45N1X9SE62X8GJZ6N49gKbxM3I64_cmYDv1OFyYC1oEjzxVQzzFry7p-YugRIG6hs7OrLh6uZWBW0YK0Ni86UdJFcT3LRqVr9ZgCXmIdor4_WXUiEissVEIlBUkgynW2TDahEfUBFzgNAIZLCSKZHOqY2waLEN4ClMQKedo7X6Jt61DO-qnnlr5oJ4gFIgfeURka0Uy9Evs8uTdoEAzeigOj6jfMRHrw5POZ5lC6N4WKpH_f3u0000__y30000)

---

# 4. Phân tích ca sử dụng "Maintain Timecard"

## Mô tả Use Case
- **Mục đích**: Nhân viên thêm, sửa hoặc xóa thông tin timecard.
- **Diễn biến chính**:
  1. Nhân viên đăng nhập và chọn chức năng **"Maintain Timecard"**.
  2. Hệ thống xác minh quyền truy cập.
  3. Nhân viên nhập thông tin về giờ làm việc cho các ngày trong tuần và các dự án.
  4. Hệ thống kiểm tra tính hợp lệ và xung đột của thông tin, sau đó lưu vào cơ sở dữ liệu.

---

## Biểu đồ Sequence - Maintain Timecard
![Diagram](https://www.planttext.com/api/plantuml/png/T991JiCm44NtFiMe-ufz5wXf0wo2a1AodzeJQf74aUqWbQknu4XSWN4IkoaIsvd___iU-UVhU-yyMZzshK3fZOM7RcZDXKWCFDPI3zXxs5Iw8ubMGO4zlf7T03geYbjHINAqsbzkH6NnJrADhLR8o3chlfNbwF64ZY1JEFWbAy-4YlEac3S78M9psDvpDTYnLTsz3kmWY5J12rwNOLsJrSqbFHYoqP-DrP_ejUb5EGdpGn3EJLaX9Ja7BsGxxHohd631DWQkvicZfg3KQ8s09yjFfTYfgjUeQ-4wzJYUIRx3qVHDgwLFxCduRD827itOpyR8NM83j1odHpHZkt3pZ0KbVgoOF8hCF_U32ayjHVBLkaeDviYTTg6Njjryrcg-HZhwxXeTn4higLVXDufV0000__y30000)

## Biểu đồ Lớp - Maintain Timecard
![Diagram](https://www.planttext.com/api/plantuml/png/R991Ri8m44NtFiKioo8Ng2e4WkvW5SH-i0TgrNOYpmGfGfoCHO_KAxG9IPguMSxtqn__h_b-VArOC4hbdT8EcU7TbwweYU2c03Am1buXbsZ3fPq3UfegOZrfZ8P_vPrbUJjqmbBTLMVQItiCUA7OUWFuTkhVNXP_V4wwYbRgAN-bQC_rMcjY7jEzmn6TDIZ5m3_dyOP6rX-aFpT5E3khPMAqHS4JCgqDbZAiPRpEVhAdEwmgnxiEU7Bqf8T6isoPDg7IPXecIJ_B_CiyIoM1L1fmpAWL1TFSWVe1003__mC0)

---

# 5. Hợp nhất kết quả phân tích

## Tổng kết
- **Các lớp được tái sử dụng**: Các lớp như `SecurityManager`, `DatabaseAdapter`, và `Database` được tái sử dụng để giảm độ phức tạp và đơn giản hóa hệ thống.
- **Khả năng mở rộng**: Hệ thống đảm bảo khả năng mở rộng và dễ bảo trì nhờ vào sự phân chia rõ ràng giữa các thành phần.
- **Tính bảo trì**: Kiến trúc phân tách các lớp một cách hợp lý, giúp việc bảo trì và nâng cấp hệ thống trở nên dễ dàng hơn.

---

## Kết luận
- Biểu đồ **Sequence** và **Lớp** đã được sử dụng để mô tả hành vi và cấu trúc của hệ thống trong các ca sử dụng "Select Payment Method" và "Maintain Timecard".
- Cấu trúc hệ thống cho phép dễ dàng duy trì và mở rộng khi cần thiết.
