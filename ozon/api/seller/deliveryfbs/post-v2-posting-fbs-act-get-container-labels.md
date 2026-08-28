---
title: Этикетки для грузового места
api: ozon-seller
method: POST
path: /v2/posting/fbs/act/get-container-labels
operation_id: PostingAPI_PostingFBSActGetContainerLabels
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: accf0c317b2abdf0
---

# Этикетки для грузового места

`POST /v2/posting/fbs/act/get-container-labels`

Метод создает этикетки для грузового места.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `id` — integer<int64> **обязательный**. Идентификатор перевозки из метода [/v1/carriage/create](#operation/CarriageAPI_CarriageCreate).

## Ответы

**200** — Этикетки для грузового места

- `content_type` — string. Тип файла.
- `file_content` — string<byte>. Содержание файла в бинарном виде.
- `file_name` — string. Название файла.

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
