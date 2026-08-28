---
title: Получить лист отгрузки по перевозке
api: ozon-seller
method: POST
path: /v2/posting/fbs/digital/act/get-pdf
operation_id: PostingAPI_PostingFBSGetDigitalAct
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: 415b1058c5488654
---

# Получить лист отгрузки по перевозке

`POST /v2/posting/fbs/digital/act/get-pdf`

> ⚠️ Метод помечен как **deprecated**.

Метод устаревает и будет отключён 22 марта 2026 года. Переключитесь на /v2/posting/fbs/act/get-pdf.

Вы можете получить документы, если в ответе метода [/v2/posting/fbs/digital/act/check-status](#operation/PostingAPI_PostingFBSDigitalActCheckStatus) был один из статусов:
- `FORMED` — перевозка сформирована успешно,
- `CONFIRMED` — перевозка подтверждена Ozon,
- `CONFIRMED_WITH_MISMATCH` — перевозка принята Ozon с расхождениями.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `doc_type` — None<string>. Тип электронного документа: - `act_of_acceptance` — лист отгрузки, - `act_of_mismatch` — акт о расхождениях, - `act_of_excess` — акт об излишках, - `waybill` — транспортная накладная.
- `id` — integer<int64> **обязательный**. Номер задания на формирование документов (также идентификатор перевозки) из метода [POST /v2/posting/fbs/act/create](#operation/PostingAPI_PostingFBSActCreate).

## Ответы

**200** — Файл с документом

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
