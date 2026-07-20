# Admin API - Tim danh sach thong bao thue

Tim kiem danh sach thong bao thue theo bo loc, searchText va phan trang.

## Endpoint

- URL: /TaxCDSTaxNotification/find
- Method: POST

## Headers schema

| Header | Required | Mo ta |
|---|---|---|
| Authorization | Yes | Bearer staff token |

## Body schema

| Field | Type | Required | Rule | Mo ta |
|---|---|---|---|---|
| filter | object | No | default {} | Bo loc tim kiem |
| filter.taxNotiNotificationCode | string | No | allow('') | Loc theo ma thong bao |
| filter.taxNotiPayerTaxCode | string | No | allow('') | Loc theo ma so thue |
| filter.taxNotiPayerIdentity | string | No | allow('') | Loc theo CCCD/CMND |
| filter.taxNotiPayerName | string | No | allow('') | Loc theo ten nguoi nop thue |
| filter.taxNotiDocumentCode | string | No | allow('') | Loc theo ma van ban |
| filter.taxNotiDocumentTitle | string | No | allow('') | Loc theo tieu de van ban |
| searchText | string | No | default '' | Chuoi tim kiem tong quat |
| skip | number | No | min(0), default 0 | So ban ghi bo qua |
| limit | number | No | max(100), default 20 | So ban ghi toi da tra ve |
| order.key | string | No | default createdAt | Truong sap xep |
| order.value | string | No | default desc | Chieu sap xep |

## Sample Request

curl --location 'http://127.0.0.1:4001/TaxCDSTaxNotification/find' \
  --header 'Content-Type: application/json' \
  --header 'Authorization: Bearer <staff_token>' \
  --data '{
    "filter": {
      "taxNotiPayerTaxCode": "0312345678"
    },
    "searchText": "",
    "skip": 0,
    "limit": 20,
    "order": {
      "key": "createdAt",
      "value": "desc"
    }
  }'

## Success response

{
  "statusCode": 200,
  "error": null,
  "message": "Success",
  "data": {
    "data": [
      {
        "taxCDSTaxNotificationId": 1,
        "taxNotiNotificationCode": "TAXCDS-NOTI-DEBT-001",
        "taxNotiTitle": "Thong bao no thue va cham nop",
        "taxNotiPayerTaxCode": "0312345678"
      }
    ],
    "totalNextPage": 0
  }
}

## Ma loi

| HTTP | Ma loi | Mo ta |
|---|---|---|
| 400 | Validation Error | Payload khong dung schema |
| 401 | UNAUTHORIZED | Thieu hoac sai token |
| 500 | UNKNOWN_ERROR | Loi khong xac dinh |

## Tham khao

- Common auth token: ../../Common.html#admin-auth
- Common error: ../../Common.html#common-error

## Data test cho developer

- Login lay token: POST /Staff/loginStaff
- username: string
- password: string
- taxNotiPayerTaxCode: 0312345678

Can thay bang du lieu moi truong that khi tich hop.
