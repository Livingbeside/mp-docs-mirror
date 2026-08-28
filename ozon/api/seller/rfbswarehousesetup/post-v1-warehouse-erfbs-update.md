---
title: Обновить склад
api: ozon-seller
method: POST
path: /v1/warehouse/erfbs/update
operation_id: WarehouseERFBSUpdate
tags:
  - rFBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 4d8e93f63bafec5e
---

# Обновить склад

`POST /v1/warehouse/erfbs/update`

[Подробнее о схеме realFBS Express](https://seller-edu.ozon.ru/rfbs/scheme-of-work/rfbs-express#%D1%87%D1%82%D0%BE-%D1%82%D0%B0%D0%BA%D0%BE%D0%B5-realfbs-express)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `is_auto_assembly` — boolean. `true`, если на складе доступна автосборка. По умолчанию: `False`.
- `min_order_value` — integer<int64>. Минимальная стоимость заказа.
- `name` — string. Название склада.
- `phone` — string. Номер телефона склада.
- `timetable_warehouse` — object. Расписание работы склада.
  - `holidays` — array[object]. Выходные дни склада.
    - `day` — string. День в формате `YYYY-MM-DD`.
    - `from` — string. Время начала выходного дня в формате `HH:MM`.
    - `to` — string. Время окончания выходного дня в формате `HH:MM`.
  - `working_days` — array[object]. Рабочие дни склада.
    - `day` — string (UNSPECIFIED, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY). Рабочий день: - `UNSPECIFIED` — не определён, - `MONDAY` — понедельник, - `TUESDAY` — вторник, - `WEDNESDAY` — среда, - `THURSDAY` — четверг, - `FRIDAY` — пятница, - `SATURDAY` — суббота, - `SUNDAY` — воскресенье. По умолчанию: `UNSPECIFIED`.
    - `from` — string. Время начала рабочего дня в формате `HH:MM`.
    - `to` — string. Время окончания рабочего дня в формате `HH:MM`.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Склад обновлён

- `operation_id` — string. Идентификатор операции. Получите статус операции методом [/v1/warehouse/operation/status](#operation/GetWarehouseFBSOperationStatus).

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
