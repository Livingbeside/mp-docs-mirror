---
title: Получить информацию об остатках на складах FBO
api: ozon-seller
method: POST
path: /v1/product/info/stocks-by-warehouse/fbo
operation_id: GetProductInfoStocksByWarehouseFbo
tags:
  - Prices&StocksAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 939c48cf79072739
---

# Получить информацию об остатках на складах FBO

`POST /v1/product/info/stocks-by-warehouse/fbo`

Передайте в запросе `offer_ids` или `skus`.

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `limit` — integer<uint64> **обязательный**. Количество значений в ответе.
- `offer_ids` — array[string]. Идентификатор товаров в системе продавца — артикул.
- `skus` — array[string<int64>]. Идентификатор товаров в системе Ozon — SKU.

## Ответы

**200** — Информация об остатках.

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
