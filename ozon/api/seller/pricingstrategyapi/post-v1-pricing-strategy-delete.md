---
title: Удалить стратегию
api: ozon-seller
method: POST
path: /v1/pricing-strategy/delete
operation_id: pricing_delete
tags:
  - PricingStrategyAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 61190ea3aee8ee94
---

# Удалить стратегию

`POST /v1/pricing-strategy/delete`

Можно удалить любую стратегию кроме системной.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `strategy_id` — string **обязательный**. Идентификатор стратегии.

## Ответы

**200** — Стратегия удалена

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
