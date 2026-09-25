---
title: Печать акта приемки
api: uzum-seller
method: GET
path: /v1/fbs/invoice/{invoiceId}/closing-documents
operation_id: getFbsInvoiceClosingDocuments
tags:
  - FBS Invoice
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 4d4eaebd777ed0cb
---

# Печать акта приемки

`GET /v1/fbs/invoice/{invoiceId}/closing-documents`

Печать акта приемки

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `invoiceId` | path | integer<int64> | да | Идентификатор накладной |

## Ответы

**400** — Коды ошибок: seller-order-19 - Накладная не найдена seller-order-16 - Неподходящий статус накладной

- `payload` — object. Response payload
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string

**403** — fbs-2-seller-access-denied - У продавца нет доступа

- `payload` — object. Response payload
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string

**200** — Success

- `payload` — object. Document
  - `document` — string<byte> **обязательный**. Накладная в pdf в Base64
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string
