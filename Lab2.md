1. Phân tích ca sử dụng Create Payment:
Các lớp phân tích:
-  Employee: Đại diện cho nhân viên.
    +  Thuộc tính: employeeID, name, address, employeeType, paymentMethod.
    +  Nhiệm vụ: Định nghĩa thông tin nhân viên và phương thức thanh toán.
-  Timecard: Đại diện cho thẻ chấm công.
    +  Thuộc tính: timecardID, date, hoursWorked, chargeNumber.
    +  Nhiệm vụ: Cung cấp thông tin về số giờ làm việc của 1 nhân viên.
-  PaymentMethod: Đại diện cho phương thức thanh toán.
    +  Thuộc tính: methodType (PostOffice, Banking, At Work).
    +  Nhiệm vụ: Cung cấp các phương thức thanh toán.

Biểu đồ lớp:    
![Class - Create Employee](https://www.planttext.com/api/plantuml/png/P95DJiCm48NtESKeQwBkiogqIB0eL6ebraCyQQpw9_8uYmXnCXOSYIim1jSYnGlByzb-yvxzzV6vveWXJjPKLMUG6UxjQFnC16yLo6X0gnOECMXtoi2XfIk4IWLYlgAKfOxpM2u0h5PGF_WfcBc-WVg01eCcbTORRwrcrjv9dJL6d2svkACuU36o_rjMxnVJHsrfWq4Lqr509-1nsu9sCLE5KOniPSvW41_yuiEPHBit7Yydkm73YPuc-qgX1VvDLTejN9IUzgVy7tRlES9pt-kEKiexT6VPIylR2AbvdPJBkpTDYRE0o-ZLcfnAt_OD003__mC0)

Biểu đồ tuần tự:    
![Sequence - Create Employee](https://www.planttext.com/api/plantuml/png/P95DJiCm48NtESKeQwBkiogqIB0eL6ebraCyQQpw9_8uYmXnCXOSYIim1jSYnGlByzb-yvxzzV6vveWXJjPKLMUG6UxjQFnC16yLo6X0gnOECMXtoi2XfIk4IWLYlgAKfOxpM2u0h5PGF_WfcBc-WVg01eCcbTORRwrcrjv9dJL6d2svkACuU36o_rjMxnVJHsrfWq4Lqr509-1nsu9sCLE5KOniPSvW41_yuiEPHBit7Yydkm73YPuc-qgX1VvDLTejN9IUzgVy7tRlES9pt-kEKiexT6VPIylR2AbvdPJBkpTDYRE0o-ZLcfnAt_OD003__mC0)

2. Phân tích ca sử dụng Maintain Purchase Order:
Các lớp phân tích:
