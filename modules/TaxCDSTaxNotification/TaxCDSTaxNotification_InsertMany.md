# Admin API - Thêm nhiều thông báo thuế

Thêm nhiều thông báo thuế vào hệ thống trong một lần gọi API.

## Endpoint

- URL: /TaxCDSTaxNotification/insertMany
- Method: POST

## Headers schema

| Header | Required | Mô tả |
|---|---|---|
| Authorization | Yes | Bearer staff token |

## Body schema

| Field | Type | Required | Rule | Mô tả |
|---|---|---|---|---|
| data | array<object> | Yes | min(1) | Danh sách thông báo cần insert |
| data[].taxNotiNotificationCode | string | No | allow('', null) | Mã thông báo |
| data[].taxNotiTitle | string | No | allow('', null) | Tiêu đề thông báo |
| data[].taxNotiContent | string | No | allow('', null) | Nội dung thông báo |
| data[].taxNotiMetadata | string | No | allow('', null) | Metadata dạng chuỗi JSON |
| data[].taxNotiDocumentCode | string | No | allow('', null) | Mã văn bản |
| data[].taxNotiDocumentTitle | string | No | allow('', null) | Tiêu đề văn bản |
| data[].taxNotiPayerIdentity | string | No | allow('', null) | CCCD/CMND người nộp thuế |
| data[].taxNotiPayerTaxCode | string | No | allow('', null) | Mã số thuế người nộp thuế |
| data[].taxNotiPayerPhone | string | No | allow('', null) | Số điện thoại người nộp thuế |
| data[].taxNotiPayerEmail | string | No | allow('', null) | Email người nộp thuế |
| data[].taxNotiPayerName | string | No | allow('', null) | Tên người nộp thuế |
| data[].taxNotiNotificationDate | string | No | allow('', null) | Thời điểm thông báo |
| data[].taxNotiIssuingAuthority | string | No | allow('', null) | Cơ quan thuế ban hành thông báo |
| data[].taxNotiTaxPeriod | string | No | allow('', null) | Kỳ thuế |
| data[].taxNotiGuidanceAuthority | string | No | allow('', null) | Cơ quan thuế hướng dẫn |
| data[].taxNotiPICUnit | string | No | allow('', null) | Đơn vị phụ trách |
| data[].taxNotiPICName | string | No | allow('', null) | Người phụ trách |
| data[].taxNotiPICAddress | string | No | allow('', null) | Địa chỉ đơn vị phụ trách |
| data[].taxNotiPICPhone | string | No | allow('', null) | Số điện thoại đơn vị phụ trách |
| data[].taxNotiPICEmail | string | No | allow('', null) | Email đơn vị phụ trách |
| data[].taxNotiDataClosingTime | string | No | allow('', null) | Thời điểm chốt dữ liệu |
| data[].taxNotiType | string | Yes | valid(['TB001', 'TB002', 'TB003', 'TB004', 'TB005', 'TB006', 'TB007', 'TB008']) | Loại thông báo |

## Sample Request

```bash
curl --location 'http://127.0.0.1:4001/TaxCDSTaxNotification/insertMany' \
  --header 'Content-Type: application/json' \
  --header 'Authorization: Bearer <staff_token>' \
  --data '{
    "data": [
      {
        "taxNotiNotificationCode": "TB001-2024-001",
        "taxNotiTitle": "Thông báo nợ thuế và chậm nộp",
        "taxNotiContent": "Nội dung thông báo...",
        "taxNotiPayerTaxCode": "0312345678",
        "taxNotiPayerIdentity": "001234567890",
        "taxNotiPayerName": "Nguyen Van A",
        "taxNotiPayerPhone": "0912345678",
        "taxNotiNotificationDate": "2024-08-15",
        "taxNotiType": "TB001"
      }
    ]
  }'
```

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
