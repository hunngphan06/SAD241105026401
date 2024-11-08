# MÔ TẢ VỀ BIỂU ĐỒ CỦA TÔI
## 1.BIỂU ĐỒ VỀ SÁCH 
-Biểu đồ gồm những lớp sau :
<br>

![Diagram](https://www.planttext.com/api/plantuml/png/ZDB13O8m50RWUwTuDo611JWH4suUD0v06YdGK5j27oPgF3k48xY179Y52Lp1YXYA5-oXQL_-b_UbwRDfGusqmdel25d0gcjk9IoLAiXEKAtx8vm9cEK3SXGiW2rMN6P3ZTQOgsfIXBxBcQIzdw0x91EkIq6FCPUfSjm03eedv39IeXvGT8yMCE-QEmKqkosC9iIK2nPhVZA3kSHXI3JlyNuw__MjJJEoP5PfvxxMacPCsquhDASTU-UbcvfACAohBIGzHVd-vtN6guKW96GoUN-D5m000F__0m00)

-Lớp Employee: Lớp cơ sở với các thuộc tính chung như ID, tên và lương.<br>
-Lớp FullTimeEmployee và PartTimeEmployee: Kế thừa từ Employee, thêm thuộc tính weekly_hours.<br>
-Mối quan hệ kế thừa: FullTimeEmployee và PartTimeEmployee kế thừa từ Employee.<br>
-Phương thức display_info(): Hiển thị thông tin nhân viên trong cả ba lớp.

## 2.BIỂU ĐỒ VỀ NHÂN VIÊN
-Biểu đồ gồm những lớp sau :
<br>

![Diagram](https://www.planttext.com/api/plantuml/png/l9AnRSCm44Nxc-8wsu2qW2etIPKYWTCB1-ji4pgH0aab40BN6I8ZP0Ehy2oQ82jOHXGv4el4ZLaGu2V_ntyalvhZqdcolYe4mELAepME0MRuq3OV9TuLfPYQ6TP2pWrBV0FiHepS2wdA4bJQzxAcWXDSUQlqjfSS2TawmOqO-Zw6Gzny6XED4gAnUT6xC-LAeJfLUcFcYmHVZCfWV-b-NuayguA7qdbxEABVjSqdeU_cALrW-A5yPSwbJdUcikw2YO7XEeuepFqlscFtP5UX1OQ_qAQ66w0zLQInGtZ_JGD3OnF7mOMFTwUT0PQii_FNFW400F__0m00)

-Lớp Book: Lớp cơ sở với các thuộc tính title và author, cùng phương thức display_info().<br>
-Lớp EBook: Kế thừa từ Book, thêm thuộc tính file_size.<br>
-Lớp PrintedBook: Kế thừa từ Book, thêm thuộc tính pages.<br>
-Quan hệ kế thừa: EBook và PrintedBook kế thừa từ Book.
