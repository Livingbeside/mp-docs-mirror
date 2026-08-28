---
title: Удалить товары из стратегии
api: ozon-seller
method: POST
path: /v1/pricing-strategy/products/delete
operation_id: pricing_items-delete
tags:
  - PricingStrategyAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 230e0e46f2e06bda
---

# Удалить товары из стратегии

`POST /v1/pricing-strategy/products/delete`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `product_id` — array[string<int64>] **обязательный**. Список идентификаторов товаров в системе Ozon — `product_id`. Максимальное количество — 50.

## Ответы

**200** — Ошибки при удалении товаров

- `result` — object. Результат работы метода.
  - `failed_product_count` — integer<int32>. Количество товаров с ошибками.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
