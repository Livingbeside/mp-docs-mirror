---
title: Изменение состава накладной
api: uzum-seller
method: POST
path: /v1/fbs/invoice/{invoiceId}/update-content
operation_id: updateFbsInvoice
tags:
  - FBS Invoice
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 52480ebf754acb32
---

# Изменение состава накладной

`POST /v1/fbs/invoice/{invoiceId}/update-content`

Изменение состава накладной

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Accept-Language` | header | string (ru, uz) | нет | Язык локализации. Поддерживаемые языки: ru, uz. По умолчанию: uz |

## Запрос

**Тело запроса** (`application/json`):

- `sellerId` — integer<int64> **обязательный**. ИД продавца
- `invoiceId` — integer<int64> **обязательный**. ИД накладной
- `customerOrderId` — integer<int64> **обязательный**. ИД заказа
- `idempotencyKey` — string. Ключ идемпотентности

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

**404** — Коды ошибок: fbs-invoice-01 - Накладная не найдена fbs-21-invoice-item-not-found - Позиция накладной не найдена fbs-23-seller-order-status-wrong - Не найден заказ в таком статусе

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

- `payload` — object. Результат изменения состава накладной
  - `id` — integer<int64>. ИД Накладной
  - `customerOrderId` — integer<int64> **обязательный**. ИД заказа
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string
