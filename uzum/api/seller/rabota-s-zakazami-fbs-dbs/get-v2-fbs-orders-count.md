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
content_sha: 1240e5262482a164
---

# Получить количество заказов

`GET /v2/fbs/orders/count`

Нужен API-ключ в заголовке Authorization, без Bearer. В Swagger UI нажмите **Authorize**.

Возвращает количество заказов FBS в зависимости от указанных фильтров — например, по статусу, магазину и диапазону дат.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `shopIds` | query | array[integer<int64>] | да | Обязательный список ID магазинов, доступных API-ключу. Получите ID через GET /v1/shops. Формат: shopIds=12345 или shopIds=12345,67890. Без shopIds gateway вернёт 403; shopId не заменяет этот параметр. |
| `status` | query | string (CREATED, PACKING, PENDING_DELIVERY, DELIVERING, DELIVERED, ACCEPTED_AT_DP, DELIVERED_TO_CUSTOMER_DELIVERY_POINT, COMPLETED, CANCELED, PENDING_CANCELLATION, RETURNED) | нет | Статус заказов, по которому нужно отфильтровать. По умолчанию — CREATED (создан). |
| `dateFrom` | query | integer<int64> | нет | Начальная дата создания заказа. Unix timestamp в секундах (int64), не в миллисекундах и не ДД.ММ.ГГГГ. Например, 1790794800 = 01.10.2026 00:00 UTC+5. |
| `dateTo` | query | integer<int64> | нет | Конечная дата создания заказа. Unix timestamp в секундах (int64), не в миллисекундах и не ДД.ММ.ГГГГ. Например, 1790794800 = 01.10.2026 00:00 UTC+5. |

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

**401** — Заголовок Authorization отсутствует или пуст. Передайте Authorization: API_TOKEN без префикса Bearer; заголовок token не используется.

**403** — Ключ не найден, истёк, выключен, не даёт доступа к магазину или изменениям. Если метод требует shopIds, проверьте наличие этого параметра и доступ ко всем указанным магазинам. Значение Authorization передавайте без Bearer.
