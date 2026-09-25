---
title: Получение остатков по SKU (устарело)
api: uzum-seller
method: GET
path: /v2/fbs/sku/stocks
operation_id: downloadFbsSkuStocks
tags:
  - Stocks
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: true
content_sha: b35014662ee46843
---

# Получение остатков по SKU (устарело)

`GET /v2/fbs/sku/stocks`

> ⚠️ Метод помечен как **deprecated**.

Устарело: используйте GET /v3/fbs/sku/stocks с пагинацией. Возвращает доступные для обновления остатки FBS и DBS SKU.

## Ответы

**200** — Success

- `payload` — object
  - `skuAmountList` — array[object]
    - `skuId` — integer<int64>. skuId, для обновления необязательное поле
    - `skuTitle` — string. skuTitle, для обновления необязательное поле
    - `productTitle` — string. productTitle, для обновления необязательное поле
    - `barcode` — string. ШК ску на стороне маркета, обязательное поле для обновления, должно быть уникальным
    - `amount` — integer<int32>. Остатки FBS для SKU
    - `fbsAllowed` — boolean. Разрешено ли продавать по FBS
    - `dbsAllowed` — boolean. Разрешено ли продавать по DBS
    - `fbsLinked` — boolean. Привязка SKU к FBS схеме
    - `dbsLinked` — boolean. Привязка SKU к DBS схеме
    - `sellerSkuCode` — string. для обновления необязательное поле, идентификатор СКУ селлера
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string

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

**403** — fbs-2-seller-access-denied: У селлера нет доступа, необходимы права 'SKU_READ' storage-service-04: Селлер заблокирован

- `payload` — object. Данные ответа, содержит информацию об объекте, возвращаемом сервисом.
- `errors` — array[object]. Список ошибок, если запрос не был успешно выполнен.
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>. Время формирования ответа, формат даты и времени.
- `trace` — string. Трассировка для отладки ошибок.
- `error` — string. Сообщение об ошибке, если оно имеется.

**500** — Internal server error

- `payload` — object. Данные ответа, содержит информацию об объекте, возвращаемом сервисом.
- `errors` — array[object]. Список ошибок, если запрос не был успешно выполнен.
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>. Время формирования ответа, формат даты и времени.
- `trace` — string. Трассировка для отладки ошибок.
- `error` — string. Сообщение об ошибке, если оно имеется.
