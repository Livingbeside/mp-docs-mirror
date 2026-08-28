---
title: Получить список таймслотов для обновления склада с отгрузкой pick-up
api: ozon-seller
method: POST
path: /v1/warehouse/fbs/update/pick-up/timeslot/list
operation_id: WarehouseFbsUpdatePickUpTimeslotList
tags:
  - FBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 5d10944ab535e919
---

# Получить список таймслотов для обновления склада с отгрузкой pick-up

`POST /v1/warehouse/fbs/update/pick-up/timeslot/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Список таймслотов

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
