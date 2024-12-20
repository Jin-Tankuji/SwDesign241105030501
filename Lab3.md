# Identify design elements
## 1. Subsystem context diagrams
BankSystem:  
- PayrollController: Lớp thực hiện quy trình bảng lương bằng phương thức run payroll().
- IBankSystem: Giao diện định nghĩa phương thức deposit(aPaycheck : Paycheck, intoBack : BankInformation) để chuyển tiền trực tiếp vào ngân hàng.
- BankSystem: Hệ thống con thực hiện giao dịch ngân hàng, triển khai phương thức deposit từ IBankSystem để gửi tiền vào tài khoản nhân viên.
- Paycheck: Chứa thông tin thanh toán.
- BankInformation: Thông tin tài khoản ngân hàng của nhân viên, xác định nơi gửi tiền.

![Subsystem - BankSystem](https://www.planttext.com/api/plantuml/png/j5HBJiCm4Dtx54Ct18bS80lKZogeXAf2kO3ZJ5EhYHtvWnIXhbcpPiK9E40MB3X9Jy0LY6dpQLBOuPtVp9jvyoREL_4nr8OgOzE4d4MuuWBXVZfv6CslRwV04ger8USm-NnZaEoArmocmd2Jauoo3OqH1llx09u8bEU70GkQipMopG5qnwUfjC8444aR9jZW6SqNgBYC0bWQnKLSXo16C_fXUHSzdWikAggBjyXRqj8ofc8p4okfKcgu54UI67FLvpODKVNQ-s79dDCKJmjhSplzgvpneK1FthRZwKmOL2lAiB6rXYfdUGN0pDLTvjfWsfe68ioaviQZbVj1lOTBnvQE5dJzAAKzIXxz8cmYXL4oIL0roXgijtG7D-6sE6N58UxztN5fGxqVpRlP5SzWrhlYHSJ0IgcDXZhhMC8_6tDdgO2rKnNpNV5EWTMwINzwtxywMbK0LgCcBQIVmTCimHI5wUNLJog0J4c6-aIjxgTUTimYQih4cdqwhJJNK2xAfpv44Rb_mJS0003__mC0)

PrintService:  
- PrintController: Điều phối quá trình in.
- IPrintService: Giao diện định nghĩa phương thức print.
- PrintServiceProxy: Triển khai IPrintService, thực hiện in ấn.
- Document và PrintSettings: Thực thể chứa nội dung tài liệu và cài đặt in.
- PrinterBoundary: Lớp biên xử lý giao tiếp với máy in vật lý.

![SubSystem - PrintService](https://www.planttext.com/api/plantuml/png/h5DBJiCm4Dtx5DvH9De3H0XLK1PT82721OmpJImvTh37GFYSZ0L7uWfC4YTf4w4k88l8djzxRsRy_VcrzYWSXb8pTi8ti5C6E1R0hwn1PxK6nwKMthFsps-TChZdUsEy-Hmy1l3OUXUPbQ44WppXctWyunuGbSaz6TkeDDvFsSS4UMiGt4v8OAe_yMtCSK-ARX6q-W-qD3pusYEK56XVwauiLsMbeIb5IMtOG6M_3v5Fb_X7KeSApzzNgpd6XFerqSF86Fe1zN0z7qcpweYaIFNopag96aORuH_8YZnxIIA7LBt2f8QqsheRcytjbO9699MQjVlI1fC9Ly-N2jpWYxWUJ7PletEH2HG3KfpZ7MY1oXfVgCgpwMukbnUJnKbuQ3er7ruJEcMHa9Ao34P9WQJdMM7nI-PcdFQn-kcu0sqeMvF8vlNz0000__y30000)

ProjectManagementDatabase:
- ProjectControllerL Điều phối các hoạt động quản lý dự án.
- IProjectDatabase: Giao diện cho các thao tác cơ bản với cơ sở dữ liệu dự án.
- ProjectDatabaseProxy: Hệ thống con thực hiện các thao tác cơ sở dữ liệu, triển khai giao diện để lưu trữ và quản lý thông tin dự án.
- Project: Chứa thông tin cụ thể về 1 dự án.
- DatabaseConnection: Lớp biên cung cấp kết nối giữa hệ thống và cơ sở dữ liệu.

![Subsystem - ProjectManagementDatabase](https://www.planttext.com/api/plantuml/png/j9F1Ri8m38RlUOhS1WTu03HDQ6C7RcWyGMWDP4hSAdRPqBOdss6Fj5UOqn04BHExh8ScjVtNdntd-_DhIcm2DzufTQDdiBO8chUW7ohaK3a7GHVE4AdshHUXUeQ2JxnlIiUd260O3kv1dLOzoO9XYchgyWzH9JZeHSrBYRCeCHyTr3aoXBKfGDcyq_E3UcROh0n1nYIpWojqLx2kyooR5Us9mKVzwpxrJrjVE_20R77JXXrXprkRYPFsVx5xNRfz7uylWdHAV9GoU7zfCZ9n9rqoel4WtqiEqeHCHqMmDTiAEvvsC0KYAkAIh83bgQtR-_kgmTA4SxHSYKmj2bDCbQSsMGP3-T-kikM1oLBFqIPw0cUYdBQs9jM_2wFHNN_o9heXE4QV7syKNA2R29Zt3Tf2QYJzOddxktvnF7Tlq6mabPfAb-AL_W400F__0m00)

## 2. Analysis class to design element map  
Ánh xạ các lớp phân tích đến các phần tử thiết kế

| **Các lớp phân tích**               | **Phần tử thiết kế** |
|-------------------------------------|----------------------|
| **BankSystem**                       | - **PayrollController** (Điều phối quy trình bảng lương) |
| **PayrollController**                | - **PayrollController** (Điều phối quy trình bảng lương, gọi phương thức `runPayroll()`) |
| **IBankSystem**                      | - **IBankSystem** (Giao diện định nghĩa phương thức `deposit`) |
| **BankSystem**                       | - **BankSystem** (Thực hiện phương thức `deposit` để gửi tiền vào tài khoản ngân hàng) |
| **Paycheck**                         | - **Paycheck** (Thông tin thanh toán của nhân viên) |
| **BankInformation**                  | - **BankInformation** (Thông tin tài khoản ngân hàng của nhân viên) |
| **PrintService**                     | - **PrintController** (Điều phối quá trình in) |
| **PrintController**                  | - **PrintController** (Điều phối quá trình in và giao tiếp với `PrintServiceProxy`) |
| **IPrintService**                    | - **IPrintService** (Giao diện định nghĩa phương thức `print`) |
| **PrintServiceProxy**                | - **PrintServiceProxy** (Triển khai `IPrintService` để thực hiện in ấn) |
| **Document**                         | - **Document** (Chứa nội dung tài liệu cần in) |
| **PrintSettings**                    | - **PrintSettings** (Quản lý các cài đặt in) |
| **PrinterBoundary**                  | - **PrinterBoundary** (Lớp biên giao tiếp với máy in vật lý) |
| **ProjectManagementDatabase**        | - **ProjectController** (Điều phối các hoạt động quản lý dự án) |
| **ProjectController**                | - **ProjectController** (Quản lý các yêu cầu liên quan đến dự án và điều phối với cơ sở dữ liệu) |
| **IProjectDatabase**                 | - **IProjectDatabase** (Giao diện định nghĩa các thao tác cơ sở dữ liệu) |
| **ProjectDatabaseProxy**             | - **ProjectDatabaseProxy** (Triển khai các thao tác cơ sở dữ liệu với thêm bảo mật hoặc cache) |
| **Project**                          | - **Project** (Thông tin chi tiết về dự án) |
| **DatabaseConnection**               | - **DatabaseConnection** (Cung cấp kết nối cơ sở dữ liệu) |

## 3. Design element to owning package map
Ánh xạ các phần tử thiết kế vào các gói

| **Phần tử thiết kế**               | **Gói (Package)**             |
|------------------------------------|-------------------------------|
| **PayrollController**              | `com.bank.payroll`            |
| **IBankSystem**                    | `com.bank.system`             |
| **BankSystem**                     | `com.bank.system`             |
| **Paycheck**                       | `com.bank.model`              |
| **BankInformation**                | `com.bank.model`              |
| **PrintController**                | `com.print.controller`        |
| **IPrintService**                  | `com.print.service`           |
| **PrintServiceProxy**              | `com.print.service`           |
| **Document**                       | `com.print.model`             |
| **PrintSettings**                  | `com.print.model`             |
| **PrinterBoundary**                | `com.print.boundary`          |
| **ProjectController**              | `com.project.controller`      |
| **IProjectDatabase**               | `com.project.database`        |
| **ProjectDatabaseProxy**           | `com.project.database`        |
| **Project**                        | `com.project.model`           |
| **DatabaseConnection**             | `com.project.database`        |

## 4. MVC Components and their Dependencies
Biểu đồ mô tả các component MVC trong hệ thống và quan hệ giữa chúng

![MVC Component - BankSystem](https://www.planttext.com/api/plantuml/png/V5GxJiCm6Dvp2jE5gJb01rHQggeIGa2vWElyRKrZEx8TH8IOEGGJ9s1WxC3Ga_G4N87OITJu0LcY_D_ZVpd-sN-FbSPIbonFpZ9OKmxeVZPzkBoPNyyGoR5IINAEveSlYeXWwGhpNSf41dbIOBB36q03Dpv0Bmcg7wj5jxWYMo2xNcXIKnTyBIJ3cWhU9qln24Jt8bU2b0ouTaYKwoLeJVb6zQbOunLMC1MSroR6-JKilS2L57ci-1O9oZV1sbERDqZFip35f0ha4oNWcZfGvrg7GAun0RHe-sYKGNisNC_ZkOfcN8cIPrXMiPGTvdKYRUv99_HTxUHJSchKS_PntztY_yofqMVjakBk7HgTbgLqImvJTqXiPdQ_gb8QM6Jn3H39QGxgib6vfxSDsYHt9UPeUzo_eGqzxZyn8eSFWlBZ_hr8WjE3XiCBT_DeX4e5AWdM7gLILkHW_WSZy2RU2PnfdEp38Vqbw2KvDTkGUzzUCSxXikImev5P1Yiv9LZNDOK_RAkBb6gabbNVHcFWcRckVW400F__0m00)
