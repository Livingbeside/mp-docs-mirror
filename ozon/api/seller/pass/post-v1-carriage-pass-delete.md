---
title: Удалить пропуск
api: ozon-seller
method: POST
path: /v1/carriage/pass/delete
operation_id: carriagePassDelete
tags:
  - Pass
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 332c65a6d5130842
---

# Удалить пропуск

`POST /v1/carriage/pass/delete`

## Запрос

**Тело запроса** (`application/json`):

- `arrival_pass_ids` — array[string<int64>] **обязательный**. Идентификаторы пропусков.
- `carriage_id` — integer<int64> **обязательный**. Идентификатор перевозки.

## Ответы

**200** — Пропуск удалён

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
