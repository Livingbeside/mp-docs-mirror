---
title: Значение штрихкода для отгрузки отправления
api: ozon-seller
method: POST
path: /v2/posting/fbs/act/get-barcode/text
operation_id: PostingAPI_PostingFBSGetBarcodeText
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 65550faa17786956
---

# Значение штрихкода для отгрузки отправления

`POST /v2/posting/fbs/act/get-barcode/text`

Используйте этот метод, чтобы получить штрихкод из ответа
[/v2/posting/fbs/act/get-barcode](#operation/PostingAPI_PostingFBSGetBarcode) в текстовом виде.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `id` — integer<int64> **обязательный**. Идентификатор перевозки.

## Ответы

**200** — Значение штрихкода

- `result` — string. Штрихкод в текстовом виде.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
