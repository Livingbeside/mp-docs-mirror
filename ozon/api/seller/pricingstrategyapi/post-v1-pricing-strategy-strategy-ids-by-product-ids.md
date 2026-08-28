---
title: Список идентификаторов стратегий
api: ozon-seller
method: POST
path: /v1/pricing-strategy/strategy-ids-by-product-ids
operation_id: pricing_ids
tags:
  - PricingStrategyAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ee36c39f177fdd32
---

# Список идентификаторов стратегий

`POST /v1/pricing-strategy/strategy-ids-by-product-ids`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `product_id` — array[string<int64>] **обязательный**. Список идентификаторов товаров в системе Ozon — `product_id`. Максимальное количество — 50.

## Ответы

**200** — Список идентификаторов

- `result` — object. Результат работы метода.
  - `products_info` — array[object]. Информация о товаре.
    - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
    - `strategy_id` — string. Идентификатор стратегии, в которую добавлен товар.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
