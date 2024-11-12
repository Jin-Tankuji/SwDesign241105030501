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
    +  Phương thức: generateReport().
-  Report: Lớp chứa dữ liệu báo cáo và cung cấp các phương thức để xuất ra file PDF hoặc Excel.
    +  Thuộc tính: data, format
    +  Phương thức: exportToPDF(), exportToExcel().
-  Database: Cơ sở dữ liệu lưu các report.

Biểu đồ lớp:      
![Class - Create Administrative Report](https://www.planttext.com/api/plantuml/png/Z50x3e904Ett55jg8XUWC1H8fOaHBp32G4XO83EZWHXFPk6Hl8BBnrMit6QIUM_Vc_UUzqV00YHdKogLbC2i3zZK9777WaPVbHvUZXKI28xWGhe6jQzZeQBALxe10eE2n7QvWsPfnyXKjxdi9EZf50GiQrkmJ9ki9WFYL2TZRFjlnteVHejUDYfA_84sROBb1tIEeRKu0UDN21clw95_CWpNMRrP9PwtVeVnNIyySGRK6VkQqChZ1NaCd55jb0gmIll2Nm000F__0m00)

Biểu đồ tuần tự:         
![Sequence - Create Administrative Report](https://www.planttext.com/api/plantuml/png/R54zJiCm5DvzYgTEL6elqA4g0Wb612TmugVKKkAazalLZ8Y10J5m0oeEm4mzCEGaFW5NuAMkQ4AxMFRpz-VFF_vxuKXQgejS29bIQU5I5Tg8YeSwrPKq1ADxh4fBS8C6hIHT6hYJ6Ov0Eh3xg-vublBGECAYXuo38VPQaaoaYu8g4M8V0QRpdZhCu6eP_Ak1l0oxhOQatPQGTikwVUysAT1I5k22VnCztfzAT6OTYwiQ7SM45zHKE07E8miaj6ui1d2cguH96Hu8NTWp90PDJwt8Xjq7h8D_11Ny9-Gw-EVwcFt4Q_3WBFQDXwIAdSV_dXQRci4j2pyPRY3ubwFy1AZzQY2DnH5dqR2fkI2J2R50exfl_mK00F__0m00)

5. Phân tích ca sử dụng Maintain Employee Info:  
Các lớp phân tích:
-  EmployeeSystem: Chứa các phương thức để thêm, cập nhật, và xóa thông tin nhân viên.
-  Employee: Đại diện cho đối tượng nhân viên với các thuộc tính cơ bản và các phương thức lưu và xóa.
-  Database: Thực hiện lưu trữ, cập nhật, và xóa thông tin nhân viên trong cơ sở dữ liệu.

Biểu đồ lớp:  
![Class - Maintain Employee Info](https://www.planttext.com/api/plantuml/png/p58x3i8m3Drp2ez5eXVeW3h0mC342GonIgGcZMfJX10dO-18N86qAa64pqoMHEyJFJ_vThcMBDZAtjPARMjaXeNrTNCaMXzPoC99mN1GwmUJQHI40bRe9-7g6gD7qTu7YgAEniTo7cHhQOshfl3LhAcct-PeEATXnvWvV72DZ4DBAHQ6QYbyay2-OIEcSIckoOUkB3bvPG0OEye-pfEzXvw71ZR85BljtNzLRh83UJvxDbs0HOSLSLGDV1og0EE4MjmAmy78JgcIdEuNx0u00F__0m00)

Biểu đồ tuần tự:
![Sequence - Maintain Employee Info](https://www.planttext.com/api/plantuml/png/X951IWCn58RtESLFLmeMzowaOWM52e9UuCqaT8AJp7GcK-XIN8bu0ZUYkuBWGX0cYou6l4TEu1MQT3hM2kBkvNylt__dvSik1gMXmbGgPOnYanKuuafgbdjHnZ8dRT0xKNcQpOJ0EMaQ2oMyUE6B7gY4K7ce_xXnEIkDKDrWUzeU7PAXYCeMnYF6LW7GF-p8EC1nuko3XacQkO9ozb4YoLpz4IFsdJkTe7JsbQ2JvbbZAfkvPjtj5jGwUrILSpAYoxSZriNPS0--GRlO1t7-tLzfR0FmD1vvpEZphGfvtlKOniVzwUm7-hzShmfNls3gx0skNRqmc5H1IDUK9_-2EB2sdJOBE9NEteO5E7l_3u4DXERXFvS0003__mC0)

6. Phân tích ca sử dụng Run Payroll:    
Các lớp phân tích:
-  PayrollSystem: Lớp chính thực hiện quy trình tính lương và gửi thông tin đến BankSystem và Printer.
-  Các actor:
    +  BankSystem: Xử lý việc thanh toán lương (mô phỏng chuyển khoản).
    +  Printer: Xử lý việc in báo cáo lương (mô phỏng in).
    +  SystemClock: Kích hoạt PayrollSystem theo lịch trình (ví dụ: hàng tuần hoặc hàng tháng).

Biểu đồ lớp:  
![Class - Run Payroll](https://www.planttext.com/api/plantuml/png/d94nRiCm34LtdO9Z0jGNy504RPTkGNC2LYQC89Haa5G1e-Z9EkH8kK8KkogSf5ErYV__1_7hz7tSgA5O3koSPrI5BOwIc7UZ6WNuT30ToV57MAsXXO-qxoQb0O_iCwFHdVvLaKyO3pUyGP8drP8956r5OU0q4hs-bF3EP1_x1y2GShGow59-PxhdRelFI1RGSd-Z8Sb_YVChdpdvmo-rPFkUfAvtrS-IiCmspUDDaMtbgBiMBjP5GIqenKvXc9k13Wt_IDJLgrschMUtsvJHvKVF0000__y30000)

Biểu đồ tuần tự:    
![Sequence - Run Payroll](https://www.planttext.com/api/plantuml/png/R90z3i8m38NtdCBgL2Iu00EgW8KDmGbCiAge-PFZ3ZqR0qVY2gI4IYrYi_q-lsVvzNWsIP2bTrOfr18OhaCISWSRTATYbems4Rr0TSQ1WxL5hm0Jn39POdlqtOovvVR7XuqNuk9GQgLcgR3PJSwm1M7JjiJVy7gb9cb1QRIwjoZqbnjlo53ae2cbZ3ZoKfEBDWn4f-CQq8NUozAydFRPozM5Ok3_IweXVny_-0O00F__0m00)


Code Java mô phỏng ca sử dụng Maintain Timecard:
- models:
```java
package models;

public class Employee {
	private int employeeID;
	private String name;
	private String paymentMethod;
	
	public Employee(int employeeID, String name, String paymentMethod) {
		this.employeeID = employeeID;
		this.name = name;
		this.paymentMethod = paymentMethod;
	}
	
	public int getEmployeeID() {
		return employeeID;
	}
	
	public void setEmployeeID(int employeeID) {
		this.employeeID = employeeID;
	}
	
	public String getName() {
		return name;
	}
	
	public void setName(String name) {
		this.name = name;
	}
	
	public String getPaymentMethod() {
		return paymentMethod;
	}
	
	public void setPaymentMethod(String paymentMethod) {
		this.paymentMethod = paymentMethod;
	}
	
	public void submitTimecard(Timecard timecard) {
        System.out.println("Timecard submitted for Employee: " + name);
    }
}
