---
title: Получить информацию по остаткам на складе FBS и rFBS
api: ozon-seller
method: POST
path: /v1/product/info/warehouse/stocks
operation_id: ProductInfoWarehouseStocks
tags:
  - Prices&StocksAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 924982e6d62c0b15
---

# Получить информацию по остаткам на складе FBS и rFBS

`POST /v1/product/info/warehouse/stocks`

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `limit` — integer<int64> **обязательный**. Количество значений на странице.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Количество товара на складе FBS и rFBS

- `cursor` — string. Указатель для выборки следующих данных. Если параметр пустой, данных больше нет.
- `has_next` — boolean. Признак, что в ответе вернули не все товары: - `true` — сделайте повторный запрос с другим значением `cursor`, чтобы получить остальные значения; - `false` — ответ содержит все значения.
- `stocks` — array[object]. Информация об остатках товара.
  - `free_stock` — integer<int64>. Количество товара на складе, которое доступно для заказа.
  - `offer_id` — string. Идентификатор товара в системе продавца — `offer_id`.
  - `present` — integer<int64>. Общее количество товара на складе.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `reserved` — integer<int64>. Количество зарезервированных товаров на складе.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `updated_at` — string<date-time>. Дата последнего обновления товара.
  - `warehouse_id` — integer<int64>. Идентификатор склада.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
