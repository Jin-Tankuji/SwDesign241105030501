# Thiết kế ca sử dụng Login
### 1. Describe Interaction Among Design Objects
- Người dùng nhập thông tin tài khoản và gửi yêu cầu.
- Hệ thống nhận dữ liệu, chuyển đến hệ thống xác thực.
- Hệ thống xác thực kiểm tra dữ liệu với cơ sở dữ liệu.
- Nếu thông tin hợp lệ, người dùng được truy cập vào hệ thống. Ngược lại, thông báo lỗi đến người dùng.

### 2. Simplify Sequence Diagrams Using Subsystems
- Login Form (Giao diện): Nhận thông tin tài khoản từ người dùng.
- Authentication System (Hệ thống xác thực): Xác minh thông tin đăng nhập.
- Database (Cơ sở dữ liệu): Quản lý dữ liệu tài khoản.

![Sequence - Login](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aK9eSMeH5nU8LD2rKr3ooK_Fp5Dmoo_ALLAmKl3BUBXhRO52ICRXBNdf2Y50cP332p8Ll3Fo7-vQdCU5eXgasx6q92CrhoGpER4aCpzF8RYok2GLR93xmzrhCv7DEJBXI3EG2R602vT6a9akYIM9IOd5gI1ZGefAAnN27kvQcgVWyd3tUWMVp8UxsqiL_DAFRNYuUswcWilXdNdfN4XQy3egf0Ze2w1nknlnceR7RQYXvVrmr_uIXS1IaAaHXnSc0_txSFV6P8nW0WUsbO87qBhcFB2YRcIzN5mEgNafe1W20000__y30000)

### 3. Describe Persistence-Related Behavior
- Database lưu trữ thông tin người dùng.
- Authentication System xử lý xác thực, không lưu thông tin.

### 4. Refine the Flow of Events Description
##### Luồng cơ bản:
- Người dùng nhập thông tin tài khoản và nhấn "Đăng nhập".
- Hệ thống kiểm tra thông tin với cơ sở dữ liệu.
- Nếu đúng, hiển thị thông báo thành công và chuyển hướng.
##### Luồng ngoại lệ:
- Sai thông tin đăng nhập: Thông báo lỗi và yêu cầu nhập lại.
- Tài khoản bị khóa: Hiển thị thông báo và yêu cầu nhập lại.
- Lỗi kết nối với cơ sở dữ liệu: Thông báo người dùng thử lại sau.

### 5. Unify Classes and Subsystems
- Login Form và Login Controller được gộp vào Login Module: Quản lý giao diện và logic cơ bản của quá trình đăng nhập.
- Authentication System: Chứa các lớp xử lý bảo mật như Validator, Authenticator (kiểm tra thông tin, mã hóa mật khẩu, v.v.).
- Database: Quản lý cơ sở dữ liệu.
  
