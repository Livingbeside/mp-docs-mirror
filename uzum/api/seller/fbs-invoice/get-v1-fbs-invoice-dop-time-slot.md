---
title: Возвращает доступные тайм-слоты от текущего времени до минимальной даты «доставить до» среди переданных заказов, где оставшаяся емкость >= количеству заказов в списке
api: uzum-seller
method: GET
path: /v1/fbs/invoice/dop/time-slot
operation_id: getFbsInvoiceTimeSlots
tags:
  - FBS Invoice
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 57f0fdb4645da538
---

# Возвращает доступные тайм-слоты от текущего времени до минимальной даты «доставить до» среди переданных заказов, где оставшаяся емкость >= количеству заказов в списке

`GET /v1/fbs/invoice/dop/time-slot`

Возвращает доступные тайм-слоты от текущего времени до минимальной даты «доставить до» среди переданных заказов, где оставшаяся емкость >= количеству заказов в списке

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `dopId` | query | string<uuid> | да | Идентификатор drop off point |
| `sellerOrderIds` | query | array[integer<int64>] | да | Список идентификаторов заказов |
| `Accept-Language` | header | string (ru, uz) | нет | Язык локализации. Поддерживаемые языки: ru, uz. По умолчанию: uz |

## Ответы

**400** — Коды ошибок: seller-order-14 - Пункт приема Не найден fbs-20-incompatible-dimensional-groups - Не совместимы габаритные группы fbs-19-time-is-up - Время доставки вышло

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

- `payload` — object. Полученные тайм-слоты
  - `timeSlots` — array[object]. Список тайм-слотов
    - `timeFrom` — string<date-time>. Время начала временного интервала
    - `timeTo` — string<date-time>. Время окончания временного интервала
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string
