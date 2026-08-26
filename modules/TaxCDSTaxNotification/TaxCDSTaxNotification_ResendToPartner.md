# Admin API - Gửi lại thông báo đến đối tác

Gửi lại thông báo thuế đến một đối tác cụ thể.

## Endpoint

- URL: /TaxCDSTaxNotification/resendToPartner
- Method: POST

## Headers schema

| Header | Required | Mô tả |
|---|---|---|
| Authorization | Yes | Bearer staff token |

## Body schema

| Field | Type | Required | Rule | Mô tả |
|---|---|---|---|---|
| taxCDSTaxNotificationId | number | Yes | | ID của thông báo thuế cần gửi lại |
| stationId | number | Yes | | ID của trạm (đối tác) cần gửi đến |

## Sample Request

```bash
curl --location 'http://127.0.0.1:4001/TaxCDSTaxNotification/resendToPartner' \
  --header 'Content-Type: application/json' \
  --header 'Authorization: Bearer <staff_token>' \
  --data '{
    "taxCDSTaxNotificationId": 1601592,
    "stationId": 123
  }'
```

## Success response

```json
{
  "statusCode": 200,
  "error": null,
  "message": "Success",
  "data": {
    "success": true,
    "sentAt": "2024-08-26T10:30:00.000Z"
  }
}
```

## Mã lỗi

| HTTP | Mã lỗi | Mô tả |
|---|---|---|
| 400 | Validation Error | Payload không đúng schema (thiếu field bắt buộc) |
| 400 | NOTIFICATION_NOT_FOUND | Không tìm thấy thông báo với ID đã cho |
| 400 | STATION_NOT_FOUND | Không tìm thấy trạm với ID đã cho |
| 401 | UNAUTHORIZED | Thiếu hoặc sai token |
| 500 | SEND_NOTIFICATION_FAILED | Gửi thông báo thất bại |
| 500 | UNKNOWN_ERROR | Lỗi không xác định |

## Tham khảo

- Common auth token: ../../Common.html#admin-auth
- Common error: ../../Common.html#common-error

## Data test cho developer

- Login lấy token: POST /Staff/loginStaff
- username: string
- password: string
- taxCDSTaxNotificationId: 1601592
- stationId: 123

Cần thay bằng dữ liệu môi trường thật khi tích hợp.
