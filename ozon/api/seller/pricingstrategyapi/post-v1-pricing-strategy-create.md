---
title: Создать стратегию
api: ozon-seller
method: POST
path: /v1/pricing-strategy/create
operation_id: pricing_create
tags:
  - PricingStrategyAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 75635b9688e45b50
---

# Создать стратегию

`POST /v1/pricing-strategy/create`

## Запрос

**Тело запроса** (`application/json`):

- `competitors` — array[object] **обязательный**. Список конкурентов.
  - `coefficient` — number<float> **обязательный**. Коэффициент, на который будет умножаться минимальная цена среди конкурентов. Допустимый диапазон — от `0.5` до `1.2`.
  - `competitor_id` — integer<int64> **обязательный**. Идентификатор конкурента.
- `strategy_name` — string **обязательный**. Название стратегии.

## Ответы

**200** — Стратегия создана

- `result` — object. Результат работы метода.
  - `strategy_id` — string. Идентификатор стратегии.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
