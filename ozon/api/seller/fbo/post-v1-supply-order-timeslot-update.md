---
title: Обновить интервал поставки
api: ozon-seller
method: POST
path: /v1/supply-order/timeslot/update
operation_id: SupplyOrderAPI_UpdateSupplyOrderTimeslot
tags:
  - FBO
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e506a17e032b92b9
---

# Обновить интервал поставки

`POST /v1/supply-order/timeslot/update`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `supply_order_id` — integer<int64> **обязательный**. Идентификатор заявки на поставку.
- `timeslot` — object **обязательный**. Время интервала поставки.
  - `from` — string<date-time> **обязательный**. Начало интервала по местному времени.
  - `to` — string<date-time> **обязательный**. Конец интервала по местному времени.

## Ответы

**200** — Интервал обновлён

- `errors` — array[string (UPDATE_TIMESLOT_ERROR_UNSPECIFIED, UPDATE_TIMESLOT_ERROR_INVALID_ORDER_STATE, UPDATE_TIMESLOT_ERROR_INCOMPATIBLE_ORDER_FLOW, UPDATE_TIMESLOT_ERROR_SET_TIMESLOT_DEADLINE_EXCEED, UPDATE_TIMESLOT_ERROR_OUT_OF_ALLOWED_RANGE, UPDATE_TIMESLOT_ERROR_ORDER_NOT_BELONG_CONTRACTOR, UPDATE_TIMESLOT_ERROR_ORDER_NOT_BELONG_COMPANY, UPDATE_TIMESLOT_ERROR_PICKUP_ORDER_LIMIT_EXCEEDED, UPDATE_TIMESLOT_ERROR_LIMIT_OF_CHANGING_TIMESLOT_EXCEEDED)]. Возможные ошибки: - `UNSPECIFIED` — статус не указан; - `INVALID_ORDER_STATE` — неверный статус заказа; - `INCOMPATIBLE_ORDER_FLOW` — неверный статус интервала поставки; - `SET_TIMESLOT_DEADLINE_EXCEED` — заявка на поставку просрочена; - `OUT_OF_ALLOWED_RANGE` — вы ввели некорректное значение интервала поставки; - `ORDER_NOT_BELONG_CONTRACTOR` — заявка создана другим юридическим лицом, работать с ней не получится; - `ORDER_NOT_BELONG_COMPANY` — заявка не принадлежит вашему кабинету, работать с ней не получится; - `UPDATE_TIMESLOT_ERROR_PICKUP_ORDER_LIMIT_EXCEEDED` — превышен суточный лимит на создание заявок на поставку курьером; - `UPDATE_TIMESLOT_ERROR_LIMIT_OF_CHANGING_TIMESLOT_EXCEEDED` — превышен лимит изменения интервала доставки.
- `operation_id` — string. Идентификатор операции.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
