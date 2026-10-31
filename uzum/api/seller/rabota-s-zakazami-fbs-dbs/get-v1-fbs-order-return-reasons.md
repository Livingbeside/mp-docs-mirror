---
title: Получение причин возврата
api: uzum-seller
method: GET
path: /v1/fbs/order/return-reasons
operation_id: getFbsReturnReasons
tags:
  - Работа с заказами FBS/DBS
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: a3d701589f4e41c6
---

# Получение причин возврата

`GET /v1/fbs/order/return-reasons`

Нужен API-ключ в заголовке Authorization, без Bearer. В Swagger UI нажмите **Authorize**.

Возвращает список причин возврата для заказов.

## Ответы

**200** — OK

- `payload` — object. Список причин возврата.
  - `reasons` — array[object]. Список причин возврата.
    - `reason` — string (OUT_OF_STOCK, OUT_OF_PACKAGE, OUT_OF_TIME, OTHER, ACCEPTANCE_TIME_EXPIRED, DELIVERY_TIME_EXPIRED, RETURNED_BY_CUSTOMER, CANCELED_BY_CUSTOMER, MARKET_REASON). Причина возврата.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>. Метка времени ответа.
- `trace` — string. Трассировочная информация для отладки.
- `error` — string. Описание ошибки, если она произошла.

**400** — Bad Request

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
