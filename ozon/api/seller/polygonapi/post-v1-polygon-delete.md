---
title: Удалить полигон из области доставки
api: ozon-seller
method: POST
path: /v1/polygon/delete
operation_id: PolygonDelete
tags:
  - PolygonAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 8be1f0327ae1dd95
---

# Удалить полигон из области доставки

`POST /v1/polygon/delete`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

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
