---
title: Получить FBS заказы по идентификатору накладной
api: uzum-seller
method: GET
path: /v1/fbs/invoice/{invoiceId}/orders
operation_id: getFbsOrdersByInvoiceId
tags:
  - FBS Invoice
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 1b176f6ee63d029e
---

# Получить FBS заказы по идентификатору накладной

`GET /v1/fbs/invoice/{invoiceId}/orders`

Получить FBS заказы по идентификатору накладной

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `id` | path | integer<int64> | да | Идентификатор накладной |
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

**200** — Success

- `payload` — array[object]. Response payload
  - `orderId` — integer<int64> **обязательный**. Накладная
  - `fullPrice` — integer<int64> **обязательный**. Сумма заказа
  - `items` — array[object] **обязательный**. Список элементов заказов
    - `orderId` — integer<int64> **обязательный**. Идентификатор заказа
    - `barcode` — string **обязательный**. SKU баркод
    - `skuTitle` — string **обязательный**. Наименование SKU
    - `sellerSkuCode` — string. Идентификатор SKU селлера. Отсутствует, если селлер не задал код для этого SKU
    - `title` — string **обязательный**. Наименовани
    - `amount` — integer<int32> **обязательный**. Кол-во
    - `price` — integer<int64> **обязательный**. Цена
    - `skuId` — integer<int64>. идентификаторс SKU
    - `photo` — object
      - `high` — string<uri>. URL высокого качества изображения
      - `low` — string<uri>. URL низкого качества изображения
    - `status` — string (NOT_ACCEPTED, ACCEPTED, IN_PROGRESS, CANCELLED). Статус накладной
    - `deliverUntil` — string<date-time>. Дата до которой селлер должен сдать заказ
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string
