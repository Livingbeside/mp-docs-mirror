---
title: Удалить черновик для доставки в drop-off пункт
api: ozon-seller
method: POST
path: /v1/fbp/draft/drop-off/delete
operation_id: FbpDraftDropOffDelete
tags:
  - DraftDropOffFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 6bed235f9800dc78
---

# Удалить черновик для доставки в drop-off пункт

`POST /v1/fbp/draft/drop-off/delete`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `supply_id` — string **обязательный**. Идентификатор заявки на поставку.

## Ответы

**200** — Черновик удалён

- `cancellation_state` — object. Статус отмены.
  - `cancellation_error` — object. Ошибка отмены.
    - `error_code` — string (CODE_UNSPECIFIED, NO_RESPONSE_FROM_3PF, ACCEPTANCE_ALREADY_STARTED). Код ошибки: - `CODE_UNSPECIFIED` — не определён; - `NO_RESPONSE_FROM_3PF` — отмена заявки не подтверждена, мы не получили ответа от склада партнёра; - `ACCEPTANCE_ALREADY_STARTED` — отмена заявки не подтверждена, приёмка уже началась. По умолчанию: `CODE_UNSPECIFIED`.
    - `message` — string. Описание ошибки.
  - `cancellation_status` — string (STATUS_UNSPECIFIED, CONFIRMATION, CANCELED, NOT_CANCELED). Статус ошибки: - `STATUS_UNSPECIFIED` — не определён; - `CONFIRMATION` — ожидается подтверждение отмены заявки; - `CANCELED` — подтверждение получено; - `NOT_CANCELED` — подтверждение не получено. По умолчанию: `STATUS_UNSPECIFIED`.
- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
