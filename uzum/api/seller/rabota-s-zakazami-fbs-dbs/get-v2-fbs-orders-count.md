---
title: Получить количество заказов
api: uzum-seller
method: GET
path: /v2/fbs/orders/count
operation_id: getOrderCountV2
tags:
  - Работа с заказами FBS/DBS
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: f38402aa8d48bcb3
---

# Получить количество заказов

`GET /v2/fbs/orders/count`

Возвращает количество заказов FBS в зависимости от указанных фильтров — например, по статусу, магазину и диапазону дат.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `shopIds` | query | array[integer<int64>] | нет | Массив идентификаторов магазинов. |
| `status` | query | string (CREATED, PACKING, PENDING_DELIVERY, DELIVERING, DELIVERED, ACCEPTED_AT_DP, DELIVERED_TO_CUSTOMER_DELIVERY_POINT, COMPLETED, CANCELED, PENDING_CANCELLATION, RETURNED) | нет | Статус заказов, по которому нужно отфильтровать. По умолчанию — CREATED (создан). |
| `dateFrom` | query | integer<int64> | нет | Начальная дата для фильтрации заказов. |
| `dateTo` | query | integer<int64> | нет | — |

## Ответы

**200** — Success

- `payload` — integer<int64>. Полезная нагрузка ответа — числовое значение типа long.
- `errors` — array[object]. Массив ошибок, возникших при выполнении запроса.
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>. Дата и время формирования ответа, в формате ISO 8601.
- `trace` — string. Трассировочный идентификатор запроса, полезен для отладки и логирования.
- `error` — string. Краткое описание ошибки, если она произошла. Если значение равно null — значит ошибка не возникла.

**400** — seller-order-12 - dateTo is before dateFrom

- `payload` — integer<int64>. Полезная нагрузка ответа — числовое значение типа long.
- `errors` — array[object]. Массив ошибок, возникших при выполнении запроса.
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>. Дата и время формирования ответа, в формате ISO 8601.
- `trace` — string. Трассировочный идентификатор запроса, полезен для отладки и логирования.
- `error` — string. Краткое описание ошибки, если она произошла. Если значение равно null — значит ошибка не возникла.
