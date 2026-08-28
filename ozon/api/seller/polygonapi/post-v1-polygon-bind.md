---
title: Свяжите метод доставки с полигоном доставки
api: ozon-seller
method: POST
path: /v1/polygon/bind
operation_id: PolygonAPI_BindPolygon
tags:
  - PolygonAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ded7d568d131fa31
---

# Свяжите метод доставки с полигоном доставки

`POST /v1/polygon/bind`

Метод устаревает и будет отключён в будущем. Переключитесь на /v2/polygon/bind .

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `delivery_method_id` — integer<int32> **обязательный**. Идентификатор метода доставки.
- `polygons` — array[object] **обязательный**. Список полигонов.
  - `polygon_id` — integer<int64> **обязательный**. Идентификатор полигона.
  - `time` — integer<int64> **обязательный**. Время в минутах, за которое доставят товар в этом полигоне.
- `warehouse_location` — object **обязательный**. Расположение склада.
  - `lat` — string **обязательный**. Географическая широта расположения склада.
  - `lon` — string **обязательный**. Географическая долгота расположения склада.

## Ответы

**200** — Успешно

**400** — Неверный параметр

- `code` — integer<int32>
- `details` — array[object]
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Сообщение об ошибке: - **delivery target polygons not provided** — полигоны не переданы; - **no delivery method id provided** — delivery_method_id не передан; - **no warehouse points provided** — не передана координата склада; - **polygon id .... not found** — переданы ID полигонов, которые не найдены в базе данных; - **not found polygon for warehouse point** — точка склада не принадлежит ни одному переданному полигону.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
