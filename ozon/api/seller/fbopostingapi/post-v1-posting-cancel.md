---
title: Отменить отправление из заказа
api: ozon-seller
method: POST
path: /v1/posting/cancel
operation_id: PostingAPI_PostingCancel
tags:
  - FboPostingAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: db5a2160fad9e989
---

# Отменить отправление из заказа

`POST /v1/posting/cancel`

Отменяет отправление из заказа. Используйте идентификатор причины отмены `reasons.id` из метода [/v1/cancel-reason/list-by-posting](#operation/CancelReasonAPI_CancelReasonListByPosting).

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — string **обязательный**. Номер отправления.
- `reason_id` — integer<int32> **обязательный**. Идентификатор причины отмены.
- `reason_message` — string. Дополнительная информация по отмене.

## Ответы

**200** — Сообщение со статусом отмены

- `message` — string. Текст сообщения.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
