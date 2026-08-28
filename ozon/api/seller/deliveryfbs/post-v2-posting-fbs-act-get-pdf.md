---
title: Получить PDF c документами
api: ozon-seller
method: POST
path: /v2/posting/fbs/act/get-pdf
operation_id: PostingAPI_PostingFBSGetAct
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 5ca4ee275b6ea73e
---

# Получить PDF c документами

`POST /v2/posting/fbs/act/get-pdf`

С помощью метода можно получить: - продацам из России — лист отгрузки и транспортную накладную; - продавцам из СНГ — акт и транспортную накладную. Получите список доступных документов для отгрузки в параметре `available_actions` метода [/v1/carriage/get](#operation/CarriageGet).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `id` — integer<int64> **обязательный**. Номер задания на формирование документов (также идентификатор перевозки) из методов [/v2/posting/fbs/act/create](#operation/PostingAPI_PostingFBSActCreate) или [/v1/carriage/create](#operation/CarriageAPI_CarriageCreate).

## Ответы

**200** — Документы

- `file_content` — string<byte>. Содержание файла в бинарном виде.
- `file_name` — string. Название файла.
- `content_type` — string. Тип файла.

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
