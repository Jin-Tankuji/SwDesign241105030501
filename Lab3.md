# 1. Subsystem context diagrams:
## BankSystem
     - PayrollController (Control): Lớp thực hiện quy trình bảng lương bằng phương thức run payroll().
     - IBankSystem (Interface): Giao diện định nghĩa phương thức deposit(aPaycheck : Paycheck, intoBack : BankInformation) để chuyển tiền trực tiếp vào ngân hàng.
     - BankSystem (Subsystem Proxy): Hệ thống con thực hiện giao dịch ngân hàng, triển khai phương thức deposit từ IBankSystem để gửi tiền vào tài khoản nhân viên.
     - Paycheck (Entity): Chứa thông tin thanh toán.
     - BankInformation (Entity):  
