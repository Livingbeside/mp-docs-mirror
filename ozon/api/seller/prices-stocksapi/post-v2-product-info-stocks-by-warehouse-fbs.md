---
title: Получить информацию об остатках на складах продавца
api: ozon-seller
method: POST
path: /v2/product/info/stocks-by-warehouse/fbs
operation_id: ProductAPI_GetProductInfoStocksByWarehouseFbsV2
tags:
  - Prices&StocksAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: d2f04ac6ac809713
---

# Получить информацию об остатках на складах продавца

`POST /v2/product/info/stocks-by-warehouse/fbs`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Количество товаров на складах

- `cursor` — string. Указатель для выборки следующих данных.
- `has_next` — boolean. `true`, если в ответе вернули не все товары.
- `products` — array[object]. Остатки товаров.
  - `free_stock` — integer<int64>. Количество доступных для продажи товаров.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `present` — integer<int64>. Общее количество товара на складе.
  - `product_id` — integer<int64>. Идентификатор товара в системе продавца — артикул.
  - `reserved` — integer<int64>. Количество зарезервированных товаров на складе.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `warehouse_id` — integer<int64>. Идентификатор склада.
  - `warehouse_name` — string. Название склада.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
