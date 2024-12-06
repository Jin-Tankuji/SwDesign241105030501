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
![Attribute - BankSystem](https://www.planttext.com/api/plantuml/png/V54n3i8m3Dpp2ezKeX_8W029WGMGu0Cck81eaYfrXmhnCWQUn1TeInkQ8iWK-yxdi_syFwOve-D2fqAbcEUmmLATI5tWAg1wCQ2sXM49IMgHcno0SeHCeyIwMH-Df2zlYKVYDsCKXGeLiD1PQakY6kh-uYPQ7tCqbwMfEcZaipNUZa5D4hRipkROffmjk8fMXTwJyrYWj7DeSbI1qlTWCV27jyx8DQrbe-33lqs3zTXiK3eEUuvx8fr298T-wq7yKU9uyjdLSB0Q3At-OlGMAwPa3lNvNm000F__0m00)
#### Xác định các phụ thuộc
![Dependencies - BankSystem](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTcNabgKLfYSgg2frDYNdPmPN59QYvNSavYSR427W5Fc3QeJ41YPN96Qd8saiAGeiIyuiJaaipyF2HHpxoq_ABSHB0e5vAL2ZOrkhh8DY99wUhQORDQmKf1gRWqAJUpH4DJ2Lqzt45Op45s0pPpOUgGVU2GcfS22Yy00000__y30000)
