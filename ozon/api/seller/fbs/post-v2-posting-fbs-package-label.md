---
title: Напечатать этикетку
api: ozon-seller
method: POST
path: /v2/posting/fbs/package-label
operation_id: PostingAPI_PostingFBSPackageLabel
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 084b7aecf76553f3
---

# Напечатать этикетку

`POST /v2/posting/fbs/package-label`

Если вы работаете по схеме rFBS или rFBS Express, изучите процесс печати этикетки в [Базе знаний продавца](https://seller-edu.ozon.ru/rfbs/scheme-of-work).

Генерирует PDF-файл с этикетками для указанных отправлений в статусе «Ожидает отгрузки» — `awaiting_deliver`. В одном запросе можно передать не больше 20 идентификаторов. Если хотя бы для одного отправления возникнет ошибка, этикетки не будут подготовлены для всех отправлений в запросе.

Рекомендуем запрашивать этикетки через 45–60 секунд после сборки заказа.

Ошибка `The next postings aren't ready` означает, что этикетки ещё не готовы, повторите запрос позднее.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — array[string] **обязательный**. Идентификатор отправления.

## Ответы

**200** — Маркировка напечатана

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
