# Admin API - Tìm danh sách thông báo thuế

Tìm kiếm danh sách thông báo thuế theo bộ lọc, searchText và phân trang.

## Endpoint

- URL: /TaxCDSTaxNotification/find
- Method: POST

## Headers schema

| Header | Required | Mô tả |
|---|---|---|
| Authorization | Yes | Bearer staff token |

## Body schema

| Field | Type | Required | Rule | Mô tả |
|---|---|---|---|---|
| filter | object | No | default  | Bộ lọc tìm kiếm |
| filter.taxNotiType | string | No | | Lọc theo loại thông báo (TB001-TB008) |
| filter.taxNotiNotificationDate | array | No | items(string) | Lọc theo khoảng ngày thông báo ['2023-01-01', '2023-12-31'] |
| startDate | string | No | | Ngày bắt đầu lọc |
| endDate | string | No | | Ngày kết thúc lọc |
| searchText | string | No | default '' | Chuỗi tìm kiếm tổng quát |
| skip | number | No | min(0), default 0 | Số bản ghi bỏ qua |
| limit | number | No | max(100), default 20 | Số bản ghi tối đa trả về |
| order.key | string | No | default createdAt | Trường sắp xếp |
| order.value | string | No | default desc | Chiều sắp xếp |

## Sample Request

```bash
curl --location 'http://127.0.0.1:4001/TaxCDSTaxNotification/find' \
  --header 'Content-Type: application/json' \
  --header 'Authorization: Bearer <staff_token>' \
  --data '{
    "filter": {
      "taxNotiType": "TB001",
      "taxNotiNotificationDate": ["2024-01-01", "2024-12-31"]
    },
    "searchText": "Nguyen Van A",
    "skip": 0,
    "limit": 20,
    "order": {
      "key": "createdAt",
      "value": "desc"
    }
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
        "taxCDSTaxNotificationId": 1,
        "taxNotiNotificationCode": "TB001-2024-001",
        "taxNotiTitle": "Thông báo nợ thuế và chậm nộp",
        "taxNotiType": "TB001",
        "taxNotiPayerTaxCode": "0312345678",
        "taxNotiPayerName": "Nguyen Van A",
        "taxNotiNotificationDate": "2024-08-15",
        "createdAt": "2024-08-15T10:30:00.000Z"
      }
    ],
    "total": 1
  }
}
```

## Mã lỗi

| HTTP | Mã lỗi | Mô tả |
|---|---|---|
| 400 | Validation Error | Payload không đúng schema |
| 401 | UNAUTHORIZED | Thiếu hoặc sai token |
| 500 | UNKNOWN_ERROR | Lỗi không xác định |

## Tham khao

- Common auth token: ../../Common.html#admin-auth
- Common error: ../../Common.html#common-error

## Data test cho developer

- Login lấy token: POST /Staff/loginStaff
- username: string
- password: string
- taxNotiType: TB001

Cần thay bằng dữ liệu môi trường thật khi tích hợp.
