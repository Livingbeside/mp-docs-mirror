---
title: Создайте полигон доставки
api: ozon-seller
method: POST
path: /v1/polygon/create
operation_id: PolygonAPI_CreatePolygon
tags:
  - PolygonAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 4d87e744104dffa0
---

# Создайте полигон доставки

`POST /v1/polygon/create`

Вы можете добавить полигон к методу доставки. Создайте полигон, получив его координаты на https://geojson.io: отметьте на карте минимум 3 точки и соедините их линиями. Сервис geojson.io возвращает координаты в формате [[[long lat]]] . Поменяйте местами широту и долготу в запросе метода.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `coordinates` — string **обязательный**. Координаты полигона доставки в формате `[[[lat long]]]`.

## Ответы

**200** — Полигон создан

- `polygon_id` — integer<int64>. Идентификатор полигона.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Сообщение об ошибке: - `coordinates not provided` — координаты не переданы; - `invalid coordinates, must have two points in coordinate` — в какой-то точке передана только широта или долгота, нужно передать две точки; - `the first and last points in loop must be same` — первая и последняя точка не совпадают (по стандартным правилам geojson точки должны совпадать); - `non-full loops must have at least 4 unique vertices for polygons` — для полигона передано менее четырех точек.

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
