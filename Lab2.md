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
-  PurchaseOrder: Đại diện cho đơn hàng.
    +  Thuộc tính: orderID, supplier(nhà cung cấp), status, items(danh sách sản phẩm), totalAmount(tổng chi phí).
    +  Phương thức: createOrder(), updateOrder(), setStatus(), cancelOrder().
-  Product: Đại diện cho sản phẩm.
    +  Thuộc tính: productID, name, quantity, price.
    +  Phương thức: calculateTotal().
-  User: Đại diện cho nhân viên thưởng theo hoa hồng và quản lý.
    +  Thuộc tính: userID, name, role.
    +  Phương thức: approveOrder(): duyệt đơn, rejectOrder(): từ chối đơn.
   
Biểu đồ lớp:    
![Class - Maintain Purchase Order](https://www.planttext.com/api/plantuml/png/V9BFJiCm3CRlUGghfmsjshr2qv2u886OD7W0ateZA4rAx20Xn9Dnu95u1T8_wxPkMc-slxYVV_RVp--I1OF4oYgbBJB3AWRzYaoFeQG0NmhIbuDlehjRAC0uwNCSwzgQ92fWBS6uxIulA977MIDKDSbxmtAz2hwCMXPzJRoWlQbyT98KfOylbjeIW0w4qfcPdFnmThxhj7yRwt9uUr789ElMz6JaVIVGw3JPhjDKVG-ikZu3fRgBHvmSLZIcyHxHYP7F8s5qHbR1Q3g1W5P7csPvQa1DfllwOEMP3xOL-MHPvqm4R_SvWFaSidxxAKv0DfiiBHwo1tIufP3rRh1EStxqNDl3I4sEpcQ7BT0RQRaWd2K9idS7mDD4noTubUS3w0AqTuB6iMe7plF5w60Bg5gthDIINDaSzZy0003__mC0)

Biểu đồ tuần tự:  
![Sequence - Maintain Purchase Order](https://www.planttext.com/api/plantuml/png/X58zJiCm5DvzYgTCZLGkm82AAYO4L702otbD38bjx6Uad82P6u0OkZ8mDKE78kwH4t05d3X015NnO3zRtz-p_T5iPewu9L-LZ751si9SLvLqJcg5sKbbIbqZ0dSGSClbW3dZYkTek-CgbeoP82E5D5mH90jlHS4TNjWCRTBXT5Snrgl0mL7Smo48YvmYRkAyCQL4EmL9MBaftFgW9gcUWh5IOCeYQqHtI5V4oRj9ia2LIPKdwGuNRx9lbr_Q0JxqC2PmOwo-6nZxVOyZDEkCUKbmtgut7juUtfyK5Dj7bSDDiNqDIpXwQPjd0Pcls-QU68InmzlYDGgArk5sd5Pf3zqNuhBdz272DSGWfuK4qQvN8KRRhEfnf5xlxrjm9R3ywla_otcFBdyyPs7kFj8d0000__y30000)

3. Phân tích ca sử dụng Login:    
Các lớp phân tích:    
-  User: Đại diện cho người dùng.
    +  Thuộc tính: userID, username, password.
    +  Phương thức: Login(), Logout().
-  AuthenticationSystem: Đại diện hệ thống xác thực thông tin và bảo mật mật khẩu.
    +  Phương thức: validate(), hashPassword().
-  Dashboard: Hiển thị thông tin chào mừng hoặc nội dung chính cho người dùng đã đăng nhập thành công.
    +  Phương thức: displayWelcomeMessage().

Biểu đồ lớp:    
![Class - Login](https://www.planttext.com/api/plantuml/png/R951Ri8m44NtFiKiWqGka4L59JPTLAg4KDU3FIGZEJRoZ5iXnCcww95w1Hm8q9Puv-_vUd--Vxw-5wAODFVU6EjH1DP22Gu6ogaXbylB4XhWeB-aW3qLSQM9GplgksB-ZCdzrG5yR3bKio9lOlHtCMQjPkPunJvdxIWeMrIEORKNfNwC0V21dXqgLG_m-IFt7wf3wTx6cMfoU8nxYx8iZat4CdNbEvQTn_qxUHjxUYKHR2zXYdqexBp8kRcwVfhUfRaqOIOV1zSTsq0Ynuci2l0M95jRaCOiABZXfqu0003__mC0)

Biểu đồ tuần tự:  
![Sequence - Login](https://www.planttext.com/api/plantuml/png/b5AnJiCm4Dtz5QTE8C4FT415C30WX0Hym96OnghZHF6vA7C71gPE32mW1aGb90QcPEYGYl_m5_0BN19A6iI21yllVFVktRC_o-N84cRaOYq41fHaS65b9bAEgK2bQ0W6nybO6JZ5iHm0Mj0rh54_QzzH90rZ99KOECijoRWfGBvfOR_Y46rqcM0MDbdX6WbHIu3TlQuJ3E4ayiLh2bGj3ApcgvaPWsb3q-e1OZuHJ3ZmuaHNnXnTSoQPebOXajnotC5WB7SWHMklaopSvlarmNbKlJCryS2HBvzIqBwy4S1hW-YNj6-3h0i2QUsWoUvf-1cjJZw8NExB6VD_lFdodfkjvhvO6kZi459RkIbbqXx_g-WAbPRX7u8QWuTmf1eXnBotDUsTQipCguM3m1VFRcsnziMZ4jBmsunuht_B5m000F__0m00)

4. Phân tích ca sử dụng Create Administrative Report:  
Các lớp phân tích:  
-  ReportSystem: Lớp chịu trách nhiệm tạo báo cáo dựa trên các tham số từ admin.
    +  Thuộc tính: 
