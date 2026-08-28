---
title: Получить расписание работы drop-off пункта
api: ozon-seller
method: POST
path: /v1/fbp/draft/drop-off/point/timetable
operation_id: FbpDraftDropOffPointTimetable
tags:
  - DraftDropOffFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e7e1161ae1ffc831
---

# Получить расписание работы drop-off пункта

`POST /v1/fbp/draft/drop-off/point/timetable`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

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

**200** — Расписание работы

- `calendar` — array[object]. Расписание работы drop-off пункта.
  - `calendar_item` — object. Расписание работы.
    - `break_hours` — object. Часы перерыва.
      - `timeslot_end` — string. Время окончания таймслота.
      - `timeslot_start` — string. Время начала таймслота.
    - `is_holiday` — boolean. `true`, если праздничный день.
    - `opening_hours` — object. Часы работы.
      - `timeslot_end` — string. Время окончания таймслота.
      - `timeslot_start` — string. Время начала таймслота.
  - `day_of_week` — string (DAY_OF_WEEK_UNSPECIFIED, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY). Дни недели: - `DAY_OF_WEEK_UNSPECIFIED` — не определён, - `MONDAY` — понедельник, - `TUESDAY` — вторник, - `WEDNESDAY` — среда, - `THURSDAY` — четверг, - `FRIDAY` — пятница, - `SATURDAY` — суббота, - `SUNDAY` — воскресенье. По умолчанию: `DAY_OF_WEEK_UNSPECIFIED`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
