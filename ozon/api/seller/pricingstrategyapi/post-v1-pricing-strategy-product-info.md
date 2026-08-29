---
title: Цена товара у конкурента
api: ozon-seller
method: POST
path: /v1/pricing-strategy/product/info
operation_id: pricing_items-info
tags:
  - PricingStrategyAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9ebdcf18db407f5e
---

# Цена товара у конкурента

`POST /v1/pricing-strategy/product/info`

Если вы добавили товар в стратегию ценообразования, метод вернёт цену и ссылку на товар у конкурента.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `product_id` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — `product_id`.

## Ответы

**200** — Цена товара у конкурента

- `result` — object. Результат работы метода.
  - `strategy_id` — string. Идентификатор стратегии.
  - `is_enabled` — boolean. `true`, если товар участвует в стратегии ценообразования.
  - `strategy_product_price` — integer<int32>. Цена по стратегии.
  - `price_downloaded_at` — string. Дата установки цены по стратегии.
  - `strategy_competitor_id` — integer<int64>. Идентификатор конкурента.
  - `strategy_competitor_product_url` — string. Ссылка на товар конкурента.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
