---
title: Отредактировать детали доставки для drop-off черновика
api: ozon-seller
method: POST
path: /v1/fbp/draft/drop-off/dlv/edit
operation_id: FbpDraftDropOffDlvEdit
tags:
  - DraftDropOffFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: f23299979a171c73
---

# Отредактировать детали доставки для drop-off черновика

`POST /v1/fbp/draft/drop-off/dlv/edit`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `drop_off_date` — string **обязательный**. Дата доставки.
- `drop_off_point_id` — integer<int64> **обязательный**. Идентификатор drop-off пункта.
- `drop_off_province_uuid` — string **обязательный**. Уникальный идентификатор провинции.
- `row_version` — integer<int64> **обязательный**. Идентификатор актуальной версии черновика.
- `supply_id` — string **обязательный**. Идентификатор заявки на поставку.

## Ответы

**200** — Успешно

- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
