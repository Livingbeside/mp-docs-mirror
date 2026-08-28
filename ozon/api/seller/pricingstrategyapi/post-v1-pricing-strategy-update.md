---
title: Обновить стратегию
api: ozon-seller
method: POST
path: /v1/pricing-strategy/update
operation_id: pricing_update
tags:
  - PricingStrategyAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 93a65b7a93327120
---

# Обновить стратегию

`POST /v1/pricing-strategy/update`

Можно обновить все стратегии кроме системной.

## Запрос

**Тело запроса** (`application/json`):

- `competitors` — array[object] **обязательный**. Список конкурентов.
  - `coefficient` — number<float> **обязательный**. Коэффициент, на который будет умножаться минимальная цена среди конкурентов. Допустимый диапазон — от `0.5` до `1.2`.
  - `competitor_id` — integer<int64> **обязательный**. Идентификатор конкурента.
- `strategy_id` — string **обязательный**. Идентификатор стратегии.
- `strategy_name` — string **обязательный**. Название стратегии.

## Ответы

**200** — Стратегия обновлена

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
