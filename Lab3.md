# Identify design elements
## 1. Subsystem context diagrams
BankSystem:  
- PayrollController: Lớp thực hiện quy trình bảng lương bằng phương thức run payroll().
- IBankSystem: Giao diện định nghĩa phương thức deposit(aPaycheck : Paycheck, intoBack : BankInformation) để chuyển tiền trực tiếp vào ngân hàng.
- BankSystem: Hệ thống con thực hiện giao dịch ngân hàng, triển khai phương thức deposit từ IBankSystem để gửi tiền vào tài khoản nhân viên.
- Paycheck: Chứa thông tin thanh toán.
- BankInformation: Thông tin tài khoản ngân hàng của nhân viên, xác định nơi gửi tiền.

PrintService:  
- PrintController: Điều phối quá trình in.
- IPrintService: Giao diện định nghĩa phương thức print.
- PrintServiceProxy: Triển khai IPrintService, thực hiện in ấn.
- Document và PrintSettings: Thực thể chứa nội dung tài liệu và cài đặt in.
- PrinterBoundary: Lớp biên xử lý giao tiếp với máy in vật lý.
![SubSystem - PrintService](https://www.planttext.com/api/plantuml/png/h5DBJiCm4Dtx5DvH9De3H0XLK1PT82721OmpJImvTh37GFYSZ0L7uWfC4YTf4w4k88l8djzxRsRy_VcrzYWSXb8pTi8ti5C6E1R0hwn1PxK6nwKMthFsps-TChZdUsEy-Hmy1l3OUXUPbQ44WppXctWyunuGbSaz6TkeDDvFsSS4UMiGt4v8OAe_yMtCSK-ARX6q-W-qD3pusYEK56XVwauiLsMbeIb5IMtOG6M_3v5Fb_X7KeSApzzNgpd6XFerqSF86Fe1zN0z7qcpweYaIFNopag96aORuH_8YZnxIIA7LBt2f8QqsheRcytjbO9699MQjVlI1fC9Ly-N2jpWYxWUJ7PletEH2HG3KfpZ7MY1oXfVgCgpwMukbnUJnKbuQ3er7ruJEcMHa9Ao34P9WQJdMM7nI-PcdFQn-kcu0sqeMvF8vlNz0000__y30000)
