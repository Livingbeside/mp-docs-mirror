---
title: Изменить статус стратегии
api: ozon-seller
method: POST
path: /v1/pricing-strategy/status
operation_id: pricing_status
tags:
  - PricingStrategyAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 832939b42254f08c
---

# Изменить статус стратегии

`POST /v1/pricing-strategy/status`

Можно изменить статус любой стратегии кроме системной.

## Запрос

**Тело запроса** (`application/json`):

- `enabled` — boolean. Статус стратегии: - `true` — включена, - `false` — отключена.
- `strategy_id` — string **обязательный**. Идентификатор стратегии.

## Ответы

**200** — Статус стратегии изменён

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
