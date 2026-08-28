---
title: Изменить статус на «Доставлено»
api: ozon-seller
method: POST
path: /v2/fbs/posting/delivered
operation_id: PostingAPI_FbsPostingDelivered
tags:
  - DeliveryrFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ab227fa66b99ca7a
---

# Изменить статус на «Доставлено»

`POST /v2/fbs/posting/delivered`

Перед изменением статуса проверьте текущий статус отправления методом /v3/posting/fbs/get . Изменение статуса происходит асинхронно. Перевести отправление в статус «Доставлено», если используется сторонняя служба доставки.

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
