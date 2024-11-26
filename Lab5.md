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
### Sơ đồ phụ thuộc giữa các hệ thống con
![Dependency - Run Payroll](https://www.planttext.com/api/plantuml/png/V59BRiCW5Dnp2fIL8pKNyAAA6dMHLIqv5tZ1Bouo7mkUMrbLJjP5ZzGh558x9J8D6-DXD3DluFlpQ-i970rQiHv41otoLJrwGhrJLdIy7ex-yhlY7unpeS1xdX8Y6fORJ0MZiqeLwu2SsPdz2KudEsieVj7bPPUqILmu1C82j1qCbVoaBD0wwnjMWxtraeeUHl6AeYkZxcNtm8zWkhqvsP8_JJkdWQGroypFkbTsHCn7lPxE2K69GOMGmMiEqY8Tf4O1hebE2LozN85RqtsCzTjktZSbJDOUJNDmO3o8E4bEjNBIK8tkJOf_vhcbJCfznB8zDaWWbIzvJO7JNYtJXx5fxBlPF2vlbItlUUREjTwX90tSOwNpi6seABxm7m000F__0m00)
