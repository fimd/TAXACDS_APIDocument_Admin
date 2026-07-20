# Admin API Module: TaxCDSTaxNotification

Cac API quan ly va tra cuu thong bao thue cho he thong Admin.

[Quay ve trang chu](../../index.html)

## Danh sach API

### 1. Insert many thong bao thue

Endpoint:

POST /TaxCDSTaxNotification/insertMany

Tai lieu:

- HTML: ./TaxCDSTaxNotification_InsertMany.html
- MD: ./TaxCDSTaxNotification_InsertMany.md

### 2. Tim danh sach thong bao thue

Endpoint:

POST /TaxCDSTaxNotification/find

Tai lieu:

- HTML: ./TaxCDSTaxNotification_Find.html
- MD: ./TaxCDSTaxNotification_Find.md

### 3. Tim thong bao thue theo id

Endpoint:

POST /TaxCDSTaxNotification/findById

Tai lieu:

- HTML: ./TaxCDSTaxNotification_FindById.html
- MD: ./TaxCDSTaxNotification_FindById.md

## Header chung

- Authorization: Bearer staff token

## Token flow

- Dang nhap staff qua POST /Staff/loginStaff voi username/password.
- Lay data.token tu response.
- Truyen Authorization: Bearer token cho API.

## Data test tham chieu

- username: string
- password: string
- taxNotiNotificationCode: TAXCDS-NOTI-DEBT-001
- taxNotiPayerTaxCode: 0312345678

Can thay bang du lieu moi truong that khi tich hop.
