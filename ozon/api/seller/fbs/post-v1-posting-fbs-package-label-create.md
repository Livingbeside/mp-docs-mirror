---
title: Создать задание на выгрузку этикеток
api: ozon-seller
method: POST
path: /v1/posting/fbs/package-label/create
operation_id: PostingAPI_CreateLabelBatch
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: b57da5712b241316
---

# Создать задание на выгрузку этикеток

`POST /v1/posting/fbs/package-label/create`

В будущем метод будет отключён. Мы предупредим вас об этом за месяц. Переключитесь на /v2/posting/fbs/package-label/create . Метод для создания задания на асинхронное формирование этикеток. Для получения этикеток, созданных в результате вызова метода, используйте [/v1/posting/fbs/package-label/get](#operation/PostingAPI_GetLabelBatch).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — ? **обязательный**. Номера отправлений, для которых нужны этикетки.

## Ответы

**200** — Идентификатор задания на формирование этикеток

- `result` — object. Результат работы метода.
  - `task_id` — integer<int64>. Идентификатор задания на формирование этикеток.

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
