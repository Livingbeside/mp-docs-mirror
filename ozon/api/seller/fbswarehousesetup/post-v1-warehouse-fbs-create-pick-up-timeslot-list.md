---
title: Получить список таймслотов для создания склада с отгрузкой pick-up
api: ozon-seller
method: POST
path: /v1/warehouse/fbs/create/pick-up/timeslot/list
operation_id: WarehouseFbsCreatePickUpTimeslotList
tags:
  - FBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 860f70aba7367092
---

# Получить список таймслотов для создания склада с отгрузкой pick-up

`POST /v1/warehouse/fbs/create/pick-up/timeslot/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `address_coordinates` — object **обязательный**. Координаты склада.
  - `latitude` — number<double> **обязательный**. Широта.
  - `longitude` — number<double> **обязательный**. Долгота.
- `is_kgt` — boolean **обязательный**. Признак крупногабаритного товара.

## Ответы

**200** — Список таймслотов

- `is_pickup_supported` — boolean. Признак поддержки отгрузки pick-up.
- `timeslots` — array[object]. Список таймслотов.
  - `from` — string. Время начала таймслота.
  - `id` — integer<int64>. Идентификатор таймслота.
  - `to` — string. Время окончания таймслота.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
