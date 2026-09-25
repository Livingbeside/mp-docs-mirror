---
title: Отмена накладной
api: uzum-seller
method: POST
path: /v1/fbs/invoice/{invoiceId}/cancel
operation_id: fbsInvoiceCancel
tags:
  - FBS Invoice
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 52053a01f4d695e8
---

# Отмена накладной

`POST /v1/fbs/invoice/{invoiceId}/cancel`

Отмена накладной

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `invoiceId` | path | integer<int64> | да | Идентификатор накладной |
| `Accept-Language` | header | string (ru, uz) | нет | Язык локализации. Поддерживаемые языки: ru, uz. По умолчанию: uz |

## Ответы

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

**400** — Коды ошибок: seller-order-23 - Таймслот недоступен

- `payload` — object. Response payload
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string

**404** — Коды ошибок: fbs-invoice-01 - Накладная не найдена

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

- `payload` — object. Результат отмены накладной
  - `id` — integer<int64>. Идентификатор накладной
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string
