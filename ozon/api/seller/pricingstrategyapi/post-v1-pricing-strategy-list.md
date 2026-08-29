---
title: Список стратегий
api: ozon-seller
method: POST
path: /v1/pricing-strategy/list
operation_id: pricing_list
tags:
  - PricingStrategyAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: c24805f323084c7c
---

# Список стратегий

`POST /v1/pricing-strategy/list`

## Запрос

**Тело запроса** (`application/json`):

- `page` — integer<int64> **обязательный**. Страница списка, с которой нужно выгрузить стратегии. Минимальное значение — `1`.
- `limit` — integer<int64> **обязательный**. Максимальное количество стратегий на странице. Допустимые значения — от `1` до `50`.

## Ответы

**200** — Список стратегий

- `strategies` — array[object]. Список стратегий.
  - `id` — string. Идентификатор стратегии.
  - `name` — string. Название стратегии.
  - `type` — string. Тип стратегии: - `MIN_EXT_PRICE` — системная, - `COMP_PRICE` — пользовательская.
  - `update_type` — string. Тип последнего изменения стратегии: - `strategyEnabled` — возобновлена, - `strategyDisabled` — остановлена, - `strategyChanged` — обновлена, - `strategyCreated` — создана, - `strategyItemsListChanged` — изменён набор товаров в стратегии.
  - `updated_at` — string. Дата последнего изменения.
  - `products_count` — integer<int64>. Количество товаров в стратегии.
  - `competitors_count` — integer<int64>. Количество выбранных конкурентов.
  - `enabled` — boolean. Статус стратегии: - `true` — включена, - `false` — отключена.
- `total` — integer<int32>. Общее количество стратегий.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
