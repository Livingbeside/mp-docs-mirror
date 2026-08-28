---
title: Таможенные декларации ETGB
api: ozon-seller
method: POST
path: /v1/posting/global/etgb
operation_id: PostingAPI_GetEtgb
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: b1cbc373bdb6a138
---

# Таможенные декларации ETGB

`POST /v1/posting/global/etgb`

Метод для получения таможенных деклараций Elektronik Ticaret Gümrük Beyannamesi (ETGB) для продавцов из Турции.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `date` — object **обязательный**. Фильтр по периоду создания деклараций.
  - `from` — string<date-time> **обязательный**. Дата начала.
  - `to` — string<date-time> **обязательный**. Дата окончания.

## Ответы

**200** — Информация о декларациях

- `result` — array[object]. Результат запроса.
  - `etgb` — object. Информация о декларации.
    - `date` — string. Дата создания.
    - `number` — string. Номер.
    - `url` — string. Ссылка на файл. Если поле пустое и вам нужен файл, обратитесь в поддержку Ozon.
  - `posting_number` — string. Номер отправления.

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
