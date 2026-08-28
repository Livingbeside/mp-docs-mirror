---
title: Получить ограничения пункта приёма
api: ozon-seller
method: POST
path: /v1/posting/fbs/restrictions
operation_id: PostingAPI_GetRestrictions
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: f3483a1c37f98acf
---

# Получить ограничения пункта приёма

`POST /v1/posting/fbs/restrictions`

Метод для получения габаритных, весовых и прочих ограничений пункта приёма по номеру отправления. Метод применим только для работы по схеме FBS.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — string **обязательный**. Номер отправления, для которого нужно определить ограничения.

## Ответы

**200** — Ограничения пункта приёма

- `result` — object
  - `height` — number<double>. Ограничение по высоте в сантиметрах.
  - `length` — number<double>. Ограничение по длине в сантиметрах.
  - `max_posting_price` — number<double>. Ограничение по максимальной стоимости отправления в рублях.
  - `max_posting_weight` — number<double>. Ограничение по максимальному весу в граммах.
  - `min_posting_price` — number<double>. Ограничение по минимальной стоимости отправления в рублях.
  - `min_posting_weight` — number<double>. Ограничение по минимальному весу в граммах.
  - `posting_number` — string. Номер отправления.
  - `width` — number<double>. Ограничение по ширине в сантиметрах.

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
