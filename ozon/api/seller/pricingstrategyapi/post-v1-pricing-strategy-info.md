---
title: Информация о стратегии
api: ozon-seller
method: POST
path: /v1/pricing-strategy/info
operation_id: pricing_info
tags:
  - PricingStrategyAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: d2c7868ffc75df6b
---

# Информация о стратегии

`POST /v1/pricing-strategy/info`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `strategy_id` — string **обязательный**. Идентификатор стратегии.

## Ответы

**200** — Информация о стратегии

- `result` — object. Результат работы метода.
  - `competitors` — array[object]. Список конкурентов.
    - `coefficient` — number<float> **обязательный**. Коэффициент, на который будет умножаться минимальная цена среди конкурентов. Допустимый диапазон — от `0.5` до `1.2`.
    - `competitor_id` — integer<int64> **обязательный**. Идентификатор конкурента.
  - `enabled` — boolean. Статус стратегии: - `true` — включена, - `false` — отключена.
  - `name` — string. Название стратегии.
  - `type` — string. Тип стратегии: - `MIN_EXT_PRICE` — системная стратегия, - `COMP_PRICE` — пользовательская стратегия.
  - `update_type` — string. Тип последнего изменения стратегии: - `strategyEnabled` — возобновлена, - `strategyDisabled` — остановлена, - `strategyChanged` — обновлена, - `strategyCreated` — создана, - `strategyItemsListChanged` — изменён набор товаров в стратегии.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
