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
