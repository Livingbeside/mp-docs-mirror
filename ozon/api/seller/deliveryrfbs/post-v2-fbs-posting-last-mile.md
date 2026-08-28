---
title: Изменить статус на «Последняя миля»
api: ozon-seller
method: POST
path: /v2/fbs/posting/last-mile
operation_id: PostingAPI_FbsPostingLastMile
tags:
  - DeliveryrFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e74a7fdd31d2180c
---

# Изменить статус на «Последняя миля»

`POST /v2/fbs/posting/last-mile`

Перед изменением статуса проверьте текущий статус отправления методом /v3/posting/fbs/get . Изменение статуса происходит асинхронно. Перевести отправление в статус «Последняя миля», если используется сторонняя служба доставки.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — array[string] **обязательный**. Идентификатор отправления.

## Ответы

**200** — Статус изменён

- `result` — array[object]. Результат работы метода.
  - `error` — string. Ошибка при обработке запроса.
  - `posting_number` — string. Номер отправления.
  - `result` — boolean. Если запрос выполнен без ошибок — `true`.

**400** — Invalid parameter

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Access denied

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Response not found

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Request conflict

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Internal server error

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
