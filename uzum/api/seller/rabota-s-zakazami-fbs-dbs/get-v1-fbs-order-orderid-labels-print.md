---
title: Получить этикетку для FBS заказа
api: uzum-seller
method: GET
path: /v1/fbs/order/{orderId}/labels/print
operation_id: fbsPrintLabel
tags:
  - Работа с заказами FBS/DBS
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 7ff86d96448480d3
---

# Получить этикетку для FBS заказа

`GET /v1/fbs/order/{orderId}/labels/print`

Печатает этикетку для FBS заказа

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `orderId` | path | integer<int64> | да | — |
| `size` | query | string (LARGE, BIG) | да | Размер этикетки: LARGE (58x40mm) или BIG ( 43x25mm) |

## Ответы

**400** — Possible error codes: seller-order-01 - Seller order not found, seller-order-14 - Label service unavailable, try later, seller-order-15 - Customer order identifiers are missing

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

- `payload` — object. DTO этикетки FBS заказа
  - `document` — array[string<byte>] **обязательный**. PDF этикетки FBS заказа в Base64 строке
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string
