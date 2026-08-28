---
title: Добавить трек-номера
api: ozon-seller
method: POST
path: /v2/fbs/posting/tracking-number/set
operation_id: PostingAPI_FbsPostingTrackingNumberSet
tags:
  - DeliveryrFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 2d958273c4b24197
---

# Добавить трек-номера

`POST /v2/fbs/posting/tracking-number/set`

Добавить трек-номера к отправлениям. Вы можете передать до 20 трек-номеров за раз.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `tracking_numbers` — array[object] **обязательный**. Массив с парами идентификатор отправления — трек-номер.
  - `posting_number` — string **обязательный**. Идентификатор отправления.
  - `tracking_number` — string **обязательный**. Трек-номер отправления.

## Ответы

**200** — Трек-номер добавлен

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
