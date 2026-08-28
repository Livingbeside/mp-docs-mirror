---
title: Добавить товары в стратегию
api: ozon-seller
method: POST
path: /v1/pricing-strategy/products/add
operation_id: pricing_items-add
tags:
  - PricingStrategyAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 0cdc40c307724a68
---

# Добавить товары в стратегию

`POST /v1/pricing-strategy/products/add`

## Запрос

**Тело запроса** (`application/json`):

- `product_id` — array[string<int64>] **обязательный**. Список идентификаторов товаров в системе Ozon — `product_id`. Максимальное количество — 50.
- `strategy_id` — string **обязательный**. Идентификатор стратегии.

## Ответы

**200** — Ошибки при добавлении товаров

- `result` — object. Результат работы метода.
  - `errors` — array[object]. Товары с ошибками.
    - `code` — string. Код ошибки.
    - `error` — string. Текст ошибки.
    - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `failed_product_count` — integer<int32>. Количество товаров с ошибками.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
