# Admin API - Đối tác tra cứu thông báo thuế

API cho phép đối tác tra cứu thông báo thuế theo CCCD, số điện thoại và tên người nộp thuế.

## Endpoint

- URL: /TaxCDSTaxNotification/partner/lookupTaxNotification
- Method: POST

## Headers schema

| Header | Required | Mô tả |
|---|---|---|
| apikey | Yes | Khóa xác thực API của đối tác |

## Body schema

| Field | Type | Required | Rule | Mô tả |
|---|---|---|---|---|
| filter | object | Yes | | Bộ lọc tìm kiếm |
| filter.citizenIdentityNumber | string | Yes | trim() | Số CCCD/CMND |
| filter.phoneNumber | string | Yes | trim() | Số điện thoại |
| filter.taxpayerName | string | Yes | trim() | Tên người nộp thuế |
| skip | number | No | min(0), default 0 | Số bản ghi bỏ qua |
| limit | number | No | min(1), max(100), default 20 | Số bản ghi tối đa trả về |
| startDate | string | No | allow('', null) | Ngày bắt đầu lọc |
| endDate | string | No | allow('', null) | Ngày kết thúc lọc |
| order | object | No | | Sắp xếp kết quả |
| order.key | string | No | default 'createdAt' | Trường sắp xếp |
| order.value | string | No | valid('asc', 'desc'), default 'desc' | Chiều sắp xếp |

## Sample Request

```bash
curl --location 'http://127.0.0.1:4001/TaxCDSTaxNotification/partner/lookupTaxNotification' \
  --header 'Content-Type: application/json' \
  --header 'apikey: PARTNER_API_KEY_123' \
  --data '{
    "filter": {
      "citizenIdentityNumber": "001234567890",
      "phoneNumber": "0912345678",
      "taxpayerName": "Nguyen Van A"
    },
    "skip": 0,
    "limit": 20,
    "startDate": "2024-01-01",
    "endDate": "2024-12-31",
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
        "taxCDSTaxNotificationId": 1601592,
        "taxNotiNotificationCode": "TB001-2024-001",
        "taxNotiTitle": "Thông báo nợ thuế",
        "taxNotiContent": "Nội dung thông báo...",
        "taxNotiNotificationDate": "2024-08-15",
        "taxNotiType": "TB001",
        "taxNotiPayerName": "Nguyen Van A",
        "taxNotiPayerIdentity": "001234567890",
        "taxNotiPayerPhone": "0912345678"
      }
    ],
    "total": 5
  }
}
```

## Mã lỗi

| HTTP | Mã lỗi | Mô tả |
|---|---|---|
| 400 | Validation Error | Payload không đúng schema (thiếu field bắt buộc, sai kiểu) |
| 401 | UNAUTHORIZED | Thiếu hoặc sai apikey |
| 500 | UNKNOWN_ERROR | Lỗi không xác định |

## Tham khảo

- Common error: ../../Common.html#common-error

## Data test cho developer

- apikey: PARTNER_API_KEY_123
- citizenIdentityNumber: 001234567890
- phoneNumber: 0912345678
- taxpayerName: Nguyen Van A

Cần thay bằng dữ liệu môi trường thật khi tích hợp.
