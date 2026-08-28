---
title: Проверить статус отмены отправления
api: ozon-seller
method: POST
path: /v1/posting/cancel/status
operation_id: PostingAPI_PostingCancelStatus
tags:
  - FboPostingAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: d8439f15c120a50d
---

# Проверить статус отмены отправления

`POST /v1/posting/cancel/status`

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — string. Идентификатор отправления.

## Ответы

**200** — Статус отмены отправления

- `order_number` — string. Номер заказа.
- `posting_number` — array[string]. Идентификатор отправления.
- `state` — string. Статус отмены отправления: - `Подтверждена`, - `На подтверждении`, - `Отклонена`, - `Ожидает обработки`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
