# Thiết kế hệ thống con Run Payroll 

### 1. Distribute subsystem behavior to subsystem elements
- SystemClock Subsystem: Kích hoạt tiến trình tính toán lương thông qua hàm runPayroll().
- PayrollController Subsystem:
  - Kiểm tra ngày phát lương (isPayday()).
  - Lấy thông tin tiền lương (getPayAmount()).
  - Tạo bảng lương (createWithAmount(float)).
  - Truyền thông tin thanh toán đến IBankSystem bằng hàm deposit (Paycheck, BankInformation).
  - Gửi dữ liệu bảng lương đến IPrintService để in phiếu lương (print(Paycheck, String)).
- Employee Subsystem:
  - Tính toán tiền lương (calculatePay()).
  - Lấy thông tin bảng chấm công (getTimecardInfo()).
  - Lấy thông tin đơn đặt hàng (Purchase Order) nếu có getPOInfo().
- External Subsystems:
  - IBankSystem: Nhận yêu cầu gửi tiền từ PayrollController thông qua hàm deposit() và thực hiện sendTransaction().
  - IPrintService: In phiếu lương bằng cách nhận lệnh từ PayrollController thông qua hàm  print().

### 2. Document subsystem elements
#### 1. SystemClock Subsystem
- Mục đích: Kích hoạt tiến trình tính lương tại thời điểm đã lên lịch.
- Thành phần:
  - SystemClockInterface: Giao diện cung cấp thời gian hiện tại và kích hoạt tiến trình.
- Hoạt động chính: Kích hoạt hàm runPayroll() để bắt đầu quy trình.
#### 2. PayrollController Subsystem
- Mục đích: Điều phối và xử lý các bước trong quy trình bảng lương.
- Thành phần:
  - PayrollController:
    - KIểm tra ngày phát lương isPayday().
    - Tính toán lương (getPayAmount() và calculatePay()).
    - Tạo phiếu lương (createWithAmount(float)).
    - Gửi lệnh gửi tiền đến ngân hàng (deposit(Paycheck, BankInformation)).
    - In phiếu lương qua dịch vụ in (print(Paycheck, String)).
- Tương tác:
  - Lấy thông tin từ Employee Subsystem.
  - Kết nối với IBankSystem để xử lý giao dịch.
  - Gửi lệnh in đến IPrintService.
#### 3. Employee Subsystem
- Mục đích: Cung cấp thông tin nhân viên cần thiết cho quy trình bảng lương.
- Thành phần:
  - Employee:
    - Tính lương dựa trên thông tin chấm công (calculatePay()).
    - Truy xuất thông tin chấm công (getTimecardInfo()).
    - Lấy thông tin đơn đặt hàng (nếu có) (getPOInfo()).
- Tương tác: Gửi dữ liệu cho PayrollController.
#### 4. IBankSystem Subsystem
- Mục đích: Xử lý giao dịch thanh toán lương.
- Hoạt động chính: Thực hiện giao dịch gửi tiền (sendTransaction()).
- Tương tác: Nhận lệnh từ PayrollController qua deposit().
#### 5. IPrintService Subsystem
- Mục đích: In phiếu lương và báo cáo.
- Hoạt động chính: Nhận yêu cầu in phiếu lương (print(Paycheck, String)).
- Tương tác: Nhận dữ liệu từ PayrollController để in phiếu lương.

### 3. Describe Subsystem Dependencies
- SystemClock Subsystem
  - Phụ thuộc vào:
    - PayrollController Subsystem: SystemClock kích hoạt tiến trình tính lương qua PayrollController thong qua hàm runPayroll().
  - Mô tả:
    - SystemClock cung cấp thời gian hiện tại và quyết định khi nào tiến trình bảng lương sẽ được thực thi.
- PayrollController Subsystem
  - Phụ thuộc vào:
    - SystemClock Subsystem: Để nhận thông tin về thời gian và bắt đầu quy trình bảng lương (runPayroll()).
    - Employee Subsystem: Để tính toán tiền lương và lấy thông tin về nhân viên như bảng chám công (calculatePay(), getTimecardInfo(), getInfo()).
    - IBankSystem Subsystem: Để gửi tiền lương cho nhân viên (deposit()), thực hiện giao dịch gửi tiền (sendTransaction()).
    - IPrintService Subsystem: Để in phiếu lương cho nhân viên (print()).
  - Mô tả:
    - Phụ thuộc vào các subsystem khác để hoàn thành quy trình tính lương, xử lý giao dịch và in phiếu lương.
