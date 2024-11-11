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
![Class - Maintain Purchase Order](https://www.planttext.com/api/plantuml/png/V9B1JiCm38RlUGehfsvQDxXMQ1eI5oGGamOFOD9i2qgJaZX82F5a77WaNe6qpRgjczQRxJ_kxy_--_bTU497eTAC2OtUmp8uiKKldrmf7NmnY5yEjedkxw00PIZbVAXhhQAeW1KvPJQxF245FymgabMJV52URfREba7GFDN84khRoWP3KL7QyAfbMm8GJY9rPhAJ7qxETnsbjw4k-xSNXLxIgZMT3Rpl10ADaBhhD6BVFQkkJq-fxk819uEL7D9u3sX8qUUHC1X5IwU4F860MWGTPtbkG6MZVRstyk8FjXNyoRBEcN1MxtC0indmjFqOHo3hDO-B1_w81ZVIyUG6wpZdH-BQ7aPiSdGsEsnElab15uIJA45lpG7mED7n2V9h3kCy1turdOvvpxm0OGsXCfwriwTodiy79rn0rVhtZ2saAPjJ_mS00F__0m00)

Biểu đồ tuần tự:  
![Sequence = Maintain Purchase Order](https://www.planttext.com/api/plantuml/png/X58zJiCm5DvzYgTCZLGkm82AAYO4L702otbD38bjx6Uad82P6u0OkZ8mDKE78kwH4t05d3X015NnO3zRtz-p_T5iPewu9L-LZ751si9SLvLqJcg5sKbbIbqZ0dSGSClbW3dZYkTek-CgbeoP82E5D5mH90jlHS4TNjWCRTBXT5Snrgl0mL7Smo48YvmYRkAyCQL4EmL9MBaftFgW9gcUWh5IOCeYQqHtI5V4oRj9ia2LIPKdwGuNRx9lbr_Q0JxqC2PmOwo-6nZxVOyZDEkCUKbmtgut7juUtfyK5Dj7bSDDiNqDIpXwQPjd0Pcls-QU68InmzlYDGgArk5sd5Pf3zqNuhBdz272DSGWfuK4qQvN8KRRhEfnf5xlxrjm9R3ywla_otcFBdyyPs7kFj8d0000__y30000)

3. Phân tích ca sử dụng Login:
Các lớp phân tích:
-  User: Đại diện cho người dùng.
    +  Thuộc tính: userID, username, password.
    +  Phương thức: Login(), Logout().
