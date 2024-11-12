PHÂN TÍCH YÊU CẦU:
  - Cho phép nhân viên nhập thông tin thẻ chấm công.
  - Hệ thống chạy trên hệ điều hành Windows.
  - Hệ thống phải hoạt động với csdl DB2 chạy trên máy chủ IBM (được phép truy cập, không được cập nhật).
  - Hệ thống tính lương theo giờ. Nếu làm việc hơn 8 giờ sẽ trả gấp 1,5 lần mức lương bình thường cho những giờ làm thêm. Người làm việc theo giờ được trả lương vào mỗi thứ 6.
  - Nhân viên được trả lương cố định vẫn nộp thẻ chấm công ghi lại ngày và số giờ làm việc, được trả lương vào ngày cuối cùng của tháng.
  - Nhân viên hưởng lương nhận được hoa hồng dựa trên doanh số của họ với các mức 10%, 15%, 25% hoặc 35%.
  - Nhân viên có thể truy vấn hệ thống để biết số giờ làm việc, tổng số giờ được tính cho 1 dự án, tổng số tiền lương nhận được, thời gian nghỉ phép còn lại, v.v.
  - Cho phép nhân viên chọn phương thức thanh toán như gửi lương đến địa chỉ bưu chính, tài khoản ngân hàng hoặc nhận tại văn phòng.
  - Quản trị viên bảng lương có quyền thêm nhân viên mới, xóa nhân viên và thay đổi tất cả thông tin nhân viên như tên, địa chỉ và phân loại thanh toán (theo giờ, theo lương, theo hoa hồng), cũng như chạy các báo cáo hành chính.
  - Hệ thống sẽ tự động trả lương cho nhân viên vào mỗi thứ 6 và vào ngày làm việc cuối tháng.

1. Đề xuất kiến trúc:
Sử dụng kiến trúc MVC: Model xử lý dữ liệu, View hiển thị giao diện, Controller xử lý yêu cầu.

Lý do:
  - Giúp dễ quản lý và giảm phụ thuộc.
  - Dễ mở rộng và bảo trì.
  - Có thể làm việc song song trên Model, View và Controller.
  - Dễ quản lý nhiều View khác nhau cho các loại người dùng khác nhau.
    
Giải thích từng phần:
  - Model:
      + Employee: Lưu trữ thông tin như id, tên, địa chỉ, phương thức thanh toán và loại nhân viên.
      + EmploymentType: Phân loại nhân viên dựa trên cách trả lương. Các lớp con là HourlyEmployee, SalariedEmployee, CommissionedEmployee.
      + PaymentMethod: Cung cấp phương thức thánh toán: DirectDeposit, PostalMail, OfficePickup.
      + TimeCard, PurchaseOrder: Lưu dữ liệu làm việc của nhân viên (thẻ chấm công) và đơn hàng (cho nhân viên hưởng hoa hồng), dùng để tính lương.
  - View:
      + EmployeeView: Hiển thị thông tin và báo cáo cho nhân viên. Các phương thức displayEmployeeInfo, displayPaymentInfo, displayReports giúp người xem chi tiết thông tin và báo cáo cá nhân.
  - Controller:
      + EmployeeController: Quản lý các yêu cầu giữa Model và View.

