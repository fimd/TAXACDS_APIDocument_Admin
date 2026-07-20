# Admin API Documentation - TaxCDSTaxNotification

Tai lieu API Admin cho module TaxCDSTaxNotification.

## Danh sach module

1. TaxCDSTaxNotification
- Module index HTML: ./modules/TaxCDSTaxNotification/index.html
- Module index MD: ./modules/TaxCDSTaxNotification/index.md

## Danh sach API

1. Insert many thong bao thue
- Endpoint: POST /TaxCDSTaxNotification/insertMany
- HTML: ./modules/TaxCDSTaxNotification/TaxCDSTaxNotification_InsertMany.html
- MD: ./modules/TaxCDSTaxNotification/TaxCDSTaxNotification_InsertMany.md

2. Tim danh sach thong bao thue
- Endpoint: POST /TaxCDSTaxNotification/find
- HTML: ./modules/TaxCDSTaxNotification/TaxCDSTaxNotification_Find.html
- MD: ./modules/TaxCDSTaxNotification/TaxCDSTaxNotification_Find.md

3. Tim thong bao thue theo id
- Endpoint: POST /TaxCDSTaxNotification/findById
- HTML: ./modules/TaxCDSTaxNotification/TaxCDSTaxNotification_FindById.html
- MD: ./modules/TaxCDSTaxNotification/TaxCDSTaxNotification_FindById.md

## Huong dan token (bat buoc)

- Buoc 1: Goi POST /Staff/loginStaff voi payload username/password.
- Buoc 2: Lay data.token tu response.
- Buoc 3: Truyen header Authorization: Bearer token cho cac API TaxCDSTaxNotification.

## Data test tham chieu

- username staff test: string
- password staff test: string
- taxNotiNotificationCode mau: TAXCDS-NOTI-DEBT-001
- taxNotiPayerTaxCode mau: 0312345678

Can thay bang du lieu moi truong that khi tich hop.
