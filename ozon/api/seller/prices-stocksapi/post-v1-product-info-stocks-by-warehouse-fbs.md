---
title: Информация об остатках на складах продавца (FBS и rFBS)
api: ozon-seller
method: POST
path: /v1/product/info/stocks-by-warehouse/fbs
operation_id: ProductAPI_ProductStocksByWarehouseFbs
tags:
  - Prices&StocksAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 6db42f7e0d0c121a
---

# Информация об остатках на складах продавца (FBS и rFBS)

`POST /v1/product/info/stocks-by-warehouse/fbs`

Метод устаревает и будет отключён 7 апреля 2026 года. Переключитесь на [/v2/product/info/stocks-by-warehouse/fbs](#operation/ProductAPI_GetProductInfoStocksByWarehouseFbsV2).

Передайте в запросе `offer_id` или `sku`. Если укажете оба, будет использован только `sku`.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Количество товаров на складах FBS и rFBS

- `result` — ?. Результат работы метода.
  - `offer_id` — string<int64>. Идентификатор товара в системе продавца — артикул.
  - `present` — integer<int64>. Общее количество товара на складе.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — артикул.
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
