---
title: Список товаров в стратегии
api: ozon-seller
method: POST
path: /v1/pricing-strategy/products/list
operation_id: pricing_items-list
tags:
  - PricingStrategyAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 96d3dd6711a915c7
---

# Список товаров в стратегии

`POST /v1/pricing-strategy/products/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `strategy_id` — string **обязательный**. Идентификатор стратегии.

## Ответы

**200** — Список товаров

- `result` — object. Список товаров.
  - `product_id` — array[string<int64>]. Идентификатор товара в системе Ozon — `product_id`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
