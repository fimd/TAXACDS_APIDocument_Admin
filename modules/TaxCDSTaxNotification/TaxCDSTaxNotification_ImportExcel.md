# Admin API - Import thông báo thuế từ Excel

Import danh sách thông báo thuế từ file Excel.

## Endpoint

- URL: /TaxCDSTaxNotification/importExcel
- Method: POST

## Headers schema

| Header | Required | Mô tả |
|---|---|---|
| Authorization | Yes | Bearer staff token |

## Body schema

| Field | Type | Required | Rule | Mô tả |
|---|---|---|---|---|
| file | binary | Yes | base64 encoded | File Excel được mã hóa base64 |
| fileFormat | string | Yes | valid(['xlsx', 'xls']) | Định dạng file Excel |

## Sample Request

```bash
curl --location 'http://127.0.0.1:4001/TaxCDSTaxNotification/importExcel' \
  --header 'Content-Type: application/json' \
  --header 'Authorization: Bearer <staff_token>' \
  --data '{
    "file": "UEsDBBQABgAIAAAAIQBi7p1o...",
    "fileFormat": "xlsx"
  }'
```

## Success response

```json
{
  "statusCode": 200,
  "error": null,
  "message": "Success",
  "data": {
    "success": 50,
    "failed": 2,
    "total": 52
  }
}
```

## Mã lỗi

| HTTP | Mã lỗi | Mô tả |
|---|---|---|
| 400 | Validation Error | Payload không đúng schema (thiếu file, sai fileFormat) |
| 400 | INVALID_FILE_FORMAT | File không đúng định dạng Excel |
| 400 | FILE_TOO_LARGE | File vượt quá 20MB |
| 401 | UNAUTHORIZED | Thiếu hoặc sai token |
| 500 | UNKNOWN_ERROR | Lỗi không xác định |

## Tham khảo

- Common auth token: ../../Common.html#admin-auth
- Common error: ../../Common.html#common-error

## Data test cho developer

- Login lấy token: POST /Staff/loginStaff
- username: string
- password: string
- Tải file mẫu Excel tại: /templates/tax_notification_template.xlsx

Cần thay bằng dữ liệu môi trường thật khi tích hợp.
