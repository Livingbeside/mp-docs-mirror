---
title: Список конкурентов
api: ozon-seller
method: POST
path: /v1/pricing-strategy/competitors/list
operation_id: pricing_competitors
tags:
  - PricingStrategyAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: dc29a16915b60d4c
---

# Список конкурентов

`POST /v1/pricing-strategy/competitors/list`

Метод для получения списка конкурентов — продавцов с похожими товарами в других интернет-магазинах и маркетплейсах.

## Запрос

**Тело запроса** (`application/json`):

- `limit` — integer<int64> **обязательный**. Максимальное количество конкурентов на странице. Допустимы значения от `1` до `50`.
- `page` — integer<int64> **обязательный**. Страница списка, с которой нужно выгрузить конкурентов. Минимальное значение — `1`.

## Ответы

**200** — Список конкурентов

- `competitor` — array[object]. Список конкурентов.
  - `id` — integer<int64>. Идентификатор конкурента.
  - `name` — string. Название конкурента.
- `total` — integer<int32>. Общее количество конкурентов.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
