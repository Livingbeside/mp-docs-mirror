---
title: Получить список установленных полигонов на метод доставки
api: ozon-seller
method: POST
path: /v1/polygon/list
operation_id: PolygonList
tags:
  - PolygonAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 4b2865835b56af7c
---

# Получить список установленных полигонов на метод доставки

`POST /v1/polygon/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `delivery_method_id` — integer<int64> **обязательный**. Идентификатор метода доставки.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Список полигонов

- `polygons` — array[object]. Список полигонов.
  - `coordinates` — string. Координаты полигона доставки в формате `[[[lat,long],[lat,long]]]`.
  - `polygon_id` — integer<int64>. Идентификатор полигона.
  - `time` — integer<int64>. Время доставки в минутах.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
