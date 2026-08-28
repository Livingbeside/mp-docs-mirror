---
title: Обновить первую милю
api: ozon-seller
method: POST
path: /v1/warehouse/fbs/first-mile/update
operation_id: UpdateWarehouseFBSFirstMile
tags:
  - FBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 46f60239675d835d
---

# Обновить первую милю

`POST /v1/warehouse/fbs/first-mile/update`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cut_in_time` — integer<int64> **обязательный**. Время на приём заказов в минутах. Например, если вы передадите `3000`, приём заказов будет завершён через 50 часов с момента передачи.
- `drop_off_point_id` — integer<int64>. Идентификатор drop-off пункта. Если `first_mile_type = DROP_OFF`, параметр обязательный.
- `first_mile_type` — string (PICK_UP, DROP_OFF) **обязательный**. Тип первой мили: - `PICK_UP` — отгрузка заказов курьеру; - `DROP_OFF` — отгрузка заказов в пункт приёма.
- `return_point_id` — integer<int64>. Идентификатор пункта возврата. Получите значение параметра методом [/v1/warehouse/fbs/update/return-point/list](#operation/WarehouseFBSUpdateReturnPointList).
- `timeslot_id` — integer<int64> **обязательный**. Идентификатор таймслота.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Первая миля обновлена

- `operation_id` — string. Идентификатор операции. Получите статус операции методом [/v1/warehouse/operation/status](#operation/GetWarehouseFBSOperationStatus).

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
