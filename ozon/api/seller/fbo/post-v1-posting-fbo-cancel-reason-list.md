---
title: Причины отмены отправлений по схеме FBO
api: ozon-seller
method: POST
path: /v1/posting/fbo/cancel-reason/list
operation_id: PostingAPI_GetPostingFboCancelReasonList
tags:
  - FBO
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 8a5041389299c409
---

# Причины отмены отправлений по схеме FBO

`POST /v1/posting/fbo/cancel-reason/list`

Возвращает список причин отмены для всех FBO-отправлений.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Причины отмены отправлений

- `reasons` — array[object]. Информация о причинах отмены.
  - `id` — integer<int64>. Идентификатор причины отмены.
  - `name` — string. Причина отмены.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
