---
title: Доступные даты для переноса доставки
api: ozon-seller
method: POST
path: /v1/posting/fbs/timeslot/change-restrictions
operation_id: PostingAPI_PostingTimeslotChangeRestrictions
tags:
  - DeliveryrFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: a90a126a4ea557e0
---

# Доступные даты для переноса доставки

`POST /v1/posting/fbs/timeslot/change-restrictions`

Метод для получения доступных дат для переноса доставки и количества доступных переносов.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — string **обязательный**. Номер отправления.

## Ответы

**200** — Доступные даты и количество

- `delivery_interval` — object. Период дат, доступных для переноса.
  - `begin` — string<date-time>. Дата начала периода. Формат: `YYYY-MM-DDTHH:mm:ss.sssZ`.
  - `end` — string<date-time>. Дата конца периода. Формат: `YYYY-MM-DDTHH:mm:ss.sssZ`.
- `remaining_changes_count` — integer<int64>. Количество оставшихся переносов.

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
