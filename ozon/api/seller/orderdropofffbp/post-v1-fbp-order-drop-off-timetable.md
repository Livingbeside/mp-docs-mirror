---
title: Получить график работы drop-off пункта
api: ozon-seller
method: POST
path: /v1/fbp/order/drop-off/timetable
operation_id: FbpAPI_FbpOrderDropOffTimetable
tags:
  - OrderDropOffFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 60f14f45a9265908
---

# Получить график работы drop-off пункта

`POST /v1/fbp/order/drop-off/timetable`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `drop_off_point_id` — integer<int64> **обязательный**. Идентификатор drop-off пункта.
- `province_uuid` — string **обязательный**. Уникальный идентификатор провинции.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — График работы получен

- `calendar` — array[object]. Информация о графике работы drop-off пункта.
  - `calendar_item` — object. Информация о дне.
    - `break_hours` — object. Информация о перерыве.
      - `timeslot_end` — string. Время начала.
      - `timeslot_start` — string. Время окончания.
    - `is_holiday` — boolean. `true`, если выходной день.
    - `opening_hours` — object. Информация о рабочих часах.
      - `timeslot_end` — string. Время начала.
      - `timeslot_start` — string. Время окончания.
  - `day_of_week` — string (DAY_OF_WEEK_UNSPECIFIED, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY). Дни недели: - `DAY_OF_WEEK_UNSPECIFIED` — не определён, - `MONDAY` — понедельник, - `TUESDAY` — вторник, - `WEDNESDAY` — среда, - `THURSDAY` — четверг, - `FRIDAY` — пятница, - `SATURDAY` — суббота, - `SUNDAY` — воскресенье. По умолчанию: `DAY_OF_WEEK_UNSPECIFIED`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
