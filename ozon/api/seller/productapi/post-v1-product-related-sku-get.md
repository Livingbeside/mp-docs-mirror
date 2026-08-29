---
title: Получить связанные SKU
api: ozon-seller
method: POST
path: /v1/product/related-sku/get
operation_id: ProductAPI_ProductGetRelatedSKU
tags:
  - ProductAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: eabf33c771442af1
---

# Получить связанные SKU

`POST /v1/product/related-sku/get`

Метод для получения единого SKU по старым идентификаторам SKU FBS и SKU FBO. 
В ответе будут все SKU, связанные с переданными.

Метод может обработать любые SKU, даже скрытые или удалённые.

Передавайте до 200 SKU в одном запросе.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `sku` — ? **обязательный**. Список SKU.

## Ответы

**200** — Информация об SKU

- `items` — ?. Информация о связанных SKU.
  - `availability` — string. Признак доступности товара по SKU: - `HIDDEN` — скрыт; - `AVAILABLE` — доступен; - `UNAVAILABLE` — недоступен, SKU удалён.
  - `deleted_at` — string<date-time>. Дата и время удаления.
  - `delivery_schema` — string. Схема доставки: - `SDS` - идентификатор единого Ozon SKU; - `FBO` - идентификатор товара, который продаётся со склада Ozon; - `FBS` - идентификатор товара, который продаётся со склада FBS; - `Crossborder` - идентификатор товара, который продаётся из-за границы.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
- `errors` — ?. Ошибки.
  - `code` — string. Код ошибки.
  - `sku` — integer. SKU, в котором произошла ошибка.
  - `message` — string. Текст ошибки.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
