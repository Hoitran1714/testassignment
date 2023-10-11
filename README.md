# GIỚI THIỆU HÀM CALCULATE TRONG POWER BI
## 1. Hàm calculate là gì?
CALCULATE là 1 trong những hàm thông dụng và quan trọng nhất trong Power BI, cho phép người dùng tính toán những metric cần thiết. Khác với việc chỉ sử dụng những hàm tính toán thông thường, việc sử dụng hàm CALCULATE cho phép người dùng đặt bộ lọc ngay trong biểu thức tính toán.
Trong thực tế, có thể ứng dụng hàm CALCULATE để tính toán metric 
## 2. Cấu trúc của hàm calculate.
Hàm CALCULATE có cấu trúc như sau:

`CALCULATE(<expression>[, <filter1> [, <filter2> [, …]]])`

Ta có thể thấy, bên trong câu lệnh CALCULATE có 2 thành phần chính:

* `<expression>`: Đây là các hàm tính toán thông dụng như Sum, Count, Average, nhằm chỉ định giá trị tính toán
* `[, <filter1> [, <filter2> [, …]]]` : Đây là phần đặt điều kiện lọc cho biểu thức. Việc được đặt trong ngoặc vuông và được lặp đi lặp lại nhiều lần ở cấu trúc có ý nghĩa *filter* là trường không bắt buộc, và có thể xuất hiện được nhiều lần trong 1 hàm CALCULATE.
## 3. Ví dụ thực tế.
Lấy ví dụ trong Power BI có bảng Sales với data như sau
| Order ID | Order Date | Product | Quantity | Unit Price |
|----------|------------|---------|----------|------------|
| 1        | 01/01/2023 | A       | 1        | 100        |
| 2        | 02/01/2023 | B       | 4        | 125        |
| 3        | 03/01/2023 | C       | 4        | 120        |
| 4        | 01/01/2023 | A       | 5        | 100        |
| 5        | 04/01/2023 | C       | 7        | 120        |
| 6        | 02/01/2023 | B       | 5        | 125        |
| 7        | 03/01/2023 | A       | 6        | 100        |
| 8        | 03/01/2023 | C       | 8        | 120        |
| 9        | 04/01/2023 | A       | 4        | 100        |
| 10       | 02/01/2023 | B       | 1        | 125        |

* Ví dụ 1: Tính tổng doanh số bán hàng trong ngày 01/01/2023.

Sử dụng hàm CALCULATE:

`CALCULATE(SUMX(Sales,Sales[Quantity]*Sales[Unit Price]), Sales[Order Date] = DATE(2023,1,1))`

Trong đó `SUMX(Sales,Sales[Quantity]*Sales[Unit Price])` đóng vai trò tính toán doanh thu, `Sales[Order Date] = DATE(2023,1,1)` đóng vai trò đặt bộ lọc ngày bằng 01/01/2023

* Ví dụ 2: Tính số lượng order của sản phẩm A.

Sử dụng hàm CALCULATE

`CALCULATE(COUNT(Sales[Order ID]), Sales[Product] = "A")

Trong đó `COUNT(Sales[Order ID])` giữ vai trò đếm số lượng đơn hàng, `Sales[Product] = "A"` đóng vai trò đặt bộ lọc sản phẩm = A

End.

**Hội Trần**
