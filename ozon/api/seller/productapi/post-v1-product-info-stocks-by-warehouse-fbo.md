---
title: Получить информацию о стоках на складах FBO
api: ozon-seller
method: POST
path: /v1/product/info/stocks-by-warehouse/fbo
operation_id: GetProductInfoStocksByWarehouseFbo
tags:
  - ProductAPI
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9553e7929df6debd
---

# Получить информацию о стоках на складах FBO

`POST /v1/product/info/stocks-by-warehouse/fbo`

Передайте в запросе `offer_ids` или `skus`. Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/2177-Novyi-metod-dlia-polucheniia-ostatkov-FBO/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `limit` — integer<uint64> **обязательный**. Количество значений в ответе.
- `offer_ids` — array[string]. Идентификатор товаров в системе продавца — артикул.
- `skus` — array[string<int64>]. Идентификатор товаров в системе Ozon — SKU.

## Ответы

**200** — Информация о стоках.

- `cursor` — string. Указатель для выборки следующих данных.
- `has_next` — boolean. `true`, если в ответе вернулись не все значения.
- `products` — array[object]. Остатки товаров FBO.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `present` — integer<int64>. Общее количество товара на складе.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `reserved` — integer<int64>. Количество зарезервированных товаров на складе.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `warehouse_id` — integer<int64>. Идентификатор склада. Можно получить с помощью метода [/v1/warehouse/ozon/list](#operation/WarehouseOZONList).

**default** — Ошибка.

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