Biểu đồ package:   
![MVC - PayrollSystem](https://www.planttext.com/api/plantuml/png/b5NDRjim3BxxANpC3da1eoXQ90FQGzfWBTOpAp694Fr1ahiPMvwiXptINc5oOpkHBCKT3mPiVXB9Zn_fl-z_Rgm3ush12mra3riirz0OnVbJOnsAybTHbDvwvqfHvFvZsHdXO6tvLMYk6iGpnz5wn_soAfbqaVS115QbTOR9RUIwfTIWjHclJr6WT2jqEqMhy3MPGUj-RhIF5hv7O0ASr1mS-XjdNwgIglgLdq278ghxcGbSWA6ZkfV-ZkhZ6JdkL6tiYp9xfDFNhsj3Tc3nqL0qduznArGjtQNhuTNJ2iG5xUiv6GMQP2NCkYsHDuCayAT3IUCWqPadu60OqlyxjL12C6kPajCdSxK7sXcLhc4eP0O1hPw7DyLebeKbCqZS4hMop0r9fPNQPQByAF8LCFuf-EDcmmYk6TdNEdDWE36GCvzVvoWDCEd0aKwkVi_dKRSlGkCcNmIdUflEjH_2mPkKnKTLv_DKdCr4lzs-C_oHNMwHysYKMSrF8hcN6pMBfH4WEsQdWT-yT8op8z0XbVX2ITSkxM1DXEad8KS3El2KoScWK6yu0QerzKjY0hH5YSR3SkKTJHj5_FhlVaKP3beRIUAip9FO4zB9uDecTmGVYXi_K-sVyHy0003__mC0)

2. Cơ chế phân tích:  
  - Cơ chế bảo mật: Đảm bảo nhân viên chỉ truy cập được thông tin cá nhân, còn quản trị viên bảng lương quản lý thông tin nhân viên.
  - Cơ chế kế thừa: Dùng để phân loại nhân viên (theo giờ, cố định, hưởng hoa hồng).
  - Cơ chế hiệu suất: Tối ưu hóa xử lý lương cho nhân viên, đảm bảo hoạt động bình thường, đặc biệt là ngày trả lương.
  - Cơ chế lưu trữ: Lưu trữ dữ liệu thời gian làm việc, thông tin nhân viên, đồng thời tích hợp csdl DB2 đã có sẵn.
  - Cơ chế tự động hóa: Hệ thống sẽ tự động trả lương cho nhân viên vào mỗi thứ 6 và vào ngày làm việc cuối tháng.
    
3. Phân tích ca sử dụng Payment:  
Các lớp phân tích:
  - Employee: Đại diện cho nhân viên và lưu thông tin về phương thức thanh toán.
      + Thuộc tính: employeeID, name, paymentMethod.
      + Nhiệm vụ: Cung cấp thông tin phương thức thanh toán khi hệ thống yêu cầu thanh toán.
  - Payment: Đại diện cho 1 giao dịch thanh toán cho 1 nhân viên vào 1 ngày cụ thể.
      + Thuộc tính: paymentID, amount, date, status.
      + Nhiệm vụ: Lưu giữ thông tin về tiền lương và trạng thái thanh toán.
  - PaymentProcessor: Xử lý việc tính toán và tạo các khoản thanh toán.
      + Nhiệm vụ: Tạo đối tượng Payment dựa trên dữ liệu từ PayrollSystem và phương thức thanh toán của Employee.
  - PayrollSystem: Hệ thống xử lý tính toán số tiền lương của nhân viên.
      + Thuộc tính: payrollID, payrollDate.
      + Nhiệm vụ: Tính toán số tiền lương của nhân viên và chuyển thông tin đến PaymentProcessor để xử lý thanh toán.

Biểu đồ tuần tự:  
![Sequence - Payment](https://www.planttext.com/api/plantuml/png/Z99D3eCW48Ntd6BYIfDw0HTDk-YkJKmy0O59DG4nC2uyMnSzKgzGgDXgVqpPpUDzxm7XThdk775BlLQC2p8MAb6Zx1NAqXg1pW5ta3n5Y6h2kDHD2_aMIZvOerGrE49Tm2CkQj6SPcnX2jH1TyeCY0MSaQRXs3Zovcc4_3CUPrR6mA_rQB-hiQKJKcsapmx4Mdutzp_StqlUCC6Lw1Kdz7fiUKD69cJ7Lp5sXiczDdrBYyA55rwynooELM5CfoVPVCHbywWVHuWN_hEv6zMfEcCxR6NuF7S0003__mC0)

Biểu đồ lớp:    
![Class - Payment](https://www.planttext.com/api/plantuml/png/R59BJiCm4Dtd5AEkg4Gku0MgH5YmGAhe2QnaW4Z-fFQuKeGu6GkEn1MOD6DJGxFmuirxCs_UvFlpQnT91qhMDBtHCSA3dOoV4U6z0VvQG04UEmMZ8q6TjgZWG65qhm9DUhRew0dfpG-bzj58u_rQBds5NhVLrYT72bwCrnaRDF6eZby1s36bM4q7c8BlCKQPShDLSFBZy6_yVgNv83u0-e3SEklojge4SLkRuiR25Nr4DsIrx5Gerrm4RynXZeJsCee5hQCGiAktPx_QzCcibg_OtURmU6QvPTlU_HcjOCDHdCO1os7MmssQcYZIEZjMF-CnOQHSEyjgqeLo4ToVS_xbxpYtvRVx0G00__y30000)

4. Phân tích ca sử dụng Maintain Timecard:  
Các lớp phân tích:
  - Employee: Đại diện cho nhân viên, người có thể tạo, sửa, và gửi các thẻ chấm công của mình.
      + Thuộc tính: employeeID, name, paymentMethod.
      + Nhiệm vụ: Xác thực thông tin của mình, truy cập và chỉnh sửa thẻ chấm công.
  - Timecard: Đại diện cho thẻ chấm công, chứa thông tin số giờ làm việc và ngày làm việc của nhân viên.
      + Thuộc tính: timecardID, date, hoursWorked, chargeNumber.
      + Nhiệm vụ: Cung cấp thông tin về số giờ làm việc của một nhân viên.
  - TimecardManager: Chịu trách nhiệm quản lý các thẻ chấm công, bao gồm việc lưu trữ, cập nhật, và truy xuất thông tin thẻ chấm công.
      + Nhiệm vụ: Xử lý logic lưu trữ, chỉnh sửa, và truy xuất các thông tin từ thẻ chấm công khi nhân viên hoặc các hệ thống khác yêu cầu.
  - PayrollSystem: Chịu trách nhiệm kết nối với các thẻ chấm công để tính toán lương và duy trì thông tin thanh toán.
      + Thuộc tính: payrollID, payrollDate.
      + Nhiệm vụ: Sử dụng dữ liệu từ các thẻ chấm công để tính toán số tiền lương cần trả cho nhân viên vào mỗi kỳ trả lương.

Biều đồ tuần tự:  
![Sequence - Maintain Timecard](https://www.planttext.com/api/plantuml/png/R951JiCm44NtFiKiGMhKVOHGfT8b2BK8rXDxQAtQiHcFaN8s5Xo9As17fL5Gjdx_lndRFr_VcoJ8ahrJg2Kmx7nqOI02J40-gbYerJPYB_1YFMbayuWz7ebhHFnYOaHwXfvnuE3SOKX2llAOb2eJeBalbXRsz94f2KY0BHCAhNV6JaObVapgTX73ZIbdApY5pEajy9dC2lG9-KXFsNV4jrLmrpIZuThIeygiSwnrCrlea3k_lC0hEblpSrPWJAL6lPa6l9SdlTmSjkXqTYWsz4h5z6VRax2bpya63oXu2PHzsckHgifJUSmE4na8_R-EsfJXzIz_0G00__y30000)

Biểu đồ lớp:    
![Class - Maintain Timecard](https://www.planttext.com/api/plantuml/png/Z5BDJeGm4BxtAIQS95dYdOFP0nuyh36YyJnBPu5iVqWf9iJuP1vy95_1ihGLTZMH0u6lq-yly_NnkUqj6Zj8mIg1VG-tiXDw988t1kx9W3nmL-JGAkjHXP9oAArfLUsX3aT9okx8DfglpW3wOIzR-zHAgj3mA-i_SWXGciEhRZbxPzv7E8W-mfsr3uxM-IZSsmED7ap_eisH7Fj1Q0oJLOEcflj1xib4TnToErHOa_6g09KXnnsDXpBosDDcOM4pgtlTz2UT9niwlYJxkuLvl2RxJ-6bL8pqWAFHGfHZRqd66hiPNRVemM9TfakFeXg4-tTSlrX8GyDEC-vDbjrSj9b3KfusuFhvL472pYUMjwRn6K_OEiJvr2CXdsf0E6WJKYHiIufF6_qD003__mC0)

5. Hợp nhất kết quả phân tích:  
Các lớp phân tích:
  - Employee: Đại diện cho nhân viên trong hệ thống.
  - Payment: Đại diện cho thông tin thanh toán của nhân viên.
  - PaymentProcessor: Chịu trách nhiệm thực hiện các giao dịch thanh toán.
  - PayrollSystem: Hệ thống tính toán và quản lý lương cho nhân viên.
  - Timecard: Đại diện cho thông tin chấm công của nhân viên.
  - TimecardManager: Quản lý các thẻ chấm công.  
Mối quan hệ giữa các lớp:
  - Employee gửi và cập nhật thông tin chấm công thông qua TimecardManager.
  - TimecardManager quản lý các Timecard, hỗ trợ lưu trữ và cung cấp thông tin chấm công khi cần.
  - PayrollSystem truy xuất dữ liệu từ Timecard qua TimecardManager để thực hiện việc tính toán lương, nhưng không sửa đổi thông tin trong Timecard.
    
Biểu đồ lớp:  
![Class - Payment + Maintain Timecard](https://www.planttext.com/api/plantuml/png/Z5FBJiCm4BpdArOvjL8ZxZwW7igXXwAAWZYxpf96-17PwqeLuiiuy4dy0axZf35f9NA8al7kp7Yy_ldwNZhYbhoIcP3SENXGZJGdHFZ883m5O0JMAmQrfeXghf31ZcojgmWr_AHGqmRfOCfa3S3vlQhfkLOek2rd53yOzD2SmT7KPVQPHH_RZcsm4TbJ5rmPhud1cpISqi8Lfs2mVKyujzO8TCxOI0xGT4XSdqKArZTSCsUDbBkJ8rHZYosQMepWo4udARWKNeR_m3NhCsP3_FD-KuDcdzGWruUOwfMfK047uwrxDVOTopGeSU2smaUlzcY7uvh8RRZc5LwY4XO3zt2IK-UBaOL5fnvrvvVZZcI-ASTajyUYAw-G_YaybWfR6eQwAEudEsEGxyxZUVTojfDdVol6NMrvX-TPEWOtk9ym98j7RDtnQpsJgGnDQrrJ7RpqqvndIzHbUqj_0G00__y30000)
