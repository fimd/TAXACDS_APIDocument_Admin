# Admin API - Tim thong bao thue theo id

Lay chi tiet thong bao thue theo taxCDSTaxNotificationId.

## Endpoint

- URL: /TaxCDSTaxNotification/findById
- Method: POST

## Headers schema

| Header | Required | Mo ta |
|---|---|---|
| Authorization | Yes | Bearer staff token |

## Body schema

| Field | Type | Required | Rule | Mo ta |
|---|---|---|---|---|
| id | number | Yes | integer, min(1) | taxCDSTaxNotificationId can tim |

## Sample Request

curl --location 'http://127.0.0.1:4001/TaxCDSTaxNotification/findById' \
  --header 'Content-Type: application/json' \
  --header 'Authorization: Bearer <staff_token>' \
  --data '{
    "id": 1
  }'

## Success response

{
  "statusCode": 200,
  "error": null,
  "message": "Success",
  "data": {
    "taxCDSTaxNotificationId": 1,
    "taxNotiNotificationCode": "TAXCDS-NOTI-DEBT-001",
    "taxNotiTitle": "Thong bao no thue va cham nop",
    "taxNotiPayerTaxCode": "0312345678"
  }
}

## Ma loi

| HTTP | Ma loi | Mo ta |
|---|---|---|
| 400 | Validation Error | Payload khong dung schema |
| 401 | UNAUTHORIZED | Thieu hoac sai token |
| 500 | NOT_FOUND | Khong tim thay thong bao theo id |
| 500 | UNKNOWN_ERROR | Loi khong xac dinh |

## Tham khao

- Common auth token: ../../Common.html#admin-auth
- Common error: ../../Common.html#common-error

## Data test cho developer

- Login lay token: POST /Staff/loginStaff
- username: string
- password: string
- id mau tim kiem: 1 (su dung id vua insert trong testcase)

Can thay bang du lieu moi truong that khi tich hop.
