---
title: Обновить координаты полигона доставки
api: ozon-seller
method: POST
path: /v1/polygon/time/coordinates/update
operation_id: PolygonTimeCoordinatesUpdate
tags:
  - PolygonAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: b4345a3351b11c41
---

# Обновить координаты полигона доставки

`POST /v1/polygon/time/coordinates/update`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `coordinates` — string **обязательный**. Новые координаты полигона доставки в формате `[[[lat,long],[lat,long]]]`.
- `delivery_method_id` — integer<int64> **обязательный**. Идентификатор метода доставки.
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
