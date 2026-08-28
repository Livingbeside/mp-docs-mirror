---
title: Отредактировать таймслот в черновике
api: ozon-seller
method: POST
path: /v1/fbp/draft/direct/timeslot/edit
operation_id: FbpDraftDirectTimeslotEdit
tags:
  - DraftDirectFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 2f97107957e969fd
---

# Отредактировать таймслот в черновике

`POST /v1/fbp/draft/direct/timeslot/edit`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `row_version` — integer<int64> **обязательный**. Идентификатор актуальной версии черновика.
- `supply_id` — string **обязательный**. Идентификатор заявки на поставку.
- `timeslot_start` — string<date-time> **обязательный**. Начало таймслота.

## Ответы

**200** — Таймслот отредактирован

- `error_reasons` — array[string (RESERVE_FAILURE_TYPE_UNSPECIFIED, REQUEST_VALIDATION, INVALID_RESERVE, LOGISTICS_REASON, SCHEDULE_REASON, NO_CAPACITY)]. Причина ошибки: - `RESERVE_FAILURE_TYPE_UNSPECIFIED` — не определена; - `REQUEST_VALIDATION` — в запросе указана дата резервирования в прошлом; - `INVALID_RESERVE` — исходный резерв не найден, неактивен или уже содержит заявки, а его пытаются перезаписать; - `LOGISTICS_REASON` — ошибка на стороне логистики; - `SCHEDULE_REASON` — ошибка на стороне расписаний; - `NO_CAPACITY` — нет доступных слотов для резервирования. По умолчанию: `RESERVE_FAILURE_TYPE_UNSPECIFIED`.
- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
