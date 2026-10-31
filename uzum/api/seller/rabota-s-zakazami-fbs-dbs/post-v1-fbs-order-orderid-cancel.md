---
title: Отмена заказа
api: uzum-seller
method: POST
path: /v1/fbs/order/{orderId}/cancel
operation_id: cancelFbsOrder
tags:
  - Работа с заказами FBS/DBS
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: c5764532ce8cc78d
---

# Отмена заказа

`POST /v1/fbs/order/{orderId}/cancel`

Нужен API-ключ в заголовке Authorization, без Bearer. В Swagger UI нажмите **Authorize**.

Отменяет заказ продавца.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `orderId` | path | integer<int64> | да | Идентификатор заказа, который необходимо отменить. |

## Запрос

**Тело запроса** (`application/json`):

- `reason` — string (OUT_OF_STOCK, OUT_OF_PACKAGE, OUT_OF_TIME, OTHER, ACCEPTANCE_TIME_EXPIRED, DELIVERY_TIME_EXPIRED, RETURNED_BY_CUSTOMER, CANCELED_BY_CUSTOMER, MARKET_REASON) **обязательный**. Причина отмены заказа.
- `comment` — string. Комментарий к отмене заказа.

## Ответы

**200** — Success

- `payload` — object. Response payload
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string

**400** — Ошибки выполнения: - `seller-order-01`: заказ не найден; - `seller-order-02`: неподходящий статус для отмены; - `seller-order-12`: недопустимая причина отмены; - `seller-order-13`: заказ уже отменен.

- `payload` — object. Данные ответа, содержит информацию об объекте, возвращаемом сервисом.
- `errors` — array[object]. Список ошибок, если запрос не был успешно выполнен.
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>. Время формирования ответа, формат даты и времени.
- `trace` — string. Трассировка для отладки ошибок.
- `error` — string. Сообщение об ошибке, если оно имеется.

**401** — Заголовок Authorization отсутствует или пуст. Передайте Authorization: API_TOKEN без префикса Bearer; заголовок token не используется.

**403** — Ключ не найден, истёк, выключен, не даёт доступа к магазину или изменениям. Если метод требует shopIds, проверьте наличие этого параметра и доступ ко всем указанным магазинам. Значение Authorization передавайте без Bearer.
