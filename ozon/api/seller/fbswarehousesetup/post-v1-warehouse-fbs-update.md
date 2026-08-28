---
title: Обновить склад
api: ozon-seller
method: POST
path: /v1/warehouse/fbs/update
operation_id: UpdateWarehouseFBS
tags:
  - FBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: be8b33e17f679c31
---

# Обновить склад

`POST /v1/warehouse/fbs/update`

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
- `name` — string. Название склада.
- `options` — object. Параметры склада.
  - `comment` — string. Комментарий для курьера при отгрузке с типом `PICK_UP`.
  - `courier_phones` — array[string]. Номера телефонов для курьера при отгрузке с типом `PICK_UP`.
  - `is_auto_assembly` — boolean. Признак включённой автосборки. По умолчанию: `False`.
  - `is_waybill_enabled` — boolean. Признак включённой печати транспортной накладной. По умолчанию: `False`.
- `phone` — string. Номер телефона склада.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.
- `working_days` — array[string (MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY)]. Рабочие дни склада: - `MONDAY` — понедельник; - `TUESDAY` — вторник; - `WEDNESDAY` — среда; - `THURSDAY` — четверг; - `FRIDAY` — пятница; - `SATURDAY` — суббота; - `SUNDAY` — воскресенье.

## Ответы

**200** — Склад обновлён

- `operation_id` — string. Идентификатор операции. Получите статус операции методом [/v1/warehouse/operation/status](#operation/GetWarehouseFBSOperationStatus).

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