### Diagram    
![Diagram](https://www.planttext.com/api/plantuml/png/T9A_JWCn38VtF8NLlI_G0HLHCS40LLbG1pTdIaGILuupd11Fni0ZyGgawLNtHyToads_p_dEkT_ldtLI5Ct1cnFQ3pmIB1xuw28ySfCzBU3J0BnUMlSiOGzzVSTHXRqdsPilqm-upVfEKPr5THnXsoQbq4rwGUyQL2v8gGP9dWpPeE81qzLWbqZWsgl9aTHoUJDZ1IlOvaDm2hw-Sl6DpKoiqhrPmRg2m0erPqFqoGmZ5Hdh5spG8CX5sKmpbHj_JE6UCabRWSvnafW_xPaqIxnWHGld3vlRIaVY-AA4KlRwxuA6-rx1ngMJnnPIjfPI0XOWaV8CfIetQCoQOdF-iVu0003__mC0)

### Lý do: 
- Bảo mật: Tách biệt giao diện đăng nhập và hệ thống xác thực giúp bảo vệ thông tin người dùng.
- Xử lý hiệu quả: Hệ thống xác thực kiểm tra và mã hóa mật khẩu, đảm bảo an toàn khi làm việc với cơ sở dữ liệu.
- Quản lý lỗi: Xử lý và thông báo lỗi rõ ràng (sai thông tin, tài khoản bị khóa, lỗi kết nối), nâng cao trải nghiệm người dùng.
- Tính mở rộng: Thiết kế mô-đun dễ dàng mở rộng, hỗ trợ các tính năng bảo mật bổ sung trong tương lai.

# Thiết kế ca sử dụng Maintain Timecard
### 1. Describe Interaction Among Design Objects
- Nhân viên đăng nhập vào hệ thống.
- Nhân viên truy cập và sửa thẻ chấm công thông qua Timecard Manager.
- Timecard Manager cập nhật thẻ chấm công trong hệ thống.
- Payroll System sử dụng thông tin từ thẻ chấm công để tính lương cho nhân viên.

### 2. Simplify Sequence Diagrams Using Subsystems
- Employee: Giao tiếp với Timecard Manager để chỉnh sửa thẻ chấm công.
- Timecard Manager: Lưu trữ và cập nhật thông tin thẻ chấm công.
- Payroll System: Sử dụng thông tin từ các thẻ chấm công để tính toán lương.

![Sequence - Maintain Timecard Subsystem](https://www.planttext.com/api/plantuml/png/V94nIWGn68NxdEA_W1VOGhRGKX3q0Z4JPW99Pidy6KYvM8Zbtc074K4OjB2Q51QHlKTEu1LC1cRH9TY4aFplotilt_vptI4rQ9Kab65hu59jPEiu9roZG0UtGd56JNL5DQsvMOulAD8xsXt7hgaphPGthaEk25aeS7P-Ie0LkF1gWSNfnG8Qw_9st00sSVB0qlgiW8KFNPDJQQ8ToQkaZTCJzD5leOh-3QI8_i6MEF_RIQF-KJVGHJ_IWXpwi8SwNGgGSHf4oTRIHyRDQNG2Z3XBvU4z1yqMiPc1A3JvqrZPs5nEdupeNyAImQzTzFU0OKmfi0s3pcyUXfIShBckyk_-0000__y30000)

### 3. Describe Persistence-Related Behavior
- Database lưu trữ thẻ chấm công của nhân viên.
- Timecard Manager cung cấp các phương thức để truy xuất và lưu trữ thông tin thẻ chấm công.
- Payroll System sử dụng dữ liệu từ Timecard Manager để tính lương nhưng không lưu thông tin.

### 4. Refine the Flow of Events Description
##### Luồng cơ bản:
- Nhân viên đăng nhập vào hệ thống và yêu cầu truy cập thẻ chấm công.
- Timecard Manager lấy thông tin thẻ chấm công từ cơ sở dữ liệu và trả về cho nhân viên.
- Nhân viên chỉnh sửa thẻ chấm công và gửi yêu cầu cập nhật.
- Timecard Manager cập nhật thẻ chấm công trong cơ sở dữ liệu.
- Payroll System truy vấn thông tin thẻ chấm công để tính lương cho nhân viên.
##### Luồng ngoại lệ:
- Nếu nhân viên không có quyền truy cập thẻ chấm công: Thông báo lỗi quyền truy cập.
- Nếu dữ liệu không hợp lệ khi chỉnh sửa thẻ: Thông báo lỗi dữ liệu và yêu cầu nhập lại.
- Nếu hệ thống không thể lưu thẻ chấm công: Thông báo lỗi lưu trữ và thử lại sau.

### 5. Unify Classes and Subsystems
- Timecard Module (gồm Timecard và Timecard Manager): Quản lý thẻ chấm công, thực hiện các thao tác CRUD.
- Payroll Module (gồm Payroll System): Tính lương dựa trên thông tin từ thẻ chấm công.

### Diagram  
![Diagram](https://www.planttext.com/api/plantuml/png/X96_2i8m4CRtUugZkxWxY88T78JwRnA7Cpcbc3ObIGj5V3877ybNi5LYRIcw9NVVxxkFkyVjFh6EZCiJ1Hc9CvqOWqsSi20ZSQ5bhZZ02o3kV7MFtpzSK5f1PWzNQ1mYAerMgctWY-lIEaxQm8mS7SXsPw6llzGad3OO9fdI9JE0V-5WCEv9X2ES2i7M3aCPE_Hzw56s36hmtVamAAiSVy4cRUMmOcTYBdYupIgOlyPtzl33OvcpARiX-l3F9aOO6Lt4aj7BvkbH0qmubVMDdm000F__0m00)

### Lý do:
- Tách biệt mô-đun: Tạo các mô-đun riêng biệt (Timecard Module và Payroll Module) giúp quản lý thẻ chấm công và tính lương độc lập, dễ bảo trì và mở rộng.
- Bảo mật và quyền truy cập: Đảm bảo chỉ nhân viên có quyền truy cập mới chỉnh sửa thẻ chấm công.
- Xử lý lỗi rõ ràng: Các lỗi như quyền truy cập, dữ liệu không hợp lệ hay lỗi lưu trữ được thông báo rõ ràng, giúp người dùng dễ dàng khắc phục.
- Quản lý dữ liệu hiệu quả: Dữ liệu thẻ chấm công được lưu trữ, nhưng thông tin tính lương không bị lưu lại, bảo mật và bền vững.

# Thiết kế ca sử dụng Run Payroll
### 1. Describe Interaction Among Design Objects
- Payroll System nhận lệnh tính lương từ System Clock khi đến thời điểm cần tính lương.
- Payroll System tính toán lương cho nhân viên dựa trên thông tin từ Timecard và các dữ liệu khác.
- Sau khi tính toán, Payroll System gửi thông tin thanh toán đến Bank System để thực hiện chuyển khoản.
- (Lựa chọn) Payroll System gửi báo cáo lương đến Printer để in.

### 2. Simplify Sequence Diagrams Using Subsystems
- Payroll System: Chịu trách nhiệm tính lương và gửi kết quả cho Bank System và Printer.
- Bank System: Xử lý thanh toán chuyển khoản.
- Printer: In báo cáo lương.
- System Clock: Kích hoạt Payroll System theo lịch trình.

###### Biểu đồ tuần tự:  
![Sequence - Run Payroll](https://www.planttext.com/api/plantuml/png/R90z3i8m38NtdCBgL2Iu00EgW8KDmGbCiAge-PFZ3ZqR0qVY2gI4IYrYi_q-lsVvzNWsIP2bTrOfr18OhaCISWSRTATYbems4Rr0TSQ1WxL5hm0Jn39POdlqtOovvVR7XuqNuk9GQgLcgR3PJSwm1M7JjiJVy7gb9cb1QRIwjoZqbnjlo53ae2cbZ3ZoKfEBDWn4f-CQq8NUozAydFRPozM5Ok3_IweXVny_-0O00F__0m00)

### 3. Describe Persistence-Related Behavior
- Payroll System không lưu trữ trực tiếp các thông tin về lương mà lấy thông tin từ cơ sở dữ liệu (Timecard và User).
- Bank System và Printer không lưu trữ thông tin thanh toán hay báo cáo mà chỉ xử lý và thực hiện các hành động cụ thể (chuyển khoản và in báo cáo).

### 4. Refine the Flow of Events Description
##### Luồng cơ bản:
- System Clock kích hoạt Payroll System khi đến thời điểm tính lương.
- Payroll System tính lương dựa trên dữ liệu có sẵn.
- Payroll System gửi thông tin thanh toán đến Bank System.
- Payroll System gửi báo cáo lương đến Printer để in.
##### Luồng ngoại lệ:
- Nếu có lỗi khi tính lương: Thông báo lỗi gửi đến Payroll System, thông báo lỗi cho người dùng.
- Nếu có sự cố khi chuyển khoản: Thông báo lỗi gửi từ Bank System đến Payroll System, thông báo lỗi cho người dùng.
- Nếu có sự cố khi in: Thông báo lỗi gửi từ Printer đến Payroll System, thông báo lỗi cho người dùng.

### 5. Unify Classes and Subsystems
- Payroll System: Xử lý tính toán lương, gửi thông tin đến các hệ thống thanh toán và in.
- Bank System: Hệ thống thanh toán.
- Printer: Hệ thống in báo cáo.
- System Clock: Hệ thống lên lịch tự động cho quá trình tính lương.

### Diagram    
![Diagram](https://www.planttext.com/api/plantuml/png/V99DJiCm48NtFiMeArZq0YogYfy52wIeAIlKnU1CWnN_HBQB525Ene8ZSGNij2Pneh1zyxutppy_NzzRvz7wavAiHTvWJR0giBD6IdWorKdI2ZuOm4iIoyvvKWTWdsmWRb4tkRrNBjxCMbYXFTb9-5dCdMSQxgJXpSLNyZUAsCHvZnvVqQMqlL34qLQGz4DKdrtOEYY1H-wDXGVLIjCHCJQAX_LwCp_p3UojgEkGaoQ5DPoS4xfcCtSVCUyIKdRahQ1tWcowa93t7jD_amLo_0Q1AqbNiRWYxU5H7urLw8NH2tHwan7PctRK6klXohGHHddDyaKHJdVQtnXgTmn5IvHeEpRaJeoz_iyMjWqjuZ_z1G00__y30000)

## Lý do:
- Tự động hóa: Quy trình tính lương tự động hóa theo lịch trình giúp tiết kiệm thời gian và giảm sai sót.
- Tách biệt chức năng: Tách riêng các hệ thống như BankSystem và Printer giúp dễ dàng quản lý và bảo trì.
- Xử lý lỗi rõ ràng: Các lỗi chuyển khoản hoặc in được thông báo kịp thời, giúp xử lý nhanh chóng.
- Mở rộng dễ dàng: Thiết kế linh hoạt, dễ mở rộng cho các tính năng mới.
