# Thiết kế lớp
### 1. BankSystem
#### Xác định các operations
- deposit(aPaycheck: Paycheck, intoBank: BankInformation): Thực hiện gửi tiền, gọi đến BankSystemInterface để nộp giao dịch.
- validateBankInfo(bankInfo: BankInformation): Kiểm tra thông tin ngân hàng.
- logTransaction(transaction: BankTransaction): Ghi log lại giao dịch đã thực hiện.

![Operations - BankSystem](https://www.planttext.com/api/plantuml/png/h59BQiCm4Dth54DMDjWN4AM4xhnf0ya5nhASYEXZf74Wj3rP5prIhr2hbHErDOL2jH0pcdblvZtqzlAw3eIUHgEPiYHzZq92SuVsk3q7aWOU6NoSJWukA2fmWsTnaEB8OOugcA0kOZZ4kx6zymP9ELjoE3dLiMV6XCOGuD-P8qCD9zIgGv9pKz6cO0dNEgSJJhlzpgCDA6Aje6ly2SoAlqXfBixDciBOcaaI7UJkhvHPFT7LWCQDbZZqsY6bjspNXq5wl4wufAdJkv6KtT-FffMUmvRybAL5XPUJROKRla6hhpEhZ6HcA7_eYKBoltFpLDUPJImhrVNjee4SLicxShNKdqzRIzl5Z_iE003__mC0)

#### Xác định các trạng thái
- Initialized: BankSystem được khởi tạo, sẵn sàng nhận giao dịch.
- ValidatingBankInfo: Kiểm tra thông tin ngân hàng.
- ProcessingTransaction: Giao dịch đang được xử lý.
- SubmittingTransaction: Gửi giao dịch qua BankSystemInterface.
- TransactionCompleted: Giao dịch thành công.
- TransactionFailed: Giao dịch thất bại.

![Status - BankSystem](https://www.planttext.com/api/plantuml/png/Z9B1IiGm443lynK1Boei55aMyI1hImjx4ofUn4EsoIwXQL8cKq75B_FW9_aBPhghXjqA9fTcvhsPITlFzuzb88aqT1P2QrmlKNPYBPjsYtvmgl3MepYfRdWdH9H8YrSGSUM7T9wLMRaOSvLtj8zcuzeP7fN6VNo-kBp8v_06y73-A6QpQx5oXeoqvaKhSJMUOW_Nri-1T0Tfbkdx-Ama6RTbQEKsFafAzpuOEZqJZRHMAvYWMBv5t-WGOlWEfGko8UDTz1aIXgad5l_I4wcInexp_gh6xMIOxi85wc7T6QAZ_WLgVi5SAqd0D7umIU6xtceQXqcnUcXuYlyL-RbEofI87W4cUx4VFo0Sr_ZEBBLJ_9zz0G00__y30000)

#### Xác định các thuộc tính
- Paycheck: Chứa số tiền và thông tin nhân viên.
- BankInformation: Gồm tên ngân hàng và mã định tuyến.
- BankTransaction: Chứa số tiền giao dịch, loại giao dịch, và mã định tuyến.

![Attributes - BankSystem](https://www.planttext.com/api/plantuml/png/V54n3i8m3Dpp2ezKeX_8W029WGMGu0Cck81eaYfrXmhnCWQUn1TeInkQ8iWK-yxdi_syFwOve-D2fqAbcEUmmLATI5tWAg1wCQ2sXM49IMgHcno0SeHCeyIwMH-Df2zlYKVYDsCKXGeLiD1PQakY6kh-uYPQ7tCqbwMfEcZaipNUZa5D4hRipkROffmjk8fMXTwJyrYWj7DeSbI1qlTWCV27jyx8DQrbe-33lqs3zTXiK3eEUuvx8fr298T-wq7yKU9uyjdLSB0Q3At-OlGMAwPa3lNvNm000F__0m00)

#### Xác định các phụ thuộc

![Dependencies - BankSystem](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTcNabgKLfYSgg2frDYNdPmPN59QYvNSavYSR427W5Fc3QeJ41YPN96Qd8saiAGeiIyuiJaaipyF2HHpxoq_ABSHB0e5vAL2ZOrkhh8DY99wUhQORDQmKf1gRWqAJUpH4DJ2Lqzt45Op45s0pPpOUgGVU2GcfS22Yy00000__y30000)

### 2. PrintService
#### Xác định các operations
- PrintService.print: Nhận thông tin về Paycheck và Printer, thực hiện logic in.
- PaycheckPrinterImage.create: Tạo hình ảnh cần in từ Paycheck.
- PrintInterface.print: Thực hiện việc in trực tiếp trên máy in.

![Operations - PrintService](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bToJc9niK90KMPUIN1gKLbcSgf2DPS261I013KI0n8hapDIaxEj560i7ONyFB2Er28hXU0I82jTqqgXB3ypXQkM2zd4r29F496MY65gIKQgPsvYUgeLN268XsaAr4PaHN2JaejI4qjIDTAAydCntQXfXLKpL6jIQMPE2bWSBAg1i1Wb97HrxJ0yWaK5DdiSKlDIGE4B0000__y30000)

#### Xác định các trạng thái
- Ready: Chờ nhận lệnh in.
- Processing: Xử lý thông tin từ Paycheck và chuyển đổi thành PrinterImage.
- Printing: Gửi dữ liệu in đến máy in thông qua PrinterInterface.
- Complete: Hoàn thành lệnh in.

![Status - PrintService](https://www.planttext.com/api/plantuml/png/J8zD2i8m44RtESMiN0YzG1TIg0XrLUfINCHqQWVJH99OgEB9N7Wahs1-gfX52FdU-vXvFr-5TTouwo2PVpY4sf1oEpGZ2OGx0t_somDasGeQvEq4ELIA7759Dunn-Wv0RRH0QqcTFDMWG1fz8Pz4Z-8CYzIDnXTqEgf_Gl9zdkoII_dbgt1rNE3ip50mIZrS9FgnSzYG8jl3LXyZzai25ZR8OQqLiWShKBLXtmy0003__mC0)

#### Xác định các thuộc tính
- Employee: Chứa thông tin nhân viên
- Paycheck: Chứa số tiền và thông tin nhân viên
- PrinterImage: Định dạng hình ảnh cần in.

![Attributes - PrintService](https://www.planttext.com/api/plantuml/png/X54xRiCm3Drz2ex9a0juIe5qy584o0aOYN65wbDGL02ZwCawv4YvGYrNSkoYG3aHxqCzFDs_Rlieo9ASRPJ56E68WtebzGOV3Oop0tGXUMdXOWFAX04e9XJQN08_BTbjEzkBi2VvKMoswmiZyUpURHY8CbNtvhCfEIeov_3eg8MJiF5zWQXekaCBnaj1Or06xObKOYF3It9dubz6r9efnXMwojGTSgfySmvq79L2t3diQoY0Sp9MJyo4PzCr6BrmbJx-TDSQERYgUpIuA7Df_lVXFNcTl_CR003__mC0)

#### Xác định các phụ thuộc
- PrintService phụ thuộc vào IPrintService vaf PrinterInterface.
- PaycheckPrinterImage là liên kết quan trọng giữa phiếu lương và hình ảnh in.
- PrinterInterface là giao diện chính để tích hợp với các máy in.

![Dependencies - PrintService](https://www.planttext.com/api/plantuml/png/j5DBRiCW4Drp2fQELFi0g8fIALru4qNo2GWUEwXW8i2HhBOdww97wXKA57-8KtLLhuOtyzuycF7Nn-VEMAfjBmNYdGNTK0QuF6ftg41VkJkz8Xo-YmSpUgG3EmDx8NYC7h3g0WCqmPLrKRiX-AfuZTuHOe8QW_z94NGvkKvLxHbAILiWKw4_hLLYnsNHfCGqK0jPevLSUzoGk-H8FVLSr04FQFQh_QJXtwpOCJ9oJANgEqjm8nIrDxQLVbfc5uPZOGlsfy8tMYgunBEy23L0y336iuyHcNnqLC8ugWX1h2dt1BiRHTGengceWFMQs-7GozCyu_5ETQt1c0HDF9LxxyfhEaFfiZw-5KMoREZkX8jYEp_6QfFoV9lC1oKjGZRX9faRCRI3hlQ_rpS0003__mC0)

### 3. ProjectManagementDatabase
#### Xác định các operations
- getChargeNumbers(criteria: String): Tìm kiếm danh sách ChargeNumbers dựa trên tiêu chí.
- initialize(): Khởi tạo kết nối.
- ChargeNumList.add: Thêm các ChargeNum vào danh sách.

![Operations - ProjectManagementDatabase](https://www.planttext.com/api/plantuml/png/h591Ri8m4Bpx5JwcKlE1711gEHQ4XCHzYKTcAyT1zePAhNWPXpwfNsXDqnG3kU7ZpkpCxAw_Zf_JA1IaQvog7SMebw5zHIrpycJHmCkCX3OKeJ-KFZqBUTvIi5XqpGOX5dLWGM2gz4e2U_jGwO7mmb7wFlOiJ8xVKVmmzYqRTL2zw-mfaxpfTHUZZ3_OUBmL8s9aJ25R3D0PQroy5oxrxdUR2shm5xf7zkIwl7QQTldVa19TmklKTGMa-3US7dEJym5Jvl5Bb-NawYALDd2m952NKABdUwrq7P2eUJaZ9bBhXTX7DOKtwGj-0m00__y30000)

#### Xác định các trạng thái
- Ready: Sẵn sàng nhận tiêu chí tìm kiếm.
- Fetching: Nhận yêu cầu và chuẩn bị truy vấn cơ sở dữ liệu.
- Processing: Chạy truy vấn và xử lý kết quả.
- Returning: Tạo danh sách kết quả và trả về.

![Status - ProjectManagementDatabase](https://www.planttext.com/api/plantuml/png/J8z12i9034NtFKNMGY_GXHHQ1455knKNSVffHzefpAH25K_cmYDv1MVQAcOLyb_u_x-VhzG9M-dR9lABWFQskq39bWrNQ64aP-4pEz0z8Z_7nOdYU4a5k1meeRNHehdHDupoT0x02g9gRIhF553GLv2oMc0rZ-HF3x1tLN1kmWyzx43bx3l2V_faBhqr4vrPXDnPpRR2hcytsiaSvGk5bv0xeRmpY1vH2bE6oXy0003__mC0)

#### Xác định các thuộc tính
- ChargeNum: Định nghĩa thông tin cơ bản của 1 ChargeNumber.
- ChargeNumList: Danh sách các ChargeNumbers.

![Attributes - ProjectManagementDatabase](https://www.planttext.com/api/plantuml/png/h9DDJiCm48NtFiKiWqGkOA6gWYwXgeJ4VfACqa791DcJ8e4u6GkEn1MmGvhKBTdXbJNl6x_dl-_FhxLNTDgtZIaRz1vshdkcKXzGiAQMH3UeMA0dU3SGHWvLSTU918OxiJ3FPtcFhgPjtnRal8NDRL8OC82QD2bdfMCbnsZXKHrBVHNMFWBtx7NiOs5bRFYDia0SEgxCXncpdpbDYSlbl6cGVqcHy7E6oSD256ucR3MkAVIQBTXXLMMwfqawePRj9-kNtolTOal7ROtA0Pi-hGtdiPiROg9p-IbsNGWn_XzErwd9wGPZvkNdbkUhYmkrq0wWEHSYd9wx1KVQEp5fEG4359w68eitQv8g_e8V0000__y30000)

#### Xác định các phụ thuộc
- ProjectManagementDatabase phụ thuộc vào DBChargeNumbers để giao tiếp với cơ sở dữ liệu.
- ChargeNumList và ChargeNum quản lý dữ liệu trả về.
- Connection, Statement, và ResultSet đại diện cho giao tiếp cấp thấp với cơ sở dữ liệu thông qua JDBC.

![Dependencies - ProjectManagementDatabase](https://www.planttext.com/api/plantuml/png/h98z3i8m38Ntd29Z6RX01rG18o0a97QtiO9HcwBOPG1nCWQEn1LeIrKQVZOovZr_ptdA_NfBMC1BLUGgou5PhtsvnqoMuC1YWKxc8902epuhtHwBCjk1jxYgYXGzHvadGKyGwuruSdOKwzwm89PkZXm9GKudZ6h7iIIZBgfBdKy3vDUilmG5_Zu6Z8baXxquuFuc39ViMbj1qMO-rtl9MyYheL33VlSy7ay--eYrmGCwmxfqwbri1i9tnJhp28Aimll0sRXA9q2ELLApcp_m0000__y30000)
