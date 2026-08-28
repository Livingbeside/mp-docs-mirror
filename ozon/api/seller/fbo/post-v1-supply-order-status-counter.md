---
title: Количество заявок по статусам
api: ozon-seller
method: POST
path: /v1/supply-order/status/counter
operation_id: SupplyOrderAPI_SupplyOrderStatusCounter
tags:
  - FBO
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 109a6e293711ce8f
---

# Количество заявок по статусам

`POST /v1/supply-order/status/counter`

Возвращает количество заявок в конкретном статусе.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Статус заявки и количество заявок в этом статусе

- `items` — array[object]
  - `count` — integer<int32>. Количество заявок в статусе.
  - `order_state` — string (ORDER_STATE_UNSPECIFIED, ORDER_STATE_DATA_FILLING, ORDER_STATE_READY_TO_SUPPLY, ORDER_STATE_ACCEPTED_AT_SUPPLY_WAREHOUSE, ORDER_STATE_IN_TRANSIT, ORDER_STATE_ACCEPTANCE_AT_STORAGE_WAREHOUSE, ORDER_STATE_REPORTS_CONFIRMATION_AWAITING, ORDER_STATE_REPORT_REJECTED, ORDER_STATE_COMPLETED, ORDER_STATE_REJECTED_AT_SUPPLY_WAREHOUSE, ORDER_STATE_CANCELLED). Статус поставки: - `UNSPECIFIED` — статус не указан; - `DATA_FILLING` — заполнение данных; - `READY_TO_SUPPLY` — готова к отгрузке; - `ACCEPTED_AT_SUPPLY_WAREHOUSE` — принята на точке отгрузки; - `IN_TRANSIT` — в пути; - `ACCEPTANCE_AT_STORAGE_WAREHOUSE` — приёмка на складе; - `REPORTS_CONFIRMATION_AWAITING` — согласование актов; - `REPORT_REJECTED` — спор; - `COMPLETED` — завершена; - `REJECTED_AT_SUPPLY_WAREHOUSE` — отказано в приёмке; - `CANCELLED` — отменена. По умолчанию: `ORDER_STATE_UNSPECIFIED`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
