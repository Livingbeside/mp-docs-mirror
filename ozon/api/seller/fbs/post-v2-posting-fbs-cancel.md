---
title: Отменить отправление
api: ozon-seller
method: POST
path: /v2/posting/fbs/cancel
operation_id: PostingAPI_CancelFbsPosting
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 7d37ae8ea34d9c27
---

# Отменить отправление

`POST /v2/posting/fbs/cancel`

Меняет статус отправления на `cancelled`.

Перед началом работы проверьте причины отмены для конкретного отправления методом [/v1/posting/fbs/cancel-reason](#operation/PostingAPI_GetPostingFbsCancelReasonV1).

Условно-доставленные отправления отменить нельзя.

Если значение параметра `cancel_reason_id` — 402, заполните поле `cancel_reason_message`.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cancel_reason_id` — integer<int64> **обязательный**. Идентификатор причины отмены отправления.
- `cancel_reason_message` — string. Дополнительная информация по отмене. Если `cancel_reason_id = 402`, параметр обязательный.
- `posting_number` — string **обязательный**. Идентификатор отправления.

## Ответы

**200** — Отправление отменено

- `result` — boolean. Результат обработки запроса. `true`, если запрос выполнился без ошибок.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
