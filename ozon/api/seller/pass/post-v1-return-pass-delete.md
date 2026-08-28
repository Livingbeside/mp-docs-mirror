---
title: Удалить пропуск для возврата
api: ozon-seller
method: POST
path: /v1/return/pass/delete
operation_id: returnPassDelete
tags:
  - Pass
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 17c3f544caed8bba
---

# Удалить пропуск для возврата

`POST /v1/return/pass/delete`

## Запрос

**Тело запроса** (`application/json`):

- `arrival_pass_ids` — array[string<int64>] **обязательный**. Идентификаторы пропусков.

## Ответы

**200** — Пропуск удалён

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
