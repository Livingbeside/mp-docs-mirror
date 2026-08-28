---
title: Получить список таймслотов для создания склада с отгрузкой drop-off
api: ozon-seller
method: POST
path: /v1/warehouse/fbs/create/drop-off/timeslot/list
operation_id: WarehouseFbsCreateDropOffTimeslotList
tags:
  - FBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ea4a2a8fd1d03c18
---

# Получить список таймслотов для создания склада с отгрузкой drop-off

`POST /v1/warehouse/fbs/create/drop-off/timeslot/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `drop_off_point_id` — integer<int64> **обязательный**. Идентификатор drop-off пункта.

## Ответы

**200** — Список таймслотов

- `timeslots` — array[object]. Список таймслотов.
  - `acceptance_end_time_local` — string. Местное время окончания приёма заказа.
  - `acceptance_start_time_local` — string. Местное время начала приёма заказа.
  - `from` — string. Время начала таймслота.
  - `id` — integer<int64>. Идентификатор таймслота.
  - `to` — string. Время окончания таймслота.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
