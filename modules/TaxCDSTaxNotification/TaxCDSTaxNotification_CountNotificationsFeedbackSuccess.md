# Admin API - Đếm thông báo phản hồi thành công

Đếm số lượng thông báo thuế đã được người dùng phản hồi thành công.

## Endpoint

- URL: /TaxCDSTaxNotification/countNotificationsFeedbackSuccess
- Method: POST

## Headers schema

| Header | Required | Mô tả |
|---|---|---|
| Authorization | Yes | Bearer staff token |

## Body schema

| Field | Type | Required | Rule | Mô tả |
|---|---|---|---|---|
| - | - | - | - | Không có tham số |

## Sample Request

```bash
curl --location 'http://127.0.0.1:4001/TaxCDSTaxNotification/countNotificationsFeedbackSuccess' \
  --header 'Content-Type: application/json' \
  --header 'Authorization: Bearer <staff_token>' \
  --data '{}'
```

## Success response

```json
{
  "statusCode": 200,
  "error": null,
  "message": "Success",
  "data": {
    "total": 9876
  }
}
```

## Mã lỗi

| HTTP | Mã lỗi | Mô tả |
|---|---|---|
| 401 | UNAUTHORIZED | Thiếu hoặc sai token |
| 500 | UNKNOWN_ERROR | Lỗi không xác định |

## Tham khảo

- Common auth token: ../../Common.html#admin-auth
- Common error: ../../Common.html#common-error

## Data test cho developer

- Login lấy token: POST /Staff/loginStaff
- username: string
- password: string

Cần thay bằng dữ liệu môi trường thật khi tích hợp.
