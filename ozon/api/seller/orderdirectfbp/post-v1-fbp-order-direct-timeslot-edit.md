---
title: Отредактировать таймслот в заявке на поставку
api: ozon-seller
method: POST
path: /v1/fbp/order/direct/timeslot/edit
operation_id: FbpAPI_FbpEditTimeslot
tags:
  - OrderDirectFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 15f05e1373f4deff
---

# Отредактировать таймслот в заявке на поставку

`POST /v1/fbp/order/direct/timeslot/edit`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `row_version` — integer<int64> **обязательный**. Идентификатор актуальной версии черновика.
- `supply_id` — string **обязательный**. Идентификатор заявки на поставку.
- `timeslot_start` — string<date-time> **обязательный**. Начало таймслота.

## Ответы

**200** — Таймслот отредактирован

- `error_reasons` — array[string (RESERVE_FAILURE_TYPE_UNSPECIFIED, REQUEST_VALIDATION, INVALID_RESERVE, LOGISTICS_REASON, SCHEDULE_REASON)]. Причина ошибки: - `RESERVE_FAILURE_TYPE_UNSPECIFIED` — не определена; - `REQUEST_VALIDATION` — в запросе указана дата резервирования в прошлом; - `INVALID_RESERVE` — исходный резерв не найден, неактивен или уже содержит заявки, а его пытаются перезаписать; - `LOGISTICS_REASON` — ошибка на стороне логистики; - `SCHEDULE_REASON` — ошибка на стороне расписаний.
- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
