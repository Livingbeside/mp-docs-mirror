---
title: Обновить количество товаров на складах
api: ozon-seller
method: POST
path: /v2/products/stocks
operation_id: ProductAPI_ProductsStocksV2
tags:
  - Prices&StocksAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: fe6fc6923b7de561
---

# Обновить количество товаров на складах

`POST /v2/products/stocks`

Позволяет изменить информацию о количестве товара в наличии.

Переданный остаток — количество товара в наличии без учёта зарезервированных товаров. Перед обновлением остатков проверьте количество зарезервированных товаров с помощью метода [/v2/product/info/stocks-by-warehouse/fbs](#operation/ProductAPI_GetProductInfoStocksByWarehouseFbsV2).

За один запрос можно изменить наличие для 100 пар товар-склад. С одного аккаунта продавца можно отправить до 80 запросов в минуту.

Обновлять остатки у одной пары товар-склад можно только 1 раз в 30 секунд, иначе в параметре result.errors в ответе будет ошибка TOO_MANY_REQUESTS.

Вы можете задать наличие товара только после того, как его статус сменится на `price_sent`.

Остатки крупногабаритных товаров можно обновлять только на предназначенных для них складах.

Если запрос содержит оба параметра — `offer_id` и `product_id`, изменения применятся к товару с `offer_id`. Для избежания неоднозначности используйте только один из параметров.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `stocks` — array[object] **обязательный**. Информация о товарах на складах.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `product_id` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — `product_id`.
  - `stock` — integer<int64> **обязательный**. Количество товара в наличии без учёта зарезервированных товаров.
  - `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада, полученный из метода [/v1/warehouse/list](#operation/WarehouseAPI_WarehouseList).

## Ответы

**200** — Количество товаров обновлено

- `result` — array[object]
  - `errors` — array[object]. Массив ошибок, которые возникли при обработке запроса.
    - `code` — string. Код ошибки.
    - `message` — string. Причина ошибки.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `updated` — boolean. Если запрос выполнен успешно и остатки обновлены — `true`.
  - `warehouse_id` — integer<int64>. Идентификатор склада.

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
