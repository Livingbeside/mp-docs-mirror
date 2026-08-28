---
title: Обновить настройки автоутилизации
api: ozon-seller
method: POST
path: /v1/returns/settings/utilization/update
operation_id: UtilizationUpdate
tags:
  - ReturnsAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 6a3daec8f26249e0
---

# Обновить настройки автоутилизации

`POST /v1/returns/settings/utilization/update`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `utilization_price` — object **обязательный**. Максимальная цена автоутилизации для товаров без дефектов.
  - `enabled` — boolean **обязательный**. `true`, если автоутилизация для товаров без дефектов включена.
  - `value` — integer<int64>. Значение цены. Параметр обязательный, если `enabled = true`.
- `utilization_price_defects` — object **обязательный**. Максимальная цена автоутилизации для товаров с дефектами.
  - `enabled` — boolean **обязательный**. `true`, если автоутилизация для товаров с дефектами включена.
  - `value` — integer<int64>. Значение цены. Параметр обязательный, если `enabled = true`.

## Ответы

**200** — Настройки обновлены

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
