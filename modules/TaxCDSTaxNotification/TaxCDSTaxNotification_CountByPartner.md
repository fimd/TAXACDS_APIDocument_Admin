# Admin API - Đếm thống kê theo đối tác

Đếm và thống kê số lượng thông báo thuế theo từng đối tác (trạm).

## Endpoint

- URL: /TaxCDSTaxNotification/countByPartner
- Method: POST

## Headers schema

| Header | Required | Mô tả |
|---|---|---|
| Authorization | Yes | Bearer staff token |

## Body schema

| Field | Type | Required | Rule | Mô tả |
|---|---|---|---|---|
| filter | object | No | default {} | Bộ lọc tìm kiếm |
| filter.stationId | number/array | No | | Lọc theo ID trạm (một hoặc nhiều) |
| filter.taxCDSTaxNotificationId | number | No | | Lọc theo ID thông báo thuế |
| filter.lastReceivingStatus | string | No | | Lọc theo trạng thái nhận cuối |
| filter.lastFeedbackStatus | string | No | | Lọc theo trạng thái phản hồi cuối |
| skip | number | No | min(0), default 0 | Số bản ghi bỏ qua |
| limit | number | No | max(100), default 20 | Số bản ghi tối đa trả về |

## Sample Request

```bash
curl --location 'http://127.0.0.1:4001/TaxCDSTaxNotification/countByPartner' \
  --header 'Content-Type: application/json' \
  --header 'Authorization: Bearer <staff_token>' \
  --data '{
    "filter": {
      "stationId": [123, 456],
      "lastReceivingStatus": "SUCCESS"
    },
    "skip": 0,
    "limit": 20
  }'
```

## Success response

```json
{
  "statusCode": 200,
  "error": null,
  "message": "Success",
  "data": {
    "data": [
      {
        "stationId": 123,
        "stationsName": "Trạm A",
        "totalNotifications": 150,
        "receivedSuccess": 120,
        "feedbackSuccess": 100
      }
    ],
    "total": 5
  }
}
```

## Mã lỗi

| HTTP | Mã lỗi | Mô tả |
|---|---|---|
| 400 | Validation Error | Payload không đúng schema |
| 401 | UNAUTHORIZED | Thiếu hoặc sai token |
| 500 | UNKNOWN_ERROR | Lỗi không xác định |

## Tham khảo

- Common auth token: ../../Common.html#admin-auth
- Common error: ../../Common.html#common-error

## Data test cho developer

- Login lấy token: POST /Staff/loginStaff
- username: string
- password: string
- stationId: 123

Cần thay bằng dữ liệu môi trường thật khi tích hợp.