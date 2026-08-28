---
title: Перенести дату доставки
api: ozon-seller
method: POST
path: /v1/posting/fbs/timeslot/set
operation_id: PostingAPI_SetPostingTimeslot
tags:
  - DeliveryrFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ad69bd6013e8ef01
---

# Перенести дату доставки

`POST /v1/posting/fbs/timeslot/set`

Вы можете изменить дату доставки отправления не больше двух раз.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `new_timeslot` — object **обязательный**. Новый период для даты доставки.
  - `from` — string<date-time> **обязательный**. Дата начала периода. Формат: `YYYY-MM-DDTHH:mm:ss.sssZ`.
  - `to` — string<date-time> **обязательный**. Дата конца периода. Формат: `YYYY-MM-DDTHH:mm:ss.sssZ`.
- `posting_number` — string **обязательный**. Номер отправления.

## Ответы

**200** — Результат запроса

- `result` — boolean. `true`, если дата изменена.

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
