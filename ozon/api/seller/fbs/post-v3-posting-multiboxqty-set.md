---
title: Указать количество коробок для многокоробочных отправлений
api: ozon-seller
method: POST
path: /v3/posting/multiboxqty/set
operation_id: PostingAPI_PostingMultiBoxQtySetV3
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: bb098ed075257cf9
---

# Указать количество коробок для многокоробочных отправлений

`POST /v3/posting/multiboxqty/set`

Метод для передачи количества коробок для отправлений, в которых есть многокоробочные товары.

Используйте метод при работе по схеме rFBS Агрегатор — c доставкой партнёрами Ozon.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `multi_box_qty` — integer<int64> **обязательный**. Количество коробок, в которые упакован товар.
- `posting_number` — string **обязательный**. Идентификатор многокоробочного отправления.

## Ответы

**200** — Количество коробок указано

- `result` — object. Результат передачи количества коробок.
  - `result` — boolean. Возможные значения: - `true` — значение передано успешно. - `false` — при передаче произошла ошибка. Попробуйте снова.

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
