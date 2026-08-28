---
title: Связать метод доставки с полигоном
api: ozon-seller
method: POST
path: /v2/polygon/bind
operation_id: PolygonBind
tags:
  - PolygonAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 03b2c14d2cf8f63c
---

# Связать метод доставки с полигоном

`POST /v2/polygon/bind`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `delivery_method_id` — integer<int64> **обязательный**. Идентификатор метода доставки.
- `polygon_id` — integer<int64> **обязательный**. Идентификатор полигона.
- `time` — integer (15, 30, 45, 60, 90, 120, 150) **обязательный**. Время доставки в минутах.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Успешно

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
