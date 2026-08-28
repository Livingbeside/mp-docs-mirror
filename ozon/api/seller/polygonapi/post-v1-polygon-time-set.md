---
title: Установить новое время доставки в полигоне
api: ozon-seller
method: POST
path: /v1/polygon/time/set
operation_id: PolygonTimeSet
tags:
  - PolygonAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 0177cdec8784e294
---

# Установить новое время доставки в полигоне

`POST /v1/polygon/time/set`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `current_time` — integer (15, 30, 45, 60, 90, 120, 150) **обязательный**. Текущее время доставки в минутах.
- `delivery_method_id` — integer<int64> **обязательный**. Идентификатор метода доставки.
- `new_time` — integer (15, 30, 45, 60, 90, 120, 150) **обязательный**. Новое время доставки в минутах.
- `polygon_id` — integer<int64> **обязательный**. Идентификатор полигона.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Успешно

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