- Employee Subsystem
  - Phụ thuộc vào:
    - PayrollController Subsystem: Cung cấp thông tin về bảng lương cho PayrollController, bao gồm các dữ liệu về chấm công (Timecard) và thông tin đơn hàng (PurchaseOrder).
  - Mô tả:
    - Employee Subsystem phụ thuộc vào PayrollController để tính toán và cung cấp lương cho nhân viên. Nó cũng cung cấp thông tin bảng chấm công và đơn đặt hàng (nếu có).
- IBankSystem Subsystem:
  - Phụ thuộc vào:
    - PayrollController Subsystem: Nhận yêu cầu gửi tiền từ PayrollController để thực hiện giao dịch thanh toán.
  - Mô tả:
    - IBankSystem cần phải nhận thông tin từ PayrollController để thực hiện các giao dịch gửi tiền cho nhân viên.
- IPrintService Subsystem
  - Phụ thuộc vào:
    - PayrollController Subsystem: Nhận yêu cầu in phiếu lương từ PayrollController.
  - Mô tả:
    - IPrintService phụ thuộc vào PayrollController để nhận thông tin cần in và thực hiện việc in phiếu lương cho nhân viên.
### Sơ đồ phụ thuộc giữa các hệ thống con Run Payroll
![Dependency - Run Payroll](https://www.planttext.com/api/plantuml/png/V59BRiCW5Dnp2fIL8pKNyAAA6dMHLIqv5tZ1Bouo7mkUMrbLJjP5ZzGh558x9J8D6-DXD3DluFlpQ-i970rQiHv41otoLJrwGhrJLdIy7ex-yhlY7unpeS1xdX8Y6fORJ0MZiqeLwu2SsPdz2KudEsieVj7bPPUqILmu1C82j1qCbVoaBD0wwnjMWxtraeeUHl6AeYkZxcNtm8zWkhqvsP8_JJkdWQGroypFkbTsHCn7lPxE2K69GOMGmMiEqY8Tf4O1hebE2LozN85RqtsCzTjktZSbJDOUJNDmO3o8E4bEjNBIK8tkJOf_vhcbJCfznB8zDaWWbIzvJO7JNYtJXx5fxBlPF2vlbItlUUREjTwX90tSOwNpi6seABxm7m000F__0m00)

# Thiết kế hệ thống con Maintain Timecard

### 1. Distribute subsystem behavior to subsystem elements
- Employee Subsystem: Cung cấp thông tin như số giờ làm việc, mã chi phí.
- TimecardForm Subsystem:
  - Hiển thị giao diện để nhân viên nhập hoặc chỉnh sửa thông tin.
  - Xử lý các thao tác nhập liệu và gửi dữ liệu đến TimecardController. 
- TimecardController Subsystem: Xử lý logic chính của hệ thống:
  - Lấy timecard hiện tại từ Employee hoặc tạo mới.
  - Yêu cầu thông tin mã chi phí từ IProjectManagementDatabase.
- Timecard Subsystem:
  - Lưu trữ dữ liệu cụ thể của từng timecard (ví dụ: ngày tháng, số giờ làm việc, mã chi phí).
  - Được cập nhật bởi TimecardController.
- IProjectManagementDatabase:
  - Cung cấp mã chi phí cần thiết để liên kết với dự án.
  - Lưu trữ thông tin về các dự án liên quan đến nhân viên.

### 2. Document subsystem elements
#### 1. Employee Subsystem
- Mục đích: Đại diện cho nhân viên trong hệ thống, khởi tạo và thao tác với timecard.
- Hoạt động chính:
  - Duy trì timecard (maintain timecard()).
  - Nhập số giờ làm việc và mã chi phí (enter hours for charge numbers()).
  - Lưu thông tin timecard (save timecard()).
- Tương tác: Gửi dữ liệu nhập liệu đến TimecardForm.
#### 2. TimecardForm Subsystem
- Mục đích: Cung cấp giao diện biểu mẫu để nhân viên thao tác với thông tin timecard.
- Hoạt động chính:
  - Hiển thị thông tin timecard (display timecard()).
  - Chấp nhận thông tin nhập vào từ nhân viên.
  - Chuyển thông tin đến TimecardController để xử lý.
- Tương tác: Nhận thông tin từ Employee và gửi dữ liệu đến TimecardController.
#### 3. TimecardController Subsystem
- Mục đích: Là bộ điều khiển chính, chịu trách nhiệm xử lý logic của hệ thống liên quan đến timecard.
- Hoạt động chính:
  - Lấy thông tin timecard hiện tại (get current timecard()).
  - Nhận dữ liệu từ TimecardForm và xử lý.
  - Cập nhật timecard (update timecard()).
  - Lưu thông tin timecard (save timecard()).
  - Lấy mã chi phi từ IProjectManagementDatabase.
- Tương tác: Giao tiếp với TimecardForm, Timecard, và IProjectManagementDatabase.
#### 4. Timecard Subsystem
- Mục đích: Lưu trữ thông tin cụ thể của từng timecard.
- Hoạt động chính:
  - Lưu thông tin về ngày tháng, số giờ làm việc, và mã chi phí.
  - Được cập nhật thông qua TimecardController.
- Tương tác: Nhận yêu cầu cập nhật từ TimecardController.
#### 5. IProjectManagementDatabase Subsystem
- Mục đích: Đại diện cho cơ sở dữ liệu quản lý dự án.
- Hoạt động chính:
  - Cung cấp mã chi phí (charge numbers) liên quan đến các dự án.
  - Hỗ trợ kết nối thông tin giữa timecard và dự án.
- Tương tác: Cung cấp dữ liệu cho TimecardController khi được yêu cầu.

### 3. Describe subsystem dependencies
- Employee Subsystem
  - Phụ thuộc vào: TimecardController Subsystem.
  - Mô tả: Cung cấp thông tin timecard và khởi tạo yêu cầu cập nhật thông tin timecard thông qua TimecardController.
- TimecardForm Subsystem
  - Phụ thuộc vào: Employee Subsystem.
  - Mô tả: Nhận dữ liệu từ Employee, cho phép nhập thông tin vào và gửi dữ liệu đến TimecardController để xử lý.
- TimecardController Subsystem
  - Phụ thuộc vào:
    - TimecardForm Subsystem: Nhận dữ liệu từ biểu mẫu.
    - Timecard Subsystem: Đọc, cập nhật và lưu dữ liệu timecard.
    - IProjectManagementDatabase Subsystem: Lấy mã chi phí từ cơ sở dữ liệu.
  - Mô tả: Là trung tâm điều phối chính giữa các subsystem. Nó nhận thông tin từ TimecardForm, xử lý logic, và giao tiếp với Timecard và IProjectManagementDatabase.
- Timecard Subsystem
  - Phụ thuộc vào: TimecardController Subsystem.
  - Mô tả: Lưu trữ và cập nhật thông tin timecard theo yêu cầu của TimecardController.
- IProjectManagementDatabase Subsystem
  - Phụ thuộc vào: TimecardController Subsystem.
  - Mô tả: Cung cấp mã chi phí liên quan đến các dự án khi được yêu cầu từ TimecardController.

### Sơ đồ phụ thuộc giữa các hệ thống con Maintain Timecard
![Dependency - Maintain Timecard](https://www.planttext.com/api/plantuml/png/Z99BQiCm48RtEeN8gbta2i7WjD15Gw2zmDWQNBTw6CqumOISh8iSgLUeJFt64HtGGZC_-kQVqS_tBI46pxNHeeBy2mgKcoTJQTSWohSweuOOpKPUX9Iv1Y8vLDjKY0BvlJIOWrSFUs1y_4iRA2s7CzJQ_5LSnSZfIy_EctNMJD7nL4cLXcRsRWY24_w3bJhBtccDFawSw3fkNQdWReaDxjCFy0McJY55m75S3sbTh3poSlJk4tD-1Hlk1Ys7IKC6T6T74VrbqVUXDXdwIUV3VhVAdUrsDrk2c6ragHY79bRck5J7DFSDY0IjQh_hBm000F__0m00)

# Thiết kế hệ thống con Login

### 1. Distribute subsystem behavior to subsystem elements
- MainEmployeeForm Subsystem:
  - Hiển thị giao diện chính sau khi đăng nhập.
  - Thiết lập ngữ cảnh bảo mật (setupSecurityContext()).
  - Hiển thị các thao tác có sẵn cho user (displayAvailOperations()).
- LoginForm Subsystem:
  - Thu thập thông tin người dùng (UserID và password).
  - Xác thực thông tin đăng nhập.
  - Thiết lập ngữ cảnh bảo mật cho người dùng đã đăng nhập.
- ISecureUser Subsystem
  - Tạo ngữ cảnh bảo mật cho người dùng khi đăng nhập thành công new(UserID).
  - Xác nhận thông tin bảo mật cho người dùng khi đăng nhập (validateUserIDPassword).

### 2. Document subsystem elements
#### 1. MainEmployeeForm Subsystem
- Mục đích: Cung cấp giao diện chính cho người dùng sau khi đăng nhập thành công, hiển thị các thao tác.
- Hoạt động chính:
  - setupSecurityContext(): Thiết lập thông tin bảo mật.
  - displayAvailOperations(): Hiển thị các thao tác có sẵn cho người dùng.
- Tương tác:
  - Nhận dữ liệu từ LoginForm Subsystem.
  - Kết nối với ISecureUser để xác thực thông tin bảo mật khi cần.
#### 2. LoginForm Subsystem
- Mục đích: Thu thập thông tin đăng nhập của người dùng và xác thực thông tin đó.
- Hoạt động chính:
  - open(): Mở giao diện đăng nhập.
  - getUserContext(): Thu thập thông tin về người dùng.
  - validateUserIDPassword: Xác thực thông tin đăng nhập.
  - setupSecurityContext(): Thiết lập bảo mật sau khi xác thực thành công.
- Tương tác:
  - Kết nối với ISecureUser Subsystem để xác thực thông tin người dùng và thiết lập bảo mật.
  - Gửi ngữ cảnh bảo mật tới MainEmployeeForm.
#### 3. ISecureUser Subsystem
- Mục đích: Lưu trữ và quản lý thông tin bảo mật người dùng trong suốt phiên làm việc.
- Hoạt động chính:
  - new(UserID): Tạo ngữ cảnh bảo mật cho người dùng khi đăng nhập thành công.
  - validateUserIDPassword: Kiểm tra tính hợp lệ của thông tin đăng nhập.
- Tương tác:
  - Nhận yêu cầu xác thực từ LoginForm Subsystem.
  - Cung cấp thông tin bảo mật cho MainEmployeeForm Subsystem.

### 3. Describe subsystem dependencies
- MainEmployeeForm Subsystem
  - Phụ thuộc vào: LoginForm Subsystem, ISecureUser Subsystem.
  - Mô tả:
    - Cần thông tin từ LoginForm Subsystem để hiển thị giao diện chính và các thao tác.
    - Cần ngữ cảnh bảo mật từ ISecureUser Subsystem để xác thực và thực hiện các thao tác bảo mật.
- LoginForm Subsystem
  - Phụ thuộc vào: ISecureUser Subsystem.
  - Mô tả: Cần xác thực thông tin người dùng và thiết lập ngữ cảnh bảo mật qua ISecureUser Subsystem.
- ISecureUser Subsystem
  - Mô tả: Cung cấp các dịch vụ bảo mật, không phụ thuộc vào hệ thống con.

### Sơ đồ phụ thuộc giữa các hệ thống con Login
![Dependency - Login](https://www.planttext.com/api/plantuml/png/X95B2i8m48RtEKLmfGkl88eF41I5uW76PYZ1D0cPgRL8J-R28ta5RLNggvZjzpFVdvdBwJmaXi1PQeI7U0S9oiuIj9scthW2SUP2AgDiImKnfXrv55B61eZaLwf2jqV8cOympeBcOkmiuu6xlJjJcho1OhG7RLOU0x1sbcfQYb8q5HOkqRRTtU27r7cqJqc2l24C7-ez6As0iKBpoVes9NT1FMbhwVTQypfIp_XTx3Nmg6Onxzwb_vlKjg_5zfNBRN_G_Bezyk8NpP9-qI5QLLtz2W00__y30000)
