---
title: Получить список таймслотов для прямой поставки
api: ozon-seller
method: POST
path: /v1/fbp/draft/direct/timeslot/get
operation_id: FbpDraftDirectGetTimeslot
tags:
  - DraftDirectFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 73d19b920bb5b5b2
---

# Получить список таймслотов для прямой поставки

`POST /v1/fbp/draft/direct/timeslot/get`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `bundle_id` — string **обязательный**. Идентификатор провалидированного списка товаров.
- `interval_end` — string<date-time> **обязательный**. Дата окончания нужного периода доступных таймслотов.
- `interval_start` — string<date-time> **обязательный**. Дата начала нужного периода доступных таймслотов.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада продавца.

## Ответы

**200** — Список таймслотов

- `reasons` — array[string (EMPTY_TIMESLOTS_REASON_UNSPECIFIED, LOGISTICS_UNKNOWN, NO_ROUTE, NO_ROUTE_SCHEDULES, NO_LOGISTICS_CAPACITY, SCHEDULE_UNKNOWN, NOT_ENOUGH_CAPACITY, NOT_ENOUGH_TRUCKS, LIMITS_NOT_AVAILABLE, CROSS_DOCK_RESERVE_MISSING, SCHEDULE_RESERVE_MISSING)]. Причины отсутствия таймслотов: - `EMPTY_TIMESLOTS_REASON_UNSPECIFIED` — не определено; - `LOGISTICS_UNKNOWN` — неизвестная ошибка на стороне логистики; - `NO_ROUTE` — нет маршрута; - `NO_ROUTE_SCHEDULES` — нет расписания на маршруте; - `NO_LOGISTICS_CAPACITY` — недостаточно доступных слотов на маршруте; - `SCHEDULE_UNKNOWN` — неизвестная ошибка на стороне расписаний; - `NOT_ENOUGH_CAPACITY` — недостаточно доступных слотов на складе; - `NOT_ENOUGH_TRUCKS` — недостаточно машиномест; - `LIMITS_NOT_AVAILABLE` — не настроены лимиты на складе; - `CROSS_DOCK_RESERVE_MISSING` — не забронирован кросс-докинговый резерв на складе; - `SCHEDULE_RESERVE_MISSING` — отсутствует необходимый резерв по расписанию. По умолчанию: `EMPTY_TIMESLOTS_REASON_UNSPECIFIED`.
- `timeslots` — array[object]. Список доступных таймслотов.
  - `timeslot_end` — string<date-time>. Zaman aralığı bitiş tarihi.
  - `timeslot_start` — string<date-time>. Zaman aralığı başlangıç tarihi.
- `warehouse_timezone_name` — string. Часовой пояс склада продавца.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
