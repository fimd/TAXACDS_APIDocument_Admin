# Admin API Module: TaxCDSTaxNotification

Các API quản lý và tra cứu thông báo thuế cho hệ thống Admin.

[Quay về trang chủ](../../index.html)

## Danh sách API

### 1. Tìm danh sách thông báo thuế

Endpoint: POST /TaxCDSTaxNotification/find

Tài liệu:
- HTML: ./TaxCDSTaxNotification_Find.html
- MD: ./TaxCDSTaxNotification_Find.md

### 2. Thêm nhiều thông báo thuế

Endpoint: POST /TaxCDSTaxNotification/insertMany

Tài liệu:
- HTML: ./TaxCDSTaxNotification_InsertMany.html
- MD: ./TaxCDSTaxNotification_InsertMany.md

### 3. Import thông báo thuế từ Excel

Endpoint: POST /TaxCDSTaxNotification/importExcel

Tài liệu:
- HTML: ./TaxCDSTaxNotification_ImportExcel.html
- MD: ./TaxCDSTaxNotification_ImportExcel.md

### 4. Tìm thông báo thuế theo ID

Endpoint: POST /TaxCDSTaxNotification/findById

Tài liệu:
- HTML: ./TaxCDSTaxNotification_FindById.html
- MD: ./TaxCDSTaxNotification_FindById.md

### 5. Đếm thống kê theo đối tác

Endpoint: POST /TaxCDSTaxNotification/countByPartner

Tài liệu:
- HTML: ./TaxCDSTaxNotification_CountByPartner.html
- MD: ./TaxCDSTaxNotification_CountByPartner.md

### 6. Đếm tổng số thông báo thuế

Endpoint: POST /TaxCDSTaxNotification/countTotalNotifications

Tài liệu:
- HTML: ./TaxCDSTaxNotification_CountTotalNotifications.html
- MD: ./TaxCDSTaxNotification_CountTotalNotifications.md

### 7. Đếm thông báo đang gửi đến đối tác

Endpoint: POST /TaxCDSTaxNotification/countNotificationsSendingToPartner

Tài liệu:
- HTML: ./TaxCDSTaxNotification_CountNotificationsSendingToPartner.html
- MD: ./TaxCDSTaxNotification_CountNotificationsSendingToPartner.md

### 8. Đếm thông báo đối tác nhận thành công

Endpoint: POST /TaxCDSTaxNotification/countNotificationsPartnerReceivedSuccess

Tài liệu:
- HTML: ./TaxCDSTaxNotification_CountNotificationsPartnerReceivedSuccess.html
- MD: ./TaxCDSTaxNotification_CountNotificationsPartnerReceivedSuccess.md

### 9. Đếm thông báo phản hồi thành công

Endpoint: POST /TaxCDSTaxNotification/countNotificationsFeedbackSuccess

Tài liệu:
- HTML: ./TaxCDSTaxNotification_CountNotificationsFeedbackSuccess.html
- MD: ./TaxCDSTaxNotification_CountNotificationsFeedbackSuccess.md

### 10. Đối tác tra cứu thông báo thuế

Endpoint: POST /TaxCDSTaxNotification/partner/lookupTaxNotification

Tài liệu:
- HTML: ./TaxCDSTaxNotification_PartnerLookupTaxNotification.html
- MD: ./TaxCDSTaxNotification_PartnerLookupTaxNotification.md

### 11. Gửi lại thông báo đến đối tác

Endpoint: POST /TaxCDSTaxNotification/resendToPartner

Tài liệu:
- HTML: ./TaxCDSTaxNotification_ResendToPartner.html
- MD: ./TaxCDSTaxNotification_ResendToPartner.md

## Header chung

- Authorization: Bearer staff token (cho các API admin)
- apikey: API key của đối tác (cho API partner/lookupTaxNotification)

## Token flow

- Đăng nhập staff qua POST /Staff/loginStaff với username/password.
- Lấy data.token từ response.
- Truyền Authorization: Bearer token cho API.

## Data test tham chiếu

- username: string
- password: string
- taxNotiNotificationCode: TAXCDS-NOTI-DEBT-001
- taxNotiPayerTaxCode: 0312345678
- apikey: PARTNER_API_KEY_123

Cần thay bằng dữ liệu môi trường thật khi tích hợp.
