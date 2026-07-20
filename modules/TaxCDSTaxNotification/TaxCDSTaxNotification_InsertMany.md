# Admin API - Insert many thong bao thue

Them nhieu thong bao thue vao he thong trong mot lan goi API.

## Endpoint

- URL: /TaxCDSTaxNotification/insertMany
- Method: POST

## Headers schema

| Header | Required | Mo ta |
|---|---|---|
| Authorization | Yes | Bearer staff token |

## Body schema

| Field | Type | Required | Rule | Mo ta |
|---|---|---|---|---|
| data | array<object> | Yes | min(1) | Danh sach thong bao can insert |
| data[].taxNotiNotificationCode | string | No | allow('', null) | Ma thong bao |
| data[].taxNotiTitle | string | No | allow('', null) | Tieu de thong bao |
| data[].taxNotiContent | string | No | allow('', null) | Noi dung thong bao |
| data[].taxNotiMetadata | string | No | allow('', null) | Metadata dang chuoi JSON |
| data[].taxNotiDocumentCode | string | No | allow('', null) | Ma van ban |
| data[].taxNotiDocumentTitle | string | No | allow('', null) | Tieu de van ban |
| data[].taxNotiPayerIdentity | string | No | allow('', null) | CCCD/CMND nguoi nop thue |
| data[].taxNotiPayerTaxCode | string | No | allow('', null) | Ma so thue nguoi nop thue |
| data[].taxNotiPayerPhone | string | No | allow('', null) | So dien thoai nguoi nop thue |
| data[].taxNotiPayerEmail | string | No | allow('', null) | Email nguoi nop thue |
| data[].taxNotiPayerName | string | No | allow('', null) | Ten nguoi nop thue |
| data[].taxNotiNotificationDate | string | No | allow('', null) | Thoi diem thong bao |
| data[].taxNotiPICUnit | string | No | allow('', null) | Don vi phu trach |
| data[].taxNotiPICName | string | No | allow('', null) | Nguoi phu trach |
| data[].taxNotiPICAddress | string | No | allow('', null) | Dia chi don vi phu trach |
| data[].taxNotiPICPhone | string | No | allow('', null) | So dien thoai don vi phu trach |
| data[].taxNotiPICEmail | string | No | allow('', null) | Email don vi phu trach |

## Sample Request

curl --location 'http://127.0.0.1:4001/TaxCDSTaxNotification/insertMany' \
  --header 'Content-Type: application/json' \
  --header 'Authorization: Bearer <staff_token>' \
  --data '{
    "data": [
      {
        "taxNotiNotificationCode": "TAXCDS-NOTI-DEBT-001",
        "taxNotiTitle": "Thong bao no thue va cham nop",
        "taxNotiPayerTaxCode": "0312345678"
      }
    ]
  }'

## Success response

{
  "statusCode": 200,
  "error": null,
  "message": "Success",
  "data": true
}

## Ma loi

| HTTP | Ma loi | Mo ta |
|---|---|---|
| 400 | Validation Error | Payload khong dung schema |
| 401 | UNAUTHORIZED | Thieu hoac sai token |
| 500 | INSERT_FAILED | Insert du lieu that bai |
| 500 | UNKNOWN_ERROR | Loi khong xac dinh |

## Tham khao

- Common auth token: ../../Common.html#admin-auth
- Common error: ../../Common.html#common-error

## Data test cho developer

- Login lay token: POST /Staff/loginStaff
- username: string
- password: string
- taxNotiNotificationCode: TAXCDS-NOTI-DEBT-001
- taxNotiPayerTaxCode: 0312345678

Can thay bang du lieu moi truong that khi tich hop.
