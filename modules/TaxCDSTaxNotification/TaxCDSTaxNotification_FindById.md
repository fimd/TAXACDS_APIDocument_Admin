# Admin API - Tìm thông báo thuế theo ID

Lấy chi tiết thông báo thuế theo taxCDSTaxNotificationId.

## Endpoint

- URL: /TaxCDSTaxNotification/findById
- Method: POST

## Headers schema

| Header | Required | Mô tả |
|---|---|---|
| Authorization | Yes | Bearer staff token |

## Body schema

| Field | Type | Required | Rule | Mô tả |
|---|---|---|---|---|
| id | number | Yes | integer, min(1) | taxCDSTaxNotificationId cần tìm |

## Sample Request

```bash
curl --location 'http://127.0.0.1:4001/TaxCDSTaxNotification/findById' \
  --header 'Content-Type: application/json' \
  --header 'Authorization: Bearer <staff_token>' \
  --data '{
    "id": 1
  }'
```

## Success response

```json
{
  "statusCode": 200,
  "error": null,
  "message": "Success",
  "data": {
    "taxCDSTaxNotificationId": 1,
    "taxNotiNotificationCode": "TB001-2024-001",
    "taxNotiTitle": "Thông báo nợ thuế và chậm nộp",
    "taxNotiContent": "Nội dung thông báo...",
    "taxNotiType": "TB001",
    "taxNotiPayerTaxCode": "0312345678",
    "taxNotiPayerIdentity": "001234567890",
    "taxNotiPayerName": "Nguyen Van A",
    "taxNotiPayerPhone": "0912345678",
    "taxNotiNotificationDate": "2024-08-15",
    "createdAt": "2024-08-15T10:30:00.000Z"
  }
}
```

## Mã lỗi

| HTTP | Mã lỗi | Mô tả |
|---|---|---|
| 400 | Validation Error | Payload không đúng schema |
| 401 | UNAUTHORIZED | Thiếu hoặc sai token |
| 500 | NOT_FOUND | Không tìm thấy thông báo theo id |
| 500 | UNKNOWN_ERROR | Lỗi không xác định |

## Tham khảo

- Common auth token: ../../Common.html#admin-auth
- Common error: ../../Common.html#common-error

## Data test cho developer

- Login lấy token: POST /Staff/loginStaff
- username: string
- password: string
- id mẫu tìm kiếm: 1 (sử dụng id vừa insert trong testcase)

Cần thay bằng dữ liệu môi trường thật khi tích hợp.
